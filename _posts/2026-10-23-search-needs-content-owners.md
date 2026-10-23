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

Search for "travel claim" below. Switch the settings on and watch two things change: the order of the results, and how the reader feels about search. Trust is the real product. Once people stop trusting search, they stop using it.

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
<style>
#w3 .wc{display:grid;grid-template-columns:minmax(0,300px) minmax(0,1fr);gap:18px;align-items:start}
@media (max-width:760px){#w3 .wc{grid-template-columns:1fr}}
#w3 .face{font-size:3.4em;line-height:1}
#w3 .side{position:sticky;top:10px}
#w3 .tm{margin-top:8px}
#w3 .tag{display:inline-block;margin-left:6px;padding:0 7px;border-radius:9px;font-size:.78em;border:1px solid #e5534b;color:#e5534b}
#w3 .tag.ok{border-color:#2da44e;color:#2da44e}
</style>
<div class="wc">
<div class="side">
<div><strong>Ranking rules</strong></div>
<div class="row">
<button data-k="own" aria-pressed="false" title="Pages with a named owner rank higher">Boost pages with an owner</button>
<button data-k="stale" aria-pressed="false" title="Pages not reviewed in over 12 months rank lower and carry a warning">Demote old pages</button>
<button data-k="arch" aria-pressed="false" title="Retired pages leave the search index">Archive retired pages</button>
</div>
<div class="card" id="w3m" aria-live="polite"></div>
</div>
<div>
<div class="note" style="margin-bottom:6px">Staff search for: <strong>travel claim</strong></div>
<div id="w3r"></div>
</div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var P=[{t:"Travel claim form (2019 version)",rel:9,own:false,age:50,ret:true},{t:"Travel claims: how to submit",rel:8,own:true,age:4,ret:false},{t:"Travel policy summary",rel:6,own:true,age:30,ret:false},{t:"Old travel claim FAQ",rel:7,own:false,age:40,ret:false}];
var s={own:false,stale:false,arch:false};
function trusted(p){return p.own&&p.age<=12&&!p.ret;}
function draw(){
var L=P.filter(function(p){return !(s.arch&&p.ret)}).map(function(p){var sc=p.rel;if(s.own&&p.own)sc+=3;if(s.stale&&p.age>12)sc-=5;return {p:p,sc:sc};}).sort(function(a,b){return b.sc-a.sc});
var h='',mis=0;
L.forEach(function(x,i){var p=x.p,flag=s.stale&&p.age>12&&!p.ret,bad=!trusted(p);if(bad&&!flag)mis++;
h+='<div class="card"><strong>'+(i+1)+'. '+p.t+'</strong>'+(flag?'<span class="tag">May be out of date</span>':'')+(trusted(p)?'<span class="tag ok">Owned and current</span>':'')+'<br><span class="note">Owner: '+(p.own?'Finance Services':'<span class="bad">none</span>')+' &middot; Reviewed '+p.age+' months ago'+(p.ret?' &middot; <span class="bad">retired</span>':'')+'</span></div>';});
g('w3r').innerHTML=h;
var top=trusted(L[0].p),m;
if(!top)m={f:"&#128544;",l:"Frustrated",q:"The first result is the old form. Again. Why do I even use search?",b:"Phones a colleague",t:15,c:"#e5534b"};
else if(mis>0)m={f:"&#128528;",l:"Wary",q:"The first one looks right, but I will scroll and double-check.",b:"Scrolls and double-checks",t:50,c:"#d98e04"};
else m={f:"&#128524;",l:"Trusting",q:"First result, right page. I did not even think about it.",b:"Just searches",t:90,c:"#2da44e"};
g('w3m').innerHTML='<div class="row" style="margin:0"><span class="face" aria-hidden="true">'+m.f+'</span><span><span class="note">How the reader feels about search</span><br><strong style="font-size:1.1em">'+m.l+'</strong></span></div><div style="font-style:italic;margin-top:6px">“'+m.q+'”</div><div class="tm"><div class="row" style="justify-content:space-between;margin:0"><span class="note">Trust in search</span><strong style="color:'+m.c+'">'+m.t+'%</strong></div><div class="track"><div class="fill" style="width:'+m.t+'%;background:'+m.c+'"></div></div></div><div class="note" style="margin-top:6px">Habit it creates: <strong>'+m.b+'</strong></div>';
}
document.querySelectorAll('#w3 button[data-k]').forEach(function(b){b.onclick=function(){s[b.dataset.k]=!s[b.dataset.k];b.setAttribute('aria-pressed',s[b.dataset.k]);draw();};});
draw();
})();
</script>

## What this means in practice

- **The engine matters less than you think.** Whether you choose Solr, OpenSearch or something else, it will struggle with unowned, outdated content. Choose on your team's skills and how easily you can run it. Then spend the saved effort on content.
- **Fix the top 20 searches first.** Read your search logs. A small list of terms usually accounts for a large share of searches.
- **Treat "no results" as a to-do list.** Each one is a reader telling you what is missing.

Search is a service you run, not a feature you buy.
