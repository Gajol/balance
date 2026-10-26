---
layout: single
title: "Who Runs the Website? A Simple Operating Model for a Web Platform"
date: 2026-10-23 09:20:00 -0400
description: "A platform that launches without a plan for who runs it will drift. A short RACI and five roles keep it healthy."
excerpt: "A platform that launches without a plan for who runs it will drift. A short RACI and five roles keep it healthy."
theme: digital
author_profile: false
classes: full-width
tags: ["operating model", governance]
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

RACI stands for **R**esponsible (does the work), **A**ccountable (owns the result, only one per task), **C**onsulted and **I**nformed. Hover a letter to see what it means for that role in that activity. Hover or focus a role name to see what it does, the skills and tools it needs, and what the system shows it. Click a role to pin it and highlight its column.

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
<style>
#w5 .bd{display:inline-block;min-width:1.7em;padding:1px 6px;border-radius:5px;font-weight:700;font-size:.9em;color:#fff;text-align:center}
#w5 .bA{background:#1f6feb}#w5 .bR{background:#2da44e}#w5 .bC{background:#d98e04}#w5 .bI{background:#7a7f87}
#w5 td.cell{cursor:default}
#w5 td.cell:hover,#w5 td.cell:focus{outline:2px solid #1f6feb;background:rgba(31,111,235,.12)}
#w5 .leg{display:flex;flex-wrap:wrap;gap:6px 16px;font-size:.88em;margin-bottom:8px}
#w5 .pn{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:12px;margin-top:10px}
#w5 .pn h4{margin:0 0 6px;font-size:1.05em;display:flex;align-items:center;gap:8px;flex-wrap:wrap}
#w5 .g4{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:8px;margin-top:8px}
#w5 .g4>div{border:1px solid rgba(128,128,128,.3);border-radius:8px;padding:8px;font-size:.9em}
#w5 .g4 .lb{display:block;font-size:.76em;text-transform:uppercase;letter-spacing:.06em;opacity:.7;margin-bottom:3px}
#w5 .chip2{display:inline-block;margin:2px 3px 2px 0;padding:1px 8px;border-radius:10px;border:1px solid rgba(128,128,128,.5);font-size:.82em}
</style>
<div class="leg"><span><span class="bd bA">A</span> Accountable: owns the result</span><span><span class="bd bR">R</span> Responsible: does the work</span><span><span class="bd bC">C</span> Consulted: asked first</span><span><span class="bd bI">I</span> Informed: told after</span></div>
<div style="overflow-x:auto"><table id="w5t"></table></div>
<div class="pn" id="w5s" aria-live="polite"></div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var R=["Content owner","Editor","Platform admin","Product owner","Service desk"];
var A=[["Write and update a page","AR","C","-","I","-"],["Publish content","A","R","I","I","-"],["Send yearly review reminders","AR","I","R","I","-"],["Archive retired content","C","R","I","A","-"],["Manage access and roles","I","I","R","A","C"],["Patch and back up the platform","-","-","AR","I","I"],["Handle user problems","I","-","A","I","R"],["Report on content health","C","I","R","A","-"],["Decide what to improve next","C","C","C","AR","C"]];
var T=[["Writes or updates their own pages and answers for their accuracy. Nobody else can say the content is right.","Asked for plain-language, bilingual and accessibility help before the page goes live.","","Told about big changes so they appear in the health report and the roadmap.",""],
["Approves that the page is ready to go live. Their name stays on it.","Checks, formats, translates and publishes the page. Accessibility checks run as they publish.","Told only if publishing breaks something, such as a failed deployment.","Sees publishing volume and delays in the reports.",""],
["Must answer each reminder: still correct, update it, or retire it. Silence has visible consequences.","Sees which pages are due, so they can help busy owners.","Keeps the reminder and escalation rules running, and fixes it if the mail bounces.","Watches how many reminders get answered.",""],
["Asked before their page is archived, and can say it is still needed.","Carries out the archive: moves the page, adds a notice and a restore link.","Told when a large archive changes search or storage.","Owns the decision to retire content nobody claims, and the archive rules.",""],
["Told who can edit their pages.","Told when their own permissions change.","Sets up accounts and roles, and removes access when people leave.","Answers that access matches roles, and that nobody has more than they need.","Takes the access requests, and is asked who should have what."],
["","","Owns and does patching, backups and restore drills. A backup never restored is only an assumption.","Told about planned downtime.","Told in advance, so they can answer \"is the site down?\" calls."],
["Told when a problem affects one of their pages.","","Answers that platform problems are fixed and service is restored.","Sees repeat problems, which feed the roadmap.","Takes the call, solves what they can, and passes the rest on."],
["Asked to explain unusual numbers on their pages.","Sees review-due lists and accessibility results.","Keeps the data feeds (analytics and search logs) accurate and running.","Answers for the health report, and for what is done about it.",""],
["Says what their readers need.","Brings what they see in the content every day.","Says what is technically possible and what it costs to run.","Makes the call and owns the roadmap.","Brings the top questions people ask."]];
var D=[{d:"Accountable for the accuracy of their own pages. Keeps them current, or retires them.",k:"Subject knowledge; plain-language writing in both official languages; accessible content.",t:"Authoring tool; a My content view.",v:"Review-due list, per-page feedback (was this useful?), accessibility check results, page health."},{d:"Prepares, checks and publishes content on behalf of owners.",k:"Writing for the web; bilingual editing; accessible content; captioning video.",t:"Authoring and workflow in the CMS; caption files; link checker.",v:"Work queue, accessibility checks when publishing, review-due lists, English and French pair status."},{d:"Keeps the platform running, secure and patched.",k:"Linux and containers; CMS, search and cache operations; backup and restore; monitoring; patching through a pipeline.",t:"Container platform; monitoring; backup tools; code repository and pipeline.",v:"Health dashboards, alerts, backup and restore-drill results, patch status."},{d:"Decides what to improve next, using evidence, and reports on content health.",k:"Product management; web analytics; report design for executives and owners; information architecture and taxonomy; usability and accessibility testing.",t:"Analytics dashboards; search logs; reporting tool; usability testing tools.",v:"Content health and parity reports, zero-result searches, unused terms, accessibility results, task-success feedback."},{d:"First point of contact for questions and problems. Fixes what it can, passes the rest on.",k:"Triage; clear communication in both languages; good knowledge of the platform.",t:"Ticketing system; knowledge base.",v:"Open tickets, repeat issues, known-problem list."}];
var LN={A:"Accountable",R:"Responsible",C:"Consulted",I:"Informed"};
var pin=-1,hov=-1;
function bd(v){var o='';v.split('').forEach(function(c){o+='<span class="bd b'+c+'">'+c+'</span> ';});return o;}
var HINT='<span class="note">Hover or focus a role heading for what it does, the skills and tools it needs, and what the system shows it. Hover a letter in the table for what it means for that role in that activity. Click a role to pin it.</span>';
function rolePanel(j){var d=D[j],r=0,a=0,mine='';A.forEach(function(x){var v=x[j+1];if(v.indexOf('R')>-1)r++;if(v.indexOf('A')>-1)a++;if(v.indexOf('R')>-1||v.indexOf('A')>-1)mine+='<span class="chip2">'+x[0]+'</span>';});
return '<h4>'+R[j]+' <span class="bd bR">R &times; '+r+'</span> <span class="bd bA">A &times; '+a+'</span></h4><div>'+d.d+'</div><div class="g4"><div><span class="lb">Skills and experience</span>'+d.k+'</div><div><span class="lb">Tools</span>'+d.t+'</div><div><span class="lb">What the system shows them</span>'+d.v+'</div><div><span class="lb">Does or owns here</span>'+(mine||'Mostly consulted or informed.')+'</div></div>';}
function cellPanel(i,j){var v=A[i][j+1],who={A:[],R:[]};for(var k=0;k<5;k++){var x=A[i][k+1];if(x.indexOf('A')>-1)who.A.push(R[k]);if(x.indexOf('R')>-1)who.R.push(R[k]);}
var lab=v.split('').map(function(c){return LN[c];}).join(' and ');
return '<h4>'+bd(v)+' '+R[j]+' &middot; '+A[i][0]+'</h4><div><strong>'+lab+'.</strong> '+T[i][j]+'</div><div class="g4"><div><span class="lb">Accountable for this activity</span>'+who.A.join(', ')+'</div><div><span class="lb">Does the work</span>'+who.R.join(', ')+'</div></div>';}
function show(html){g('w5s').innerHTML=html;}
function idle(){show(pin>=0?rolePanel(pin):HINT);}
function draw(){
var h='<tr><th>Activity</th>';R.forEach(function(r,j){h+='<th><button class="'+(pin==j?'on':'')+'" data-j="'+j+'">'+r+'</button></th>';});h+='</tr>';
A.forEach(function(a,i){h+='<tr><td>'+a[0]+'</td>';for(var j=0;j<5;j++){var v=a[j+1],hi=pin==j&&v!='-';h+=v=='-'?'<td class="'+(hi?'hl':'')+'" style="opacity:.4">&ndash;</td>':'<td class="cell '+(hi?'hl':'')+'" tabindex="0" data-i="'+i+'" data-j="'+j+'" aria-label="'+R[j]+', '+a[0]+': '+v+'">'+bd(v)+'</td>';}h+='</tr>';});
g('w5t').innerHTML=h;
document.querySelectorAll('#w5t td.cell').forEach(function(c){var i=+c.dataset.i,j=+c.dataset.j;function go(){show(cellPanel(i,j));}c.onmouseenter=go;c.onfocus=go;c.onmouseleave=c.onblur=idle;});
document.querySelectorAll('#w5t button').forEach(function(b){var j=+b.dataset.j;function go(){show(rolePanel(j));}b.onmouseenter=go;b.onfocus=go;b.onmouseleave=b.onblur=idle;b.onclick=function(){pin=(pin==j)?-1:j;draw();idle();};});
}
draw();idle();
})();
</script>

## Checks that matter

- **One A per row.** If two roles are accountable, nobody is.
- **No empty R.** Every task needs someone who does it.
- **Watch the heavy column.** One role carrying most of the Rs is a risk to plan for.

## What each role should see

Give each role a view built for them: owners see their pages and reminders, editors see a work queue, administrators see platform health, and the product owner sees the content health report. When the system shows people what they need, fewer problems reach the service desk.
