---
layout: single
title: "Your Search Box Is Only as Good as Your Content Owners"
date: 2026-10-23 09:10:00 -0400
description: "Better search is mostly a people problem. Owners and review dates help the engine rank the right page first."
excerpt: "Better search is mostly a people problem. Owners and review dates help the engine rank the right page first."
theme: digital
author_profile: false
classes: full-width
tags: [search, intranet, content, solr]
---

When search disappoints, we blame the engine. Usually the real cause is the content: three versions of the same page, nobody who owns any of them, and the oldest ranking highest.

A search engine can only rank what it is given. It does not know which page is right. People do.

## Three things owners give the engine

1. **A signal of trust.** Pages with an owner can be ranked higher.
2. **A signal of age.** Pages past their review date can be ranked lower, or hidden.
3. **A clean-up route.** Retired pages move out of the index, so they stop competing.

Search for "travel claim" below. Switch the settings on and watch the order change.

<style>
.wx{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:14px;margin:1.2em 0;font-size:.95em}
.wx button,.wx select{font:inherit;padding:4px 10px;border:1px solid rgba(128,128,128,.55);border-radius:6px;background:transparent;color:inherit;cursor:pointer}
.wx button[aria-pressed=true],.wx button.on{background:#1f6feb;color:#fff;border-color:#1f6feb}
.wx .row{display:flex;flex-wrap:wrap;gap:8px;margin:8px 0;align-items:center}
.wx .card{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:10px;margin:6px 0}
.wx .note{opacity:.85;font-size:.9em}
.wx .good{color:#2da44e;font-weight:600}.wx .bad{color:#e5534b;font-weight:600}
.wx .track{background:rgba(128,128,128,.25);border-radius:6px;height:14px;overflow:hidden}
.wx .fill{height:14px;background:#1f6feb;border-radius:6px;transition:width .3s}
.wx table{border-collapse:collapse;width:100%}
.wx td,.wx th{border:1px solid rgba(128,128,128,.35);padding:5px 8px;text-align:center}
.wx td:first-child,.wx th:first-child{text-align:left}
.wx tr.pick{background:rgba(31,111,235,.15)}
.wx .hl{background:rgba(31,111,235,.25);outline:2px solid #1f6feb}
.wx .cols{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:8px}
</style>
<div class="wx" markdown="0" id="w3">
<div class="row">
<button data-k="own" aria-pressed="false" title="Pages with a named owner rank higher">Boost pages with an owner</button>
<button data-k="stale" aria-pressed="false" title="Pages not reviewed in over 12 months rank lower">Demote old pages</button>
<button data-k="arch" aria-pressed="false" title="Retired pages leave the search index">Archive retired pages</button>
</div>
<div class="note">Search: <strong>travel claim</strong></div>
<div id="w3r"></div>
</div>
<script>
(function(){
var P=[{t:"Travel claim form (2019 version)",rel:9,own:false,age:50,ret:true},{t:"Travel claims: how to submit",rel:8,own:true,age:4,ret:false},{t:"Travel policy summary",rel:6,own:true,age:30,ret:false},{t:"Old travel claim FAQ",rel:7,own:false,age:40,ret:false}];
var s={own:false,stale:false,arch:false};
function draw(){
var L=P.filter(function(p){return !(s.arch&&p.ret)}).map(function(p){var sc=p.rel;if(s.own&&p.own)sc+=3;if(s.stale&&p.age>12)sc-=5;return {p:p,sc:sc};}).sort(function(a,b){return b.sc-a.sc});
var h='';L.forEach(function(x,i){var p=x.p;h+='<div class="card"><strong>'+(i+1)+'. '+p.t+'</strong><br><span class="note">Owner: '+(p.own?'Finance Services':'<span class="bad">none</span>')+' · Reviewed '+p.age+' months ago'+(p.ret?' · <span class="bad">retired</span>':'')+'</span></div>';});
document.getElementById('w3r').innerHTML=h;
var top=L[0].p;
h='<p>'+(top.own&&top.age<=12?'<span class="good">The right page is first.</span>':'<span class="bad">The top result is out of date and has no owner.</span>')+'</p>';
document.getElementById('w3r').insertAdjacentHTML('beforeend',h);
}
document.querySelectorAll('#w3 button').forEach(function(b){b.onclick=function(){s[b.dataset.k]=!s[b.dataset.k];b.setAttribute('aria-pressed',s[b.dataset.k]);draw();};});
draw();
})();
</script>

## What this means in practice

- **The engine matters less than you think.** Whether you choose Solr, OpenSearch or something else, it will struggle with unowned, outdated content. Choose on your team's skills and how easily you can run it. Then spend the saved effort on content.
- **Fix the top 20 searches first.** Read your search logs. A small list of terms usually accounts for a large share of searches.
- **Treat "no results" as a to-do list.** Each one is a reader telling you what is missing.

Search is a service you run, not a feature you buy.
