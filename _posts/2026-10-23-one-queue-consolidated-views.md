---
layout: single
title: "One Queue: Consolidated Views So Owners and Managers Can Act in Bulk"
date: 2026-10-23 09:08:00 -0400
description: "Owners with many pages, and managers above them, need one prioritized queue instead of dozens of separate tasks. See how roll-up views and bulk actions save time."
excerpt: "Owners with many pages, and managers above them, need one prioritized queue instead of dozens of separate tasks. See how roll-up views and bulk actions save time."
theme: digital
author_profile: false
classes: full-width
tags: [product management, ux, automation, content, governance]
---

Automation can flag a page. Flagging fifty pages as fifty separate emails is a different problem. Owners ignore the noise, and managers cannot see the pattern.

The next step after [Automation Flags, People Decide]({{ '/automation-flags-people-decide/' | relative_url }}) is a **consolidated view**: one queue that gathers everything waiting on a person, ranks it, and lets them act on many items at once.

## Three views, one set of data

The same flags, shown at three levels:

- **Content owner: "My content."** Every page I am responsible for, with what needs doing, ranked.
- **Manager: "My team's content."** The same, plus who owns what, so a manager can spot a person who is overloaded or a pile that is not moving.
- **Product owner: "Whole site."** A roll-up by branch, so effort goes where the problem is biggest.

## What makes a queue useful

1. **Ranked, not just listed.** Priority should reflect how many people use the page and how overdue it is, so the first item matters most.
2. **Grouped by what is needed.** "Still correct," "update" and "retire" are quick decisions. Batch them.
3. **Bulk actions.** Select several pages and apply one decision. The most common answer, "still correct," should take seconds.
4. **Honest roll-ups.** Counts at the top show whether the pile is growing or shrinking.
5. **Same data for everyone.** Owners and managers see the same numbers at different levels, so nobody argues about whose figures are right.

## How it feels

The same 14 flagged pages can reach an owner in three very different ways. Pick one and watch the owner's mood. The times and counts are an illustrative model, not measurements.

<style>
#w12 .wc{display:grid;grid-template-columns:minmax(0,300px) minmax(0,1fr);gap:16px;align-items:start}
@media (max-width:760px){#w12 .wc{grid-template-columns:1fr}}
#w12 .face{font-size:3.4em;line-height:1}
#w12 .m{display:grid;grid-template-columns:1fr 1fr 1fr;gap:6px;text-align:center;margin-top:8px}
#w12 .m div{border:1px solid rgba(128,128,128,.35);border-radius:6px;padding:4px}
#w12 .m b{display:block;font-size:1.3em}
#w12 .em{border:1px solid rgba(128,128,128,.4);border-radius:6px;padding:5px 8px;margin:3px 0;font-size:.88em;display:flex;justify-content:space-between;gap:8px}
#w12 .em .dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:#e5534b;margin-right:6px}
#w12 .vis{max-height:330px;overflow:hidden;position:relative}
#w12 .fade:after{content:"";position:absolute;left:0;right:0;bottom:0;height:60px;background:linear-gradient(transparent,var(--bgc,#fff))}
#w12 .qrow{display:grid;grid-template-columns:1.5em 1fr 90px;gap:8px;align-items:center;padding:5px 2px;border-bottom:1px solid rgba(128,128,128,.25);font-size:.9em}
#w12 .batch{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:10px;margin:6px 0;display:flex;justify-content:space-between;align-items:center;gap:8px;flex-wrap:wrap}
#w12 .batch.done{border-color:#2da44e;background:rgba(45,164,78,.12)}
</style>
<div class="wx" markdown="0" id="w12">
<div class="row" role="group" aria-label="How the flags arrive">
<button data-s="0" aria-pressed="true">1. Separate emails</button>
<button data-s="1" aria-pressed="false">2. One ranked queue</button>
<button data-s="2" aria-pressed="false">3. Bulk decisions</button>
</div>
<div class="wc">
<div class="card" id="w12m" aria-live="polite"></div>
<div class="vis" id="w12v"></div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var P=[["Leave policy","Stale","c"],["VPN setup guide","Stale","u"],["Password reset","Broken link","u"],["Expense policy","Stale","c"],["Onboarding checklist","Failed searches","u"],["Travel claim process","Stale","c"],["Pay dates","Stale","c"],["Software catalogue","Failed searches","u"],["Year-end deadlines","Failed searches","u"],["Purchase card rules","Stale","c"],["Vendor onboarding","Broken link","u"],["Petty cash form","No accessibility check","r"],["Budget calendar","Stale","r"],["Printer help","Stale","r"]];
var NAMES={c:"Still correct",u:"Needs an update",r:"Retire"};
var st=0,done={c:false,u:false,r:false};
function cnt(k){return P.filter(function(x){return x[2]==k;}).length;}
function mood(){
 if(st==0)return {f:"&#128565;",l:"Overwhelmed and confused",q:"Which one first? Is any of this urgent? I will deal with it later.",a:P.length,b:"~42 min",c:"~56"};
 if(st==1)return {f:"&#128578;",l:"Clear",q:"Now I can see what matters most, and why.",a:1,b:"~20 min",c:"~28"};
 var d=(done.c?1:0)+(done.u?1:0)+(done.r?1:0);
 if(d==3)return {f:"&#128516;",l:"Efficient. Queue clear.",q:"Done in one sitting, and the report shows it.",a:0,b:"~8 min",c:"~9"};
 return {f:"&#128578;",l:"In control",q:"Three decisions, not fourteen emails.",a:3-d,b:"~"+(8+(3-d)*4)+" min",c:"~"+(9+(3-d)*5)};
}
function draw(){
 var m=mood(),lab=st==0?"Messages to open":st==1?"Views to open":"Decisions left";
 g('w12m').innerHTML='<div class="row" style="margin:0"><span class="face" aria-hidden="true">'+m.f+'</span><span><span class="note">How the owner feels</span><br><strong style="font-size:1.1em">'+m.l+'</strong></span></div><div class="q" style="font-style:italic;margin-top:6px">“'+m.q+'”</div><div class="m"><div><b>'+m.a+'</b><span class="note">'+lab+'</span></div><div><b>'+m.b+'</b><span class="note">Time</span></div><div><b>'+m.c+'</b><span class="note">Clicks</span></div></div>';
 var h='';
 if(st==0){P.forEach(function(x,i){h+='<div class="em"><span><span class="dot"></span>Page flagged: '+x[0]+'</span><span class="note">'+x[1]+'</span></div>';});
  g('w12v').className='vis fade';}
 else if(st==1){h+='<div class="note" style="margin-bottom:4px">My content, ranked by readers affected and how overdue:</div>';
  P.slice(0,8).forEach(function(x,i){var w=Math.round(100-i*9);h+='<div class="qrow"><span>'+(i+1)+'</span><span>'+x[0]+' <span class="note">('+x[1]+')</span></span><div class="track"><div class="fill" style="width:'+w+'%;background:'+(i<3?"#e5534b":"#1f6feb")+'"></div></div></div>';});
  h+='<div class="note" style="margin-top:6px">+ 6 more below, grouped by the decision needed.</div>';g('w12v').className='vis';}
 else{h+='<div class="note" style="margin-bottom:4px">Same 14 pages, grouped by decision. Apply each in one step.</div>';
  ['c','u','r'].forEach(function(k){h+='<div class="batch'+(done[k]?' done':'')+'"><span><strong>'+NAMES[k]+'</strong> <span class="note">('+cnt(k)+' pages)</span></span>'+(done[k]?'<span class="good">Done</span>':'<button data-b="'+k+'">Apply to all '+cnt(k)+'</button>')+'</div>';});
  g('w12v').className='vis';}
 g('w12v').innerHTML=h;
 document.querySelectorAll('#w12 button[data-b]').forEach(function(b){b.onclick=function(){done[b.dataset.b]=true;draw();};});
}
document.querySelectorAll('#w12 button[data-s]').forEach(function(b){b.onclick=function(){st=+b.dataset.s;document.querySelectorAll('#w12 button[data-s]').forEach(function(x){x.setAttribute('aria-pressed',x==b);});draw();};});
draw();
})();
</script>

What to notice:

- **Fourteen emails are fourteen interruptions.** None says which matters most, so the easy response is to defer all of them.
- **A ranked queue removes the guessing.** The owner still decides each page, but knows where to start.
- **Bulk decisions are where the time comes back.** Grouping by the decision needed turns many small chores into a few confident choices.

## Try it

Switch the view, change the sort, tick a few pages and choose an action. The numbers are made up.

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

.wx .chip{display:inline-block;padding:1px 8px;border-radius:10px;border:1px solid rgba(128,128,128,.5);font-size:.85em}
.wx td.l{text-align:left}
</style>
<div class="wx" markdown="0" id="w11">
<div class="row" role="group" aria-label="View">
<strong>View:</strong>
<button data-v="owner" aria-pressed="true">Content owner (Ana)</button>
<button data-v="mgr" aria-pressed="false">Manager (Finance)</button>
<button data-v="site" aria-pressed="false">Product owner (whole site)</button>
</div>
<div class="row"><label>Sort by: <select id="w11s"><option value="p">Priority</option><option value="w">Most overdue</option><option value="v">Most visited</option></select></label></div>
<div id="w11h"></div>
<div style="overflow-x:auto"><table id="w11t"></table></div>
<div class="row" id="w11b"></div>
<div class="note" id="w11m" aria-live="polite"></div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var D0=[
["Travel claim process","Ana","Finance","Stale",4200,20],["Expense policy","Ana","Finance","Stale",2600,34],["Year-end deadlines","Ana","Finance","Failed searches",1800,6],["Petty cash form","Ana","Finance","No accessibility check",300,48],
["Purchase card rules","Ben","Finance","Stale",1500,26],["Vendor onboarding","Ben","Finance","Broken link",900,10],["Budget calendar","Ben","Finance","Stale",700,52],
["Leave policy","Chloe","HR","Stale",5200,30],["Onboarding checklist","Chloe","HR","Failed searches",3900,8],["Pay dates","Chloe","HR","Stale",3100,14],
["VPN setup guide","Dev","IT","Stale",6100,40],["Password reset","Dev","IT","Broken link",7400,4],["Printer help","Dev","IT","Stale",800,60],["Software catalogue","Dev","IT","Failed searches",2200,12]];
var D=[],view="owner",branch=null,sel={},done=0,msg="";
function init(){D=D0.map(function(r,i){return {id:i,t:r[0],o:r[1],b:r[2],i:r[3],v:r[4],w:r[5]};});sel={};done=0;msg="";}
function pri(x){return Math.round(x.v/100*(1+x.w/26));}
function rows(){var r=D.filter(function(x){if(view=="owner")return x.o=="Ana";if(view=="mgr")return x.b=="Finance";return branch?x.b==branch:true;});
var k=g('w11s').value;r.sort(function(a,b){return k=="p"?pri(b)-pri(a):k=="w"?b.w-a.w:b.v-a.v;});return r;}
function draw(){
var r=rows(),all=D.filter(function(x){if(view=="owner")return x.o=="Ana";if(view=="mgr")return x.b=="Finance";return true;});
var top=r.length?Math.max.apply(null,r.map(pri)):1;
var hi=all.filter(function(x){return pri(x)>=40;}).length;
var h='<div class="cols"><div class="card"><span class="note">Open items</span><br><strong style="font-size:1.4em">'+all.length+'</strong></div><div class="card"><span class="note">High priority</span><br><strong style="font-size:1.4em" class="'+(hi?'bad':'good')+'">'+hi+'</strong></div><div class="card"><span class="note">Handled this session</span><br><strong style="font-size:1.4em" class="good">'+done+'</strong></div></div>';
if(view=="site"){var B={};D.forEach(function(x){B[x.b]=B[x.b]||{n:0,h:0};B[x.b].n++;if(pri(x)>=40)B[x.b].h++;});
h+='<div class="row"><span class="note">Branch (click to filter):</span>';Object.keys(B).forEach(function(k){h+='<button data-br="'+k+'" aria-pressed="'+(branch==k)+'">'+k+': '+B[k].n+' open, '+B[k].h+' high</button>';});h+='<button data-br="">All</button></div>';}
g('w11h').innerHTML=h;
var t='<tr><th><input type="checkbox" id="w11a" aria-label="Select all"></th><th>Page</th>'+(view!="owner"?'<th>Owner</th>':'')+(view=="site"?'<th>Branch</th>':'')+'<th>Needs</th><th>Visits / mo</th><th>Weeks overdue</th><th>Priority</th></tr>';
r.forEach(function(x){var p=pri(x);t+='<tr class="'+(sel[x.id]?'pick':'')+'"><td><input type="checkbox" data-id="'+x.id+'" aria-label="Select '+x.t+'"'+(sel[x.id]?' checked':'')+'></td><td class="l">'+x.t+'</td>'+(view!="owner"?'<td>'+x.o+'</td>':'')+(view=="site"?'<td>'+x.b+'</td>':'')+'<td><span class="chip">'+x.i+'</span></td><td>'+x.v+'</td><td>'+x.w+'</td><td style="min-width:90px"><div class="track"><div class="fill" style="width:'+Math.round(p/top*100)+'%;background:'+(p>=40?'#e5534b':'#1f6feb')+'"></div></div></td></tr>';});
if(!r.length)t+='<tr><td colspan="7" class="l"><span class="good">Nothing waiting. The queue is clear.</span></td></tr>';
g('w11t').innerHTML=t;
var n=Object.keys(sel).filter(function(k){return sel[k];}).length;
g('w11b').innerHTML='<span>'+n+' selected:</span><button data-a="Confirmed still correct"'+(n?'':' disabled')+'>Still correct</button><button data-a="Retired (archived, restorable)"'+(n?'':' disabled')+'>Retire</button><button data-a="Reassigned to the product owner"'+(n?'':' disabled')+'>Reassign</button><button id="w11r">Reset demo</button>';
g('w11m').textContent=msg||(n?'':'Tick one or more pages, then choose an action. Without a consolidated view, each one would be its own email.');
document.querySelectorAll('#w11h button[data-br]').forEach(function(b){b.onclick=function(){branch=b.dataset.br||null;sel={};draw();};});
document.querySelectorAll('#w11t input[data-id]').forEach(function(c){c.onchange=function(){sel[c.dataset.id]=c.checked;msg="";draw();};});
var A=g('w11a');if(A)A.onchange=function(){r.forEach(function(x){sel[x.id]=A.checked;});msg="";draw();};
document.querySelectorAll('#w11b button[data-a]').forEach(function(b){b.onclick=function(){var ids=Object.keys(sel).filter(function(k){return sel[k];}).map(Number);D=D.filter(function(x){return ids.indexOf(x.id)<0;});done+=ids.length;msg=b.dataset.a+': '+ids.length+' page'+(ids.length>1?'s':'')+' in one step (one decision each, but no separate emails, logins or searches).';sel={};draw();};});
g('w11r').onclick=function(){init();draw();};
}
document.querySelectorAll('#w11 button[data-v]').forEach(function(b){b.onclick=function(){view=b.dataset.v;branch=null;sel={};msg="";document.querySelectorAll('#w11 button[data-v]').forEach(function(x){x.setAttribute('aria-pressed',x==b);});draw();};});
g('w11s').onchange=draw;
init();draw();
})();
</script>

What to notice:

- **Priority is not the same as age.** A very old page nobody reads can wait. A moderately old page that thousands use cannot.
- **Managers see people as well as pages.** The manager view adds the owner column, so overload becomes visible.
- **The roll-up helps the product owner decide where to spend effort.** Clicking a branch narrows the work.
- **Bulk "still correct" is the big saver.** Most review work is confirming that nothing changed.

## Design rules that keep it honest

- **Every number clicks through.** A count in a header must open the list behind it.
- **Bulk does not mean blind.** Show what will change before it happens, and make every action undoable.
- **Log decisions.** Who confirmed what, and when. That record is what makes "reviewed" mean something.
- **Keep one source of truth.** The queue reads from the same health data as the report. No second spreadsheet.
- **Keep it small.** If the queue is always long, the thresholds are wrong, or there are too many pages. Fix that, not the screen.

A good queue turns a pile of obligations into a short list of decisions.
