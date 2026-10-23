---
layout: single
title: "One Vocabulary: Sharing a Taxonomy Across Search, Analytics and Navigation"
date: 2026-10-23 09:15:00 -0400
description: "If search, reports and menus all use the same list of terms, you can finally compare them."
excerpt: "If search, reports and menus all use the same list of terms, you can finally compare them."
theme: digital
author_profile: false
classes: full-width
tags: [taxonomy, search, analytics, navigation]
---

A taxonomy is a controlled list of topic terms. It sounds dull, and it is the quiet foundation of a good website.

Most sites let each tool keep its own labels. Search says "Business travel", the menu says "Trips" and the report says "Voyages". Nothing lines up, so nobody can ask a simple question like: "People search for travel a lot but rarely click the menu. Why?"

Share one list, and every tool speaks the same language.

Click a term, then flip between shared and separate vocabularies.

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
<div class="wx" markdown="0" id="w4">
<div class="row"><strong>Vocabulary:</strong>
<button data-v="1" aria-pressed="true">One shared list</button>
<button data-v="0" aria-pressed="false">Each tool has its own</button></div>
<div class="row" id="w4t" role="group" aria-label="Terms"></div>
<div class="cols">
<div class="card"><strong>Search filter</strong><div id="w4a"></div></div>
<div class="card"><strong>Analytics report</strong><div id="w4b"></div></div>
<div class="card"><strong>Navigation menu</strong><div id="w4c"></div></div>
</div>
<div id="w4n" aria-live="polite" class="note"></div>
</div>
<script>
(function(){
var T=["Travel","Benefits","IT support","Learning"];
var alt={Travel:["Business travel","Trips","Voyages"],Benefits:["Perks","Compensation","Pay and extras"],"IT support":["Tech help","Service desk","Computers"],Learning:["Training","Courses","Development"]};
var n={Travel:[420,90],Benefits:[310,120],"IT support":[880,260],Learning:[190,75]};
var sel="Travel",shared=true;
function draw(){
var h='';T.forEach(function(t){h+='<button aria-pressed="'+(t==sel)+'" data-t="'+t+'">'+t+'</button>';});
document.getElementById('w4t').innerHTML=h;
document.querySelectorAll('#w4t button').forEach(function(b){b.onclick=function(){sel=b.dataset.t;draw();};});
var ids=['w4a','w4b','w4c'];
ids.forEach(function(id,i){var el=document.getElementById(id),o='';
T.forEach(function(t){var lab=shared?t:alt[t][i],hi=t==sel;
var extra=i==0?' ('+n[t][0]+' searches)':i==1?' ('+n[t][1]+' clicks)':'';
o+='<div class="'+(hi?'hl':'')+'" style="padding:3px 6px;margin:3px 0">'+lab+'<span class="note">'+extra+'</span></div>';});
el.innerHTML=o;});
document.getElementById('w4n').innerHTML=shared?'<span class="good">Same term in all three.</span> You can join them: Travel gets '+n[sel][0]+' searches but only '+n[sel][1]+' menu clicks. That gap is worth investigating.':'<span class="bad">Three different labels for one topic.</span> Someone has to match them by hand, so the comparison rarely gets made.';
}
document.querySelectorAll('#w4 button[data-v]').forEach(function(b){b.onclick=function(){shared=b.dataset.v=="1";document.querySelectorAll('#w4 button[data-v]').forEach(function(x){x.setAttribute('aria-pressed',x==b)});draw();};});
draw();
})();
</script>

## Keep it practical

- **Start small.** Ten to thirty top-level terms is plenty.
- **One owner for the list.** Changes go through one person or a small group.
- **Tag content once.** The same tag feeds search filters, menus and reports.
- **Use it for both languages.** Each term has an English and a French label, linked as a pair.
- **Reuse the department's existing lists.** Many organizations already keep a branch or topic list in an identity or HR system. Import it rather than invent a new one.

The payoff is simple: when someone asks "how is the Travel area doing?", you can answer from one place.
