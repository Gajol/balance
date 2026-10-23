---
layout: single
title: "Can I Trust This Page? Three Signals Every Intranet Page Should Show"
date: 2026-10-23 09:00:00 -0400
description: "Owner, last reviewed date and status: three small signals that turn a page people doubt into a page people use."
excerpt: "Owner, last reviewed date and status: three small signals that turn a page people doubt into a page people use."
theme: digital
tags: [intranet, content, trust, ux]
---

People do not read an intranet page and then decide if it is true. They decide first, in a second or two, whether to believe it. If they doubt it, they phone a colleague, and the page has failed.

Three small signals fix most of this.

1. **Owner.** A named team or role, with a way to reach them.
2. **Last reviewed.** Not "last edited". A page can be edited yesterday and not checked in years.
3. **Status.** Current, needs review, or retired.

Try it below. Turn each signal on and off, then move the slider to age the page.

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
<div class="wx" markdown="0" id="w1">
<div class="row" role="group" aria-label="Signals">
<button aria-pressed="true" data-k="owner" title="Who to ask, and who is accountable">Owner</button>
<button aria-pressed="true" data-k="date" title="When a person last checked the facts">Last reviewed</button>
<button aria-pressed="true" data-k="status" title="Tells the reader how far to rely on the page">Status</button>
</div>
<label>Months since last review: <input type="range" min="0" max="24" value="3" id="w1m"> <strong id="w1mv">3</strong></label>
<div class="card" id="w1c"></div>
<div id="w1t" aria-live="polite"></div>
</div>
<script>
(function(){
var on={owner:true,date:true,status:true},m=document.getElementById('w1m');
function draw(){
var mo=+m.value,stale=mo>12;
document.getElementById('w1mv').textContent=mo;
var h='<strong>Travel claim process</strong><br>';
h+=on.owner?'Owner: Finance Services team, <u>contact the team</u><br>':'<span class="note">No owner shown</span><br>';
h+=on.date?'Last reviewed: '+mo+' month'+(mo==1?'':'s')+' ago<br>':'<span class="note">No review date shown</span><br>';
if(on.status)h+='Status: '+(stale?'<span class="bad">Needs review</span>':'<span class="good">Current</span>');
else h+='<span class="note">No status shown</span>';
document.getElementById('w1c').innerHTML=h;
var n=on.owner+on.date+on.status,t;
if(n==3)t=stale?'The page admits it is old. Readers know to double-check. That honesty keeps trust.':'All three signals are shown and the page is fresh. A reader can act without phoning anyone.';
else if(n==0)t='No signals. The reader has to guess. Most will ask a colleague instead.';
else t='Only '+n+' of 3 signals. Better, but the reader still has a gap to fill with guesswork.';
document.getElementById('w1t').innerHTML='<p>'+t+'</p>';
}
document.querySelectorAll('#w1 button').forEach(function(b){b.onclick=function(){var k=b.dataset.k;on[k]=!on[k];b.setAttribute('aria-pressed',on[k]);draw();};});
m.oninput=draw;draw();
})();
</script>

## Why this works

- **It costs little.** Three fields on a page template.
- **It makes people accountable.** An owner who sees their name on a page tends to look after it.
- **It lets the system help.** Once a review date exists, a reminder can be sent automatically, and old pages can be flagged or archived.

## One rule

Do not show a signal you cannot keep true. A "Current" label on a page nobody reviews is worse than no label at all. Pair every signal with a process that keeps it honest. The next posts in this series cover that process.
