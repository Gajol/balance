---
layout: single
title: "Why Your Website Needs a Product Manager After Launch"
date: 2026-10-23 09:25:00 -0400
description: "Projects end at launch, but content ages from that day. Someone has to own the product after the project team leaves."
excerpt: "Projects end at launch, but content ages from that day. Someone has to own the product after the project team leaves."
theme: digital
author_profile: false
classes: full-width
tags: [product management, ux, governance, intranet]
---

A project delivers a website. A **product** keeps being useful.

On launch day, content is fresh, links work and the search finds the right page. Then the project team leaves. Without someone in charge, small things slip. Pages age, links break, and people stop trusting the site.

A product owner (or product manager) is the person who:

- decides what to improve next, based on evidence;
- reads the content health and search reports;
- speaks for readers when priorities compete;
- keeps the roadmap short and visible.

## See the difference

Choose which habits the owner keeps, then pick a point in time. The faces and the row of ten people show what a typical staff member experiences, with and without an owner. The dots on the chart mark where things go wrong, and which habit would prevent each one. These numbers are an illustrative model, not measurements.

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
<div class="wx" markdown="0" id="w6">
<style>
#w6 .wc{display:grid;grid-template-columns:minmax(0,1.2fr) minmax(0,1fr);gap:16px;align-items:start}
@media (max-width:800px){#w6 .wc{grid-template-columns:1fr}}
#w6 .col{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:10px;margin-bottom:8px}
#w6 .col.me{border:2px solid #2da44e}
#w6 .col.no{border:2px solid #e5534b}
#w6 .face{font-size:2.6em;line-height:1}
#w6 .ppl{display:flex;flex-wrap:wrap;gap:3px;margin:6px 0}
#w6 .ppl svg{width:20px;height:28px}
#w6 .q{font-style:italic;margin-top:4px}
#w6 circle.mk{cursor:pointer}
#w6 circle.mk:focus{outline:none;stroke:#1f6feb;stroke-width:3}
</style>
<div class="row" role="group" aria-label="Owner habits"><strong>Owner habits:</strong>
<button data-k="rep" aria-pressed="false">Read health reports monthly</button>
<button data-k="rem" aria-pressed="false">Send review reminders</button>
<button data-k="imp" aria-pressed="false">Ship small improvements</button>
</div>
<div class="row" role="group" aria-label="When"><strong>When:</strong>
<button data-y="0" aria-pressed="false">Launch</button>
<button data-y="12" aria-pressed="false">Year 1</button>
<button data-y="24" aria-pressed="true">Year 2</button>
<button data-y="36" aria-pressed="false">Year 3</button>
</div>
<div class="wc">
<div>
<svg viewBox="0 0 420 200" style="width:100%" role="img" aria-label="Fresh content over 36 months, with markers where things go wrong" id="w6g"></svg>
<div class="note">Hover, tap or tab to a dot to see what goes wrong, and which habit prevents it.</div>
<div class="card" id="w6w" aria-live="polite"></div>
</div>
<div>
<div class="col no"><div class="row" style="margin:0"><span class="face" id="w6fa" aria-hidden="true"></span><span><span class="note">Without an owner</span><br><strong id="w6la"></strong></span></div><div class="ppl" id="w6pa"></div><div id="w6ca" class="note"></div><div class="q" id="w6qa"></div></div>
<div class="col me"><div class="row" style="margin:0"><span class="face" id="w6fb" aria-hidden="true"></span><span><span class="note">With your habits</span><br><strong id="w6lb"></strong></span></div><div class="ppl" id="w6pb"></div><div id="w6cb" class="note"></div><div class="q" id="w6qb"></div></div>
</div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var s={rep:false,rem:false,imp:false},mo=24,sel=null;
function f(t,n){var floor=30+20*n,tau=10+12*n;return floor+(95-floor)*Math.exp(-t/tau);}
function nn(){return (s.rep?1:0)+(s.rem?1:0)+(s.imp?1:0);}
var EV=[{t:6,w:"First broken links appear. Nobody owns them, so nobody fixes them.",h:"imp",hn:"Ship small improvements",p:function(){return s.imp;}},
{t:12,w:"Review dates pass. Nobody is reminded, so pages quietly go stale.",h:"rem",hn:"Send review reminders",p:function(){return s.rem;}},
{t:18,w:"Search starts putting old pages first. Newer, correct pages are buried.",h:"rep",hn:"Read health reports monthly",p:function(){return s.rep;}},
{t:24,w:"Staff stop searching and start phoning colleagues instead.",h:null,hn:"any two habits",p:function(){return nn()>=2;}},
{t:30,w:"New hires are told: do not trust the site, just ask someone.",h:null,hn:"all three habits",p:function(){return nn()==3;}}];
function mood(v){return v>=80?["&#128516;","Confident","Found it in seconds."]:v>=65?["&#128578;","Comfortable","Mostly fine. I double-check now and then."]:v>=50?["&#128528;","Not sure","I am never sure it is current, so I ask a colleague."]:v>=35?["&#128533;","Frustrated","I stopped using search. I just phone."]:["&#128543;","Given up","Nobody updates that site. I do not bother."];}
function ppl(v){var k=Math.round(v/10),h='';for(var i=0;i<10;i++){var ok=i<k;h+='<svg viewBox="0 0 20 28" aria-hidden="true"><circle cx="10" cy="7" r="5" fill="'+(ok?'#2da44e':'rgba(128,128,128,.45)')+'"/><path d="M2 27 Q2 14 10 14 Q18 14 18 27Z" fill="'+(ok?'#2da44e':'rgba(128,128,128,.45)')+'"/></svg>';}return h;}
function panel(sfx,v){var m=mood(v),k=Math.round(v/10);g('w6f'+sfx).innerHTML=m[0];g('w6l'+sfx).textContent=m[1];g('w6p'+sfx).innerHTML=ppl(v);g('w6c'+sfx).textContent=k+' of 10 find the right page. '+(10-k)+' phone someone.';g('w6q'+sfx).textContent='“'+m[2]+'”';}
function show(e){var ok=e.p();g('w6w').innerHTML='<strong>Month '+e.t+(ok?' <span class="good">&mdash; prevented</span>':' <span class="bad">&mdash; this happens</span>')+'</strong><br>'+e.w+'<br><span class="note">'+(ok?'Your habits stop this: ':'Prevented by: ')+e.hn+'.</span>';}
function path(k){var d='';for(var t=0;t<=36;t++){d+=(t?'L':'M')+(30+t*10)+' '+(170-f(t,k)*1.5).toFixed(1);}return d;}
function draw(){
var n=nn(),a=Math.round(f(mo,0)),b=Math.round(f(mo,n));
var x=30+mo*10,c='<line x1="30" y1="170" x2="390" y2="170" stroke="gray"/><line x1="30" y1="20" x2="30" y2="170" stroke="gray"/>';
c+='<text x="2" y="24" font-size="10" fill="currentColor">100%</text><text x="8" y="172" font-size="10" fill="currentColor">0</text><text x="30" y="188" font-size="10" fill="currentColor">launch</text><text x="165" y="188" font-size="10" fill="currentColor">18 months</text><text x="350" y="188" font-size="10" fill="currentColor">36 months</text>';
c+='<text x="150" y="14" font-size="10" fill="#e5534b">dashed: no owner</text><text x="260" y="14" font-size="10" fill="#2da44e">solid: your habits</text>';
c+='<line x1="'+x+'" y1="20" x2="'+x+'" y2="170" stroke="#1f6feb" stroke-dasharray="2 3"/>';
c+='<path d="'+path(0)+'" fill="none" stroke="#e5534b" stroke-width="2" stroke-dasharray="4 3"/><path d="'+path(n)+'" fill="none" stroke="#2da44e" stroke-width="3"/>';
EV.forEach(function(e,i){var ok=e.p();c+='<circle class="mk" data-i="'+i+'" tabindex="0" role="button" aria-label="Month '+e.t+': '+e.w+'" cx="'+(30+e.t*10)+'" cy="'+(170-f(e.t,0)*1.5).toFixed(1)+'" r="7" fill="'+(ok?'#fff':'#e5534b')+'" stroke="'+(ok?'#2da44e':'#e5534b')+'" stroke-width="2.5"/>';});
g('w6g').innerHTML=c;
document.querySelectorAll('#w6g circle.mk').forEach(function(m){var e=EV[+m.dataset.i];m.onmouseenter=m.onfocus=m.onclick=function(){sel=+m.dataset.i;show(e);};});
panel('a',a);panel('b',b);
if(sel===null){var last=0;EV.forEach(function(e,i){if(e.t<=mo)last=i;});show(EV[last]);}else show(EV[sel]);
}
document.querySelectorAll('#w6 button[data-k]').forEach(function(b){b.onclick=function(){s[b.dataset.k]=!s[b.dataset.k];b.setAttribute('aria-pressed',s[b.dataset.k]);draw();};});
document.querySelectorAll('#w6 button[data-y]').forEach(function(b){b.onclick=function(){mo=+b.dataset.y;sel=null;document.querySelectorAll('#w6 button[data-y]').forEach(function(x){x.setAttribute('aria-pressed',x==b);});draw();};});
draw();
})();
</script>

## Make it real

- **Name the role before the project ends.** Not "to be decided".
- **Give it time.** Even a part-time owner, with a protected few hours a week, beats none.
- **Fund it.** Include run costs in the business case, not only build costs.
- **Keep a short roadmap.** Three to five items, chosen from search logs, feedback and health reports.

A launch is the start of the product's life. Plan for the day after it.
