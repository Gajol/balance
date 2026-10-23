---
layout: single
title: "Can I Trust This Page? Three Signals Every Intranet Page Should Show"
date: 2026-10-23 09:00:00 -0400
description: "Owner, last reviewed date and status: three small signals that turn a page people doubt into a page people use."
excerpt: "Owner, last reviewed date and status: three small signals that turn a page people doubt into a page people use."
theme: digital
author_profile: false
classes: full-width
tags: [intranet, content, trust, ux]
---

People do not read an intranet page and then decide if it is true. They decide first, in a second or two, whether to believe it. If they doubt it, they phone a colleague, and the page has failed.

Three small signals fix most of this.

1. **Owner.** A named team or role, with a way to reach them.
2. **Last reviewed.** Not "last edited". A page can be edited yesterday and not checked in years.
3. **Status.** Current, needs review, or retired.

Below is a mock-up of staff searching an intranet for **leave policy**. Three results come back. Switch the signals on and off to see how much easier the choice becomes. Then fast-forward a year to see what happens when nobody looks after the pages.

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
<style>
#w1 .sr{border-bottom:1px solid rgba(128,128,128,.3);padding:10px 2px}
#w1 .sr:last-child{border-bottom:0}
#w1 .st{font-size:1.05em;color:#1a73e8;font-weight:600}
#w1 .su{font-size:.8em;color:#2da44e}
#w1 .sn{opacity:.9;margin:2px 0}
#w1 .sg{display:flex;flex-wrap:wrap;gap:6px 16px;margin-top:5px;font-size:.88em}
#w1 .sg span{white-space:nowrap}
#w1 .sg i{font-style:normal;opacity:.7}
#w1 .w1wrap{display:grid;grid-template-columns:minmax(230px,300px) minmax(0,1fr);gap:18px;align-items:start}
@media (max-width:760px){#w1 .w1wrap{grid-template-columns:1fr}}
#w1 .w1side{position:sticky;top:10px}
#w1 .sb{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:6px 14px;background:rgba(128,128,128,.06)}
</style>
<div class="w1wrap">
<div class="w1side">
<div><strong>What the search results show</strong></div>
<div class="row"><button data-k="owner" aria-pressed="true">Owner</button><button data-k="date" aria-pressed="true">Last reviewed</button><button data-k="status" aria-pressed="true">Status</button></div>
<div class="row"><button id="w1ff" aria-pressed="false">Fast-forward 12 months</button></div>
<div class="note" id="w1ffn">Today</div>
<div class="card" id="w1v" aria-live="polite" style="margin-top:10px"></div>
</div>
<div class="w1main">
<div class="note" style="margin-bottom:6px">Staff search for: <strong>leave policy</strong></div>
<div class="sb" id="w1l"></div>
</div>
</div>
</div>
<script>
(function(){
var R=[{t:"Leave policy",u:"intranet / hr / leave-policy",s:"How much leave you earn, how to request it, and who approves it.",o:"HR Policy team",m:3},{t:"Leave policy (2019 version)",u:"intranet / hr / archive / leave-2019",s:"How much leave you earn, how to request it, and who approves it.",o:null,m:52},{t:"Leave: frequently asked questions",u:"intranet / hr / leave-faq",s:"Quick answers about carry-over, sick leave and special leave.",o:"Pay and Benefits team",m:14}];
var on={owner:true,date:true,status:true},ff=0;
function g(i){return document.getElementById(i);}
function ok(r){var m=r.m+ff;return {owner:!!r.o,date:m<=12,status:m<=12};}
function draw(){
var h='',trusted=[],n=(on.owner?1:0)+(on.date?1:0)+(on.status?1:0);
R.forEach(function(r,i){var m=r.m+ff,k=ok(r),g2='';
if(on.owner)g2+='<span><i>Owner:</i> '+(r.o?r.o:'<b class="bad">none</b>')+'</span>';
if(on.date)g2+='<span><i>Last reviewed:</i> '+m+' months ago</span>';
if(on.status)g2+='<span><i>Status:</i> '+(k.status?'<b class="good">&#9679; Current</b>':'<b class="bad">&#9679; Needs review</b>')+'</span>';
var pass=(!on.owner||k.owner)&&(!on.date||k.date)&&(!on.status||k.status);
if(pass)trusted.push(i+1);
h+='<div class="sr"><div class="su">'+r.u+'</div><div class="st">'+(i+1)+'. '+r.t+'</div><div class="sn">'+r.s+'</div>'+(g2?'<div class="sg">'+g2+'</div>':'')+'</div>';});
g('w1l').innerHTML=h;
g('w1ffn').textContent=ff?'Twelve months later. Nobody reviewed anything.':'Today';
var v;
if(n==0)v='<strong>Which one is right?</strong> The three results look almost the same. A reader has to open each one, or phone HR. Many will phone.';
else{
 var hidden=n<3?' <span class="note">(Only '+n+' of 3 signals are shown. Switch on the rest for the full picture.)</span>':'';
 if(trusted.length==0)v='<strong class="bad">No result passes.</strong> Every result is old or unowned. The honest signals tell the reader to check before relying on any of them. That prompts a review.'+hidden;
 else if(trusted.length==1)v='<strong class="good">Click result '+trusted[0]+'.</strong> It is the one with the signals you can rely on. The others show why they should not be trusted.'+hidden;
 else v='<strong>Results '+trusted.join(' and ')+' pass.</strong> The reader can pick without phoning anyone. Result(s) not listed show a warning.'+hidden;
}
var em,ml;
if(n==0){em="&#128533;";ml="Confused";}
else if(trusted.length==0){em="&#128543;";ml="Worried";}
else if(trusted.length==1&&n==3){em="&#128516;";ml="Confident";}
else if(n<3){em="&#128528;";ml="Not sure yet";}
else{em="&#128578;";ml="Comfortable";}
g('w1v').innerHTML='<div class="row" style="margin:0 0 6px"><span style="font-size:3.4em;line-height:1" aria-hidden="true">'+em+'</span><span><span class="note">How the reader feels</span><br><strong style="font-size:1.1em">'+ml+'</strong></span></div>'+v;
}
document.querySelectorAll('#w1 button[data-k]').forEach(function(b){b.onclick=function(){var k=b.dataset.k;on[k]=!on[k];b.setAttribute('aria-pressed',on[k]);draw();};});
g('w1ff').onclick=function(){ff=ff?0:12;this.setAttribute('aria-pressed',!!ff);draw();};
draw();
})();
</script>

## Why this works

- **It costs little.** Three fields on a page template.
- **It makes people accountable.** An owner who sees their name on a page tends to look after it.
- **It lets the system help.** Once a review date exists, a reminder can be sent automatically, and old pages can be flagged or archived.

## One rule

Do not show a signal you cannot keep true. A "Current" label on a page nobody reviews is worse than no label at all. Pair every signal with a process that keeps it honest. The next posts in this series cover that process.
