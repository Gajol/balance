---
layout: single
title: "Getting and Keeping the Team: Skills, Experience and Resources Over Time"
date: 2026-10-23 09:30:00 -0400
description: "A web platform is only as strong as the team behind it. Explore which skills a team needs, how experience changes coverage, and how hiring delays and turnover open gaps over time."
excerpt: "A web platform is only as strong as the team behind it. Explore which skills a team needs, how experience changes coverage, and how hiring delays and turnover open gaps over time."
theme: digital
author_profile: false
classes: wide
tags: [resourcing, skills, operating model, product management, staffing]
---

A good design with the wrong team fails. A good design with the right team that has left fails too.

Most plans list the positions and stop. Two harder questions are left out:

1. **Do the people we can get actually cover the skills we need?** Experience matters, not just headcount.
2. **Will they be there when we need them?** Hiring takes time, new people take time to become useful, and some will leave.

This post gives you a small model for each. The numbers are made up. Use your own.

## Part 1: Who covers which skill?

Nine generic positions. Tick a person as hired, set their experience, and watch the skill coverage feed one headline result: how much of the product vision is realized. Experience counts as junior 0.5, intermediate 0.8, senior 1.0. Tick "leaves" to see what one departure does.

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
<div class="wx" markdown="0" id="w7">
<div style="overflow-x:auto"><table id="w7t"></table></div>
<div id="w7c" style="margin-top:10px"></div>
<div class="row"><button id="w7all">Fill all (intermediate)</button><button id="w7none">Clear</button></div>
<div class="note" id="w7n" aria-live="polite"></div>
</div>
<script>
(function(){
var P=[["Product owner","Business","Product management"],["Content strategist","Business","Content and taxonomy"],["Editor / publisher","Business","Bilingual content"],["Bilingual editor","Business","Bilingual content"],["Drupal developer","IT","Drupal"],["Search and analytics specialist","IT","Search and analytics"],["Platform administrator","IT","Operations"],["Accessibility specialist","Business","Accessibility"],["Service desk analyst","IT","Operations"]];
var W=[0.5,0.8,1.0],L=["Junior","Intermediate","Senior"];
var st=P.map(function(){return {on:false,x:1,gone:false};});
var skills=[];P.forEach(function(p){if(skills.indexOf(p[2])<0)skills.push(p[2]);});
function draw(){
var h='<tr><th>Position</th><th>Type</th><th>Skill</th><th>Hired</th><th>Experience</th><th>Leaves</th></tr>';
P.forEach(function(p,i){var s=st[i];h+='<tr class="'+(s.on&&!s.gone?'pick':'')+'"><td>'+p[0]+'</td><td>'+p[1]+'</td><td>'+p[2]+'</td><td><input type="checkbox" aria-label="Hired: '+p[0]+'" data-a="on" data-i="'+i+'"'+(s.on?' checked':'')+'></td><td><select aria-label="Experience: '+p[0]+'" data-a="x" data-i="'+i+'">'+L.map(function(l,j){return '<option value="'+j+'"'+(s.x==j?' selected':'')+'>'+l+'</option>';}).join('')+'</select></td><td><input type="checkbox" aria-label="Leaves: '+p[0]+'" data-a="gone" data-i="'+i+'"'+(s.gone?' checked':'')+(s.on?'':' disabled')+'></td></tr>';});
document.getElementById('w7t').innerHTML=h;
var c='',gaps=0,thin=0,single=0,pcts=[];
skills.forEach(function(k){var w=0,n=0;P.forEach(function(p,i){if(p[2]==k&&st[i].on&&!st[i].gone){w+=W[st[i].x];n++;}});
var need=k=="Operations"||k=="Bilingual content"?2:1,pct=Math.min(100,Math.round(w/need*100)),lab,cls;pcts.push(pct);
if(n==0){lab="Gap";cls="bad";gaps++;}else if(pct<80){lab="Thin";cls="bad";thin++;}else if(n==1&&need==1){lab="Covered by one person";cls="";single++;}else{lab="Covered";cls="good";}
c+='<div style="margin:6px 0"><div class="row" style="justify-content:space-between;margin:0"><span>'+k+'</span><span class="'+cls+'">'+lab+'</span></div><div class="track"><div class="fill" style="width:'+pct+'%;background:rgba(128,128,128,.7)"></div></div></div>';});
var avg=pcts.reduce(function(x,y){return x+y;},0)/pcts.length,mn=Math.min.apply(null,pcts),v=Math.round(0.6*avg+0.4*mn),vc=v>=80?'#12b886':v>=50?'#f59f00':'#e5534b',vl=v>=80?'On track':v>=50?'Partly realized':'At risk';
var vh='<div class="card" style="border:2px solid '+vc+';padding:12px"><div class="row" style="justify-content:space-between;margin:0"><strong style="font-size:1.15em">Vision realized: the product people will actually use</strong><strong style="font-size:1.3em;color:'+vc+'">'+v+'%</strong></div><div class="track" style="height:22px;margin-top:6px"><div class="fill" style="height:22px;width:'+v+'%;background:'+vc+'"></div></div><div class="note" style="margin-top:6px">'+vl+'. Skills below feed it, and it is held back by the weakest ones.</div></div><div class="note" style="margin:8px 0 2px">Skills that feed the vision</div>';
document.getElementById('w7c').innerHTML=vh+c;
var m=gaps?gaps+' skill'+(gaps>1?'s have':' has')+' nobody. ':'No skill is empty. ';
if(thin)m+=thin+' thin. ';
if(single)m+=single+' depend on a single person, so one resignation becomes a gap. ';
document.getElementById('w7n').textContent=m;
document.querySelectorAll('#w7t input,#w7t select').forEach(function(e){e.onchange=function(){var i=+e.dataset.i,a=e.dataset.a;if(a=='x')st[i].x=+e.value;else{st[i][a]=e.checked;if(a=='on'&&!e.checked)st[i].gone=false;}draw();};});
}
document.getElementById('w7all').onclick=function(){st=P.map(function(){return {on:true,x:1,gone:false};});draw();};
document.getElementById('w7none').onclick=function(){st=P.map(function(){return {on:false,x:1,gone:false};});draw();};
draw();
})();
</script>

What to notice:

- **The vision is only as strong as its weakest skills.** One empty skill drags the headline down far more than one strong skill lifts it.
- **Two juniors do not equal one senior.** Coverage counts experience, not bodies.
- **One-person skills are fragile.** They look "covered" until that person resigns.
- **Shared skills are safer.** Two people who each partly cover a skill beat one who covers it fully.

## Part 2: Will they be there when we need them?

Each position has a week it is first needed. A hire is only useful after the hiring delay plus the time to learn the platform. Turnover then removes some of that capacity. Move the sliders. The red area is where the plan is short.

<div class="wx" markdown="0" id="w8">
<div class="row">
<label>Weeks to hire a person: <input type="range" id="w8h" min="4" max="40" value="16"> <strong id="w8hv"></strong></label>
<label>Weeks to become productive: <input type="range" id="w8r" min="0" max="20" value="6"> <strong id="w8rv"></strong></label>
<label>Yearly turnover: <input type="range" id="w8a" min="0" max="40" value="15"> <strong id="w8av"></strong>%</label>
</div>
<svg viewBox="0 0 400 190" style="width:100%;max-width:600px" role="img" aria-label="People needed compared with people productive over 58 weeks" id="w8g"></svg>
<div id="w8o" aria-live="polite"></div>
</div>
<script>
(function(){
var N=[2,4,12,20,2,14,26,30,44];
var T=58;
function g(i){return document.getElementById(i);}
function draw(){
var h=+g('w8h').value,r=+g('w8r').value,a=+g('w8a').value/100;
g('w8hv').textContent=h;g('w8rv').textContent=r;g('w8av').textContent=Math.round(a*100);
var lose=Math.min(0.9,a*(h+r)/52);
var gapW=0,worst=0,worstAt=0,need=[],prod=[];
for(var t=0;t<=T;t++){var nd=N.filter(function(x){return x<=t}).length,pd=N.length&&(t>=h+r)?N.length*(1-lose):0;
pd=Math.min(pd,N.length);
need.push(nd);prod.push(pd);
if(nd-pd>0.5){gapW++;}
if(nd-pd>worst){worst=nd-pd;worstAt=t;}}
var X=function(t){return 30+t*6;},Y=function(v){return 170-v*14;};
var s='<line x1="30" y1="170" x2="380" y2="170" stroke="gray"/><line x1="30" y1="20" x2="30" y2="170" stroke="gray"/>';
var d='M'+X(0)+' '+Y(0);
for(var t=0;t<=T;t++){d+='L'+X(t)+' '+Y(need[t]);}
for(var t=T;t>=0;t--){d+='L'+X(t)+' '+Y(Math.min(need[t],prod[t]));}
s+='<path d="'+d+'Z" fill="#e5534b" fill-opacity=".35"/>';
var ln=function(arr,col,w,dash){var p='';arr.forEach(function(v,t){p+=(t?'L':'M')+X(t)+' '+Y(v).toFixed(1);});return '<path d="'+p+'" fill="none" stroke="'+col+'" stroke-width="'+w+'"'+(dash?' stroke-dasharray="4 3"':'')+'/>';};
s+=ln(need,'#1f6feb',2.5,false)+ln(prod,'#2da44e',2.5,true);
s+='<text x="2" y="24" font-size="10" fill="currentColor">9</text><text x="8" y="172" font-size="10" fill="currentColor">0</text><text x="30" y="186" font-size="10" fill="currentColor">week 0</text><text x="340" y="186" font-size="10" fill="currentColor">week 58</text>';
s+='<text x="60" y="14" font-size="10" fill="#1f6feb">solid: people needed</text><text x="200" y="14" font-size="10" fill="#2da44e">dashed: people productive</text>';
g('w8g').innerHTML=s;
g('w8o').innerHTML=gapW==0?'<span class="good">No gap in this scenario.</span>':'<span class="bad">Short in '+gapW+' of '+(T+1)+' weeks.</span> Worst around week '+worstAt+', short by about '+worst.toFixed(1)+' people.';
}
['w8h','w8r','w8a'].forEach(function(i){g(i).oninput=draw;});
draw();
})();
</script>

What to notice:

- **Start hiring early.** The gap often exists before anyone arrives, because the clock only starts when the posting does.
- **Turnover quietly takes capacity.** Even moderate turnover shaves a visible part off the team.
- **Learning time is real.** A hire who needs months to learn the platform is not a full person on day one.

## What to do about it

- **Plan for the whole life, not just the build.** Run roles are as real as build roles.
- **Hire for coverage.** Aim for at least two people on every critical skill, even if one is part-time or junior.
- **Write things down.** Decision records, a run book and a glossary make a new person useful faster.
- **Keep people interested.** Training, clear career paths and a meaningful product to own help more than any single perk.
- **Use contractors on purpose.** They fill peaks and rare skills well. They are a poor home for knowledge you must keep.
- **Make the risk visible.** Show leaders the gap chart, not just the position list. A chart gets a decision.

The question to ask early: *if our two most important people left next month, what would we lose?*
