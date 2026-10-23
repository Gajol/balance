---
layout: single
title: "Who Runs the Website? A Simple Operating Model for a Web Platform"
date: 2026-10-23 09:20:00 -0400
description: "A platform that launches without a plan for who runs it will drift. A short RACI and five roles keep it healthy."
excerpt: "A platform that launches without a plan for who runs it will drift. A short RACI and five roles keep it healthy."
theme: digital
tags: [operating model, raci, governance, roles]
---

Projects end on a date. Websites do not. The day after launch, someone has to patch the server, fix a broken page, answer a question and decide what to improve next.

An **operating model** answers a plain question: *who does what, every day?*

## Five generic roles

- **Content owner.** Responsible for the accuracy of their pages.
- **Editor / publisher.** Prepares and publishes content.
- **Platform administrator.** Keeps the system running, secure and patched.
- **Product owner.** Decides what to improve and reports on health.
- **Service desk.** First point of contact for questions and problems.

In a small team, one person may wear several hats. The roles still need to be clear.

## A RACI you can explore

RACI stands for **R**esponsible (does the work), **A**ccountable (owns the result, only one per task), **C**onsulted and **I**nformed. Click a role to highlight its column. Hover a cell for its meaning.

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
<div class="wx" markdown="0" id="w5">
<div style="overflow-x:auto"><table id="w5t"></table></div>
<div class="card" id="w5s" aria-live="polite"><span class="note">Click a role heading.</span></div>
</div>
<script>
(function(){
var R=["Content owner","Editor","Platform admin","Product owner","Service desk"];
var A=[["Write and update a page","AR","C","-","I","-"],["Publish content","A","R","I","I","-"],["Send yearly review reminders","AR","I","R","I","-"],["Archive retired content","C","R","I","A","-"],["Manage access and roles","I","I","R","A","C"],["Patch and back up the platform","-","-","AR","I","I"],["Handle user problems","I","-","A","I","R"],["Report on content health","C","I","R","A","-"],["Decide what to improve next","C","C","C","AR","C"]];
var X={A:"Accountable: owns the result. Only one per task.",R:"Responsible: does the work.",AR:"Accountable and responsible: owns it and does it.",C:"Consulted: asked for input before a decision.",I:"Informed: told after it is done.","-":"Not involved."};
var sel=-1;
function draw(){
var h='<tr><th>Activity</th>';R.forEach(function(r,i){h+='<th><button class="'+(sel==i?'on':'')+'" data-i="'+i+'">'+r+'</button></th>';});h+='</tr>';
A.forEach(function(a){h+='<tr><td>'+a[0]+'</td>';for(var i=1;i<=5;i++){var v=a[i],hi=sel==i-1&&v!='-';h+='<td title="'+X[v]+'" class="'+(hi?'hl':'')+'">'+v+'</td>';}h+='</tr>';});
document.getElementById('w5t').innerHTML=h;
document.querySelectorAll('#w5t button').forEach(function(b){b.onclick=function(){sel=+b.dataset.i;draw();var doR=A.filter(function(a){return a[sel+1].indexOf('R')>-1}).length,doA=A.filter(function(a){return a[sel+1].indexOf('A')>-1}).length;document.getElementById('w5s').innerHTML='<strong>'+R[sel]+'</strong>: responsible for '+doR+' of '+A.length+' activities, accountable for '+doA+'.';};});
}
draw();
})();
</script>

## Checks that matter

- **One A per row.** If two roles are accountable, nobody is.
- **No empty R.** Every task needs someone who does it.
- **Watch the heavy column.** One role carrying most of the Rs is a risk to plan for.

## What each role should see

Give each role a view built for them: owners see their pages and reminders, editors see a work queue, administrators see platform health, and the product owner sees the content health report. When the system shows people what they need, fewer problems reach the service desk.
