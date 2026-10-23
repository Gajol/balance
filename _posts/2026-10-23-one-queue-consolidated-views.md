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

## Try it: from noise to one queue

Everything in one place. Start with **separate emails**, one per flagged page, and feel the noise. Then switch to **one queue**, pick who you are (owner, manager or product owner), and make decisions in bulk. The numbers are made up, and the times and clicks are an illustrative model.

<style>
.wx{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:14px;margin:1.2em 0;font-size:.95em}
.wx button,.wx select{font:inherit;padding:4px 10px;border:1px solid rgba(128,128,128,.55);border-radius:6px;background:transparent;color:inherit;cursor:pointer}
.wx button[aria-pressed=true],.wx button.on{background:#1f6feb;color:#fff;border-color:#1f6feb}
.wx button:disabled{opacity:.45;cursor:default}
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
.wx .cols{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:8px}
.wx .chip{display:inline-block;padding:1px 8px;border-radius:10px;border:1px solid rgba(128,128,128,.5);font-size:.85em}
.wx td.l{text-align:left}
#w11 .wc{display:grid;grid-template-columns:minmax(0,290px) minmax(0,1fr);gap:16px;align-items:start}
@media (max-width:820px){#w11 .wc{grid-template-columns:1fr}}
#w11 .face{font-size:3.4em;line-height:1}
#w11 .m{display:grid;grid-template-columns:1fr 1fr 1fr;gap:6px;text-align:center;margin-top:8px}
#w11 .m div{border:1px solid rgba(128,128,128,.35);border-radius:6px;padding:4px}
#w11 .m b{display:block;font-size:1.2em}
#w11 .em{border:1px solid rgba(128,128,128,.4);border-radius:6px;padding:5px 8px;margin:3px 0;font-size:.9em;display:flex;justify-content:space-between;align-items:center;gap:8px}
#w11 .em .dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:#e5534b;margin-right:6px}
#w11 .em button{font-size:.85em;padding:2px 8px}
</style>
<div class="wx" markdown="0" id="w11">
<div class="row" role="group" aria-label="How flags arrive"><strong>Flags arrive as:</strong>
<button data-mode="mail" aria-pressed="true">Separate emails</button>
<button data-mode="queue" aria-pressed="false">One ranked queue</button>
</div>
<div class="row" role="group" aria-label="Who you are"><strong>I am the:</strong>
<button data-v="owner" aria-pressed="true">Content owner (Ana)</button>
<button data-v="mgr" aria-pressed="false">Manager (Finance)</button>
<button data-v="site" aria-pressed="false">Product owner (whole site)</button>
</div>
<div class="wc">
<div>
<div class="card" id="w11mood" aria-live="polite"></div>
<div id="w11h"></div>
</div>
<div>
<div class="row" id="w11sr"><label>Sort by: <select id="w11s"><option value="p">Priority</option><option value="w">Most overdue</option><option value="v">Most visited</option></select></label></div>
<div id="w11mail"></div>
<div style="overflow-x:auto"><table id="w11t"></table></div>
<div class="row" id="w11b"></div>
<div class="note" id="w11m" aria-live="polite"></div>
</div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var D0=[
["Travel claim process","Ana","Finance","Stale",4200,20],["Expense policy","Ana","Finance","Stale",2600,34],["Year-end deadlines","Ana","Finance","Failed searches",1800,6],["Petty cash form","Ana","Finance","No accessibility check",300,48],
["Purchase card rules","Ben","Finance","Stale",1500,26],["Vendor onboarding","Ben","Finance","Broken link",900,10],["Budget calendar","Ben","Finance","Stale",700,52],
["Leave policy","Chloe","HR","Stale",5200,30],["Onboarding checklist","Chloe","HR","Failed searches",3900,8],["Pay dates","Chloe","HR","Stale",3100,14],
["VPN setup guide","Dev","IT","Stale",6100,40],["Password reset","Dev","IT","Broken link",7400,4],["Printer help","Dev","IT","Stale",800,60],["Software catalogue","Dev","IT","Failed searches",2200,12]];
var D=[],view="owner",mode="mail",branch=null,sel={},done=0,clicks=0,msg="";
function init(){D=D0.map(function(r,i){return {id:i,t:r[0],o:r[1],b:r[2],i:r[3],v:r[4],w:r[5]};});sel={};done=0;clicks=0;msg="";}
function pri(x){return Math.round(x.v/100*(1+x.w/26));}
function inView(x){if(view=="owner")return x.o=="Ana";if(view=="mgr")return x.b=="Finance";return branch?x.b==branch:true;}
function rows(){var r=D.filter(inView),k=g('w11s').value;r.sort(function(a,b){return k=="p"?pri(b)-pri(a):k=="w"?b.w-a.w:b.v-a.v;});return r;}
function mood(open,hi,n){
 var m;
 if(mode=="mail"){
  if(open==0)m=["&#128516;","Done, but it took a while","One email at a time. It worked, but it was slow."];
  else if(open<=2)m=["&#128528;","Nearly there","Just a few more emails to chase."];
  else m=["&#128565;","Overwhelmed and confused","Which one first? Is any of this urgent? I will deal with it later."];
 }else{
  if(open==0)m=["&#128516;","Efficient. Queue clear.","Done in one sitting, and the report shows it."];
  else if(n>0)m=["&#128578;","In control","I can decide these together instead of one by one."];
  else m=["&#128578;","Clear","Now I can see what matters most, and why."];
 }
 return m;}
function draw(){
 var r=rows(),all=D.filter(inView),open=all.length,hi=all.filter(function(x){return pri(x)>=40;}).length;
 var n=Object.keys(sel).filter(function(k){return sel[k];}).length;
 var m=mood(open,hi,n),mins=mode=="mail"?open*3:Math.max(open?1:0,Math.round(open*0.8));
 g('w11mood').innerHTML='<div class="row" style="margin:0"><span class="face" aria-hidden="true">'+m[0]+'</span><span><span class="note">How I feel</span><br><strong style="font-size:1.1em">'+m[1]+'</strong></span></div><div style="font-style:italic;margin-top:6px">“'+m[2]+'”</div><div class="m"><div><b>'+open+'</b><span class="note">Open items</span></div><div><b>~'+mins+' min</b><span class="note">Time left</span></div><div><b>'+clicks+'</b><span class="note">Clicks so far</span></div></div>';
 var h='<div class="cols"><div class="card"><span class="note">High priority</span><br><strong style="font-size:1.3em" class="'+(hi?'bad':'good')+'">'+hi+'</strong></div><div class="card"><span class="note">Handled</span><br><strong style="font-size:1.3em" class="good">'+done+'</strong></div></div>';
 if(view=="site"&&mode=="queue"){var B={};D.forEach(function(x){B[x.b]=B[x.b]||{n:0,h:0};B[x.b].n++;if(pri(x)>=40)B[x.b].h++;});
  h+='<div class="row"><span class="note">Branch (click to filter):</span>';Object.keys(B).forEach(function(k){h+='<button data-br="'+k+'" aria-pressed="'+(branch==k)+'">'+k+': '+B[k].n+' open, '+B[k].h+' high</button>';});h+='<button data-br="">All</button></div>';}
 g('w11h').innerHTML=h;
 g('w11sr').style.display=mode=="queue"?"flex":"none";
 var ml='',t='';
 if(mode=="mail"){
  r.forEach(function(x){ml+='<div class="em"><span><span class="dot"></span>Page flagged: '+x.t+(view!="owner"?' <span class="note">('+x.o+')</span>':'')+'</span><span><span class="note">'+x.i+'</span> <button data-one="'+x.id+'">Open and handle</button></span></div>';});
  if(!r.length)ml='<div class="card"><span class="good">Inbox empty.</span></div>';
  g('w11mail').innerHTML=ml;g('w11t').innerHTML='';g('w11b').innerHTML='<button id="w11r">Reset demo</button>';
  g('w11m').textContent=msg||"Each email is its own chore: open, read, decide, close. Try handling a few, then switch to the queue.";
 }else{
  g('w11mail').innerHTML='';
  t='<tr><th><input type="checkbox" id="w11a" aria-label="Select all"></th><th>Page</th>'+(view!="owner"?'<th>Owner</th>':'')+(view=="site"?'<th>Branch</th>':'')+'<th>Needs</th><th>Visits / mo</th><th>Weeks overdue</th><th>Priority</th></tr>';
  var top=r.length?Math.max.apply(null,r.map(pri)):1;
  r.forEach(function(x){var p=pri(x);t+='<tr class="'+(sel[x.id]?'pick':'')+'"><td><input type="checkbox" data-id="'+x.id+'" aria-label="Select '+x.t+'"'+(sel[x.id]?' checked':'')+'></td><td class="l">'+x.t+'</td>'+(view!="owner"?'<td>'+x.o+'</td>':'')+(view=="site"?'<td>'+x.b+'</td>':'')+'<td><span class="chip">'+x.i+'</span></td><td>'+x.v+'</td><td>'+x.w+'</td><td style="min-width:90px"><div class="track"><div class="fill" style="width:'+Math.round(p/top*100)+'%;background:'+(p>=40?'#e5534b':'#1f6feb')+'"></div></div></td></tr>';});
  if(!r.length)t+='<tr><td colspan="7" class="l"><span class="good">Nothing waiting. The queue is clear.</span></td></tr>';
  g('w11t').innerHTML=t;
  g('w11b').innerHTML='<span>'+n+' selected:</span><button data-a="Confirmed still correct"'+(n?'':' disabled')+'>Still correct</button><button data-a="Retired (archived, restorable)"'+(n?'':' disabled')+'>Retire</button><button data-a="Reassigned to the product owner"'+(n?'':' disabled')+'>Reassign</button><button id="w11r">Reset demo</button>';
  g('w11m').textContent=msg||(n?'':'Tick one or more pages, then choose a decision. Without a consolidated view, each one would be its own email.');
 }
 document.querySelectorAll('#w11h button[data-br]').forEach(function(b){b.onclick=function(){branch=b.dataset.br||null;sel={};draw();};});
 document.querySelectorAll('#w11 button[data-one]').forEach(function(b){b.onclick=function(){D=D.filter(function(x){return x.id!=+b.dataset.one;});done++;clicks+=4;msg="Handled one email (open, read, decide, close).";draw();};});
 document.querySelectorAll('#w11t input[data-id]').forEach(function(c){c.onchange=function(){sel[c.dataset.id]=c.checked;clicks++;msg="";draw();};});
 var A=g('w11a');if(A)A.onchange=function(){r.forEach(function(x){sel[x.id]=A.checked;});clicks++;msg="";draw();};
 document.querySelectorAll('#w11b button[data-a]').forEach(function(b){b.onclick=function(){var ids=Object.keys(sel).filter(function(k){return sel[k];}).map(Number);D=D.filter(function(x){return ids.indexOf(x.id)<0;});done+=ids.length;clicks++;msg=b.dataset.a+': '+ids.length+' page'+(ids.length>1?'s':'')+' in one step.';sel={};draw();};});
 var R=g('w11r');if(R)R.onclick=function(){init();draw();};
}
document.querySelectorAll('#w11 button[data-v]').forEach(function(b){b.onclick=function(){view=b.dataset.v;branch=null;sel={};msg="";document.querySelectorAll('#w11 button[data-v]').forEach(function(x){x.setAttribute('aria-pressed',x==b);});draw();};});
document.querySelectorAll('#w11 button[data-mode]').forEach(function(b){b.onclick=function(){mode=b.dataset.mode;sel={};msg="";document.querySelectorAll('#w11 button[data-mode]').forEach(function(x){x.setAttribute('aria-pressed',x==b);});draw();};});
g('w11s').onchange=draw;
init();draw();
})();
</script>

What to notice:

- **Separate emails are separate interruptions.** None says which matters most, so the easy response is to defer all of them.
- **The queue removes the guessing.** Switch the sort, and the order changes. Priority is not the same as age: a very old page nobody reads can wait.
- **The role changes the view.** The owner sees their own pages. The manager sees the team, with owners alongside. The product owner sees the whole site, and can click a branch to narrow it.
- **Bulk decisions are where the time comes back.** Compare the clicks counter after clearing the same pages one email at a time and in bulk.

## Design rules that keep it honest

- **Every number clicks through.** A count in a header must open the list behind it.
- **Bulk does not mean blind.** Show what will change before it happens, and make every action undoable.
- **Log decisions.** Who confirmed what, and when. That record is what makes "reviewed" mean something.
- **Keep one source of truth.** The queue reads from the same health data as the report. No second spreadsheet.
- **Keep it small.** If the queue is always long, the thresholds are wrong, or there are too many pages. Fix that, not the screen.

A good queue turns a pile of obligations into a short list of decisions.
