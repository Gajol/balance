---
layout: single
title: "Content Health: Measuring Whether Your Website Is Current and Owned"
date: 2026-10-23 09:05:00 -0400
description: "Four simple measures show which parts of a site are healthy and which need attention, with no extra work for readers."
excerpt: "Four simple measures show which parts of a site are healthy and which need attention, with no extra work for readers."
theme: digital
author_profile: false
classes: full-width
tags: [analytics, content, governance, matomo]
---

"How good is our content?" is hard to answer. "How many pages have no owner?" is easy. Good reporting turns the first question into several of the second kind.

Analytics tools already collect most of what you need. Combine them with a little page information (owner, review date) and you get a content health report.

## Four measures that work

- **Stale.** Not reviewed within the review cycle (for example 12 months).
- **No owner.** Nobody is named as responsible.
- **Orphan.** No other page links to it, so people only find it by search or bookmark.
- **Failed searches.** Searches in that area that returned nothing, or that people abandoned.

Fictional data below. Pick a measure, sort, and click a row for the suggested next step.

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
<div class="wx" markdown="0" id="w2">
<div class="row" role="group" aria-label="Measure">
<button data-m="stale" aria-pressed="true">Stale</button>
<button data-m="noOwner" aria-pressed="false">No owner</button>
<button data-m="orphan" aria-pressed="false">Orphan</button>
<button data-m="failed" aria-pressed="false">Failed searches</button>
<button id="w2s" aria-pressed="true">Worst first</button>
</div>
<div id="w2l"></div>
<div class="card" id="w2d"><span class="note">Click a branch to see a suggested action.</span></div>
</div>
<script>
(function(){
var D=[["Finance",120,18,4,6,14],["Human Resources",210,60,22,15,40],["IT Services",340,150,60,48,25],["Communications",95,8,2,3,5],["Operations",180,70,35,20,30],["Policy",150,30,50,12,9]];
var idx={stale:2,noOwner:3,orphan:4,failed:5},tip={stale:"Send review reminders to the owners. Archive pages nobody claims.",noOwner:"Assign an owner for each page, or archive it. Start with the most visited.",orphan:"Link the page from its topic hub, or retire it if it is no longer needed.",failed:"Read the search terms. Add the missing content, a synonym, or a better title."};
var m="stale",sort=true,sel=null;
function draw(){
var k=idx[m],rows=D.slice();
if(sort)rows.sort(function(a,b){return b[k]/b[1]-a[k]/a[1];});
var h='';
rows.forEach(function(r){var p=Math.round(r[k]/r[1]*100);
h+='<div class="'+(sel==r[0]?'card hl':'card')+'" style="cursor:pointer" data-n="'+r[0]+'" tabindex="0" role="button" title="'+r[k]+' of '+r[1]+' pages"><div class="row" style="justify-content:space-between;margin:0"><span>'+r[0]+'</span><strong>'+p+'%</strong></div><div class="track"><div class="fill" style="width:'+Math.min(p,100)+'%"></div></div></div>';});
document.getElementById('w2l').innerHTML=h;
document.querySelectorAll('#w2l .card').forEach(function(c){function go(){sel=c.dataset.n;draw();var r=D.filter(function(x){return x[0]==sel})[0];document.getElementById('w2d').innerHTML='<strong>'+sel+'</strong>: '+r[idx[m]]+' of '+r[1]+' pages. <br>'+tip[m];}c.onclick=go;c.onkeydown=function(e){if(e.key=='Enter'||e.key==' '){e.preventDefault();go();}};});
}
document.querySelectorAll('#w2 button[data-m]').forEach(function(b){b.onclick=function(){m=b.dataset.m;document.querySelectorAll('#w2 button[data-m]').forEach(function(x){x.setAttribute('aria-pressed',x==b)});draw();if(sel){document.querySelector('#w2l .card.hl')&&document.querySelector('#w2l .card.hl').click();}};});
document.getElementById('w2s').onclick=function(){sort=!sort;this.setAttribute('aria-pressed',sort);draw();};
draw();
})();
</script>

## From report to action

A report only helps if someone acts on it. The goal is to send each flag to the person who owns that page, not to IT. For example, a stale page goes to the owner's review list, and a failed search goes to the product owner. Reminders, escalation and archiving can then be automated, with people making every decision. See [Automation Flags, People Decide]({{ '/automation-flags-people-decide/' | relative_url }}) for how that loop works.

## How to use the report

- **Report by branch or team, not by page.** Managers can act on a branch. Nobody can act on 3,000 rows.
- **Show owners their own numbers.** If owners can see their own health without asking IT, many will fix things on their own.
- **Track the trend.** A percentage that falls month over month is the goal.
- **Do not use it to shame.** The aim is to find work worth doing.

Keep the number of measures small. Four is enough to start.
