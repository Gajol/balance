---
layout: single
title: "Automation Flags, People Decide: From Content Health Report to Owner Action"
date: 2026-10-23 09:07:00 -0400
description: "A health report only helps if someone acts on it. See how flags, reminders, escalation and archiving move a stale page to its owner, and why people stay in charge."
excerpt: "A health report only helps if someone acts on it. See how flags, reminders, escalation and archiving move a stale page to its owner, and why people stay in charge."
theme: digital
author_profile: false
classes: full-width
tags: [product management, automation, content, governance, workflow]
---

A content health report tells you what is wrong. It does not fix anything. If the report goes to IT, IT ends up with a long list of pages it does not own and cannot judge.

The fix is simple to say: **send each problem to the person who owns the page, and let the system do the nagging.** This is the next step after [Content Health]({{ '/content-health-reporting/' | relative_url }}).

## The rule: automation flags, people decide

Machines are good at noticing and reminding. People are good at judging. So:

- **Automation does:** detects a stale page, creates a task, sends reminders, escalates, and archives when nobody answers.
- **People do:** decide whether a page is still right, needs changes, or should go.
- **Automation never:** rewrites content, deletes anything for good, or hides a decision.

## The loop

1. **Flag.** The health report finds a page past its review date, with no owner, or with failed searches.
2. **Route.** The flag becomes a task in the owner's *My content* view. A page with no owner goes to the product owner.
3. **Remind.** The owner gets reminders with a clear due date.
4. **Escalate.** If nothing happens, the owner's manager is told, then the product owner.
5. **Resolve.** The owner picks one of three answers: *still correct*, *update it*, or *retire it*.
6. **Archive.** If nobody answers by the end of the grace period, the page is archived, not deleted, and it can be restored.
7. **Report.** The result feeds back into the health report, and the loop closes.

<style>
.wx{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:14px;margin:1.2em 0;font-size:.95em}
.wx button,.wx select{font:inherit;padding:4px 10px;border:1px solid rgba(128,128,128,.55);border-radius:6px;background:transparent;color:inherit;cursor:pointer}
.wx button[aria-pressed=true],.wx button.on{background:#1f6feb;color:#fff;border-color:#1f6feb}
.wx button:disabled{opacity:.45;cursor:default}
.wx .row{display:flex;flex-wrap:wrap;gap:8px 12px;margin:8px 0;align-items:center}
.wx .card{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:10px;margin:6px 0}
.wx .note{opacity:.85;font-size:.9em}
.wx .good{color:#2da44e;font-weight:600}.wx .bad{color:#e5534b;font-weight:600}
.wx .track{background:rgba(128,128,128,.25);border-radius:6px;height:14px;overflow:hidden}
.wx .fill{height:14px;background:#1f6feb;border-radius:6px;transition:width .3s}
.wx table{border-collapse:collapse;width:100%}
.wx td,.wx th{border:1px solid rgba(128,128,128,.35);padding:5px 8px;text-align:center}
.wx .face{font-size:2.4em;line-height:1}
.wx .wc{display:grid;grid-template-columns:minmax(0,300px) minmax(0,1fr);gap:16px;align-items:start}
@media (max-width:820px){.wx .wc{grid-template-columns:1fr}}
.wx .mm{display:flex;gap:10px;align-items:center;border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:8px;margin:6px 0}
.wx .mm .face{font-size:2.2em}
.wx .tag{display:inline-block;margin-left:6px;padding:0 7px;border-radius:9px;font-size:.78em;border:1px solid #e5534b;color:#e5534b}
.wx .tag.ok{border-color:#2da44e;color:#2da44e}
.wx .tag.am{border-color:#d98e04;color:#d98e04}
.wx .sr{border:1px solid rgba(128,128,128,.35);border-radius:6px;padding:7px 10px;margin:4px 0;transition:all .3s}
.wx .sr.me{border:2px solid #1f6feb;background:rgba(31,111,235,.1)}
.wx .tlw{overflow-x:auto;padding-bottom:4px}
.wx .tl{display:grid;grid-template-columns:repeat(17,minmax(26px,1fr));gap:2px;min-width:480px;margin-top:8px}
.wx .tl .c{text-align:center;border-radius:6px;padding:2px 0;opacity:.38;transition:opacity .25s}
.wx .tl .c.on{opacity:1}
.wx .tl .c.cur{outline:2px solid #1f6feb;background:rgba(31,111,235,.12)}
.wx .tl .n{font-size:.7em;opacity:.8}
.wx .tl .ic{font-size:1.25em;line-height:1.5em;height:1.5em;cursor:default}
.wx .rib{height:12px;border-radius:3px;margin-top:2px}
.wx .ri{font-size:.95em;line-height:1.3em;height:1.3em}
.wx .legend{display:flex;flex-wrap:wrap;gap:2px 14px;font-size:.82em;opacity:.9;margin-top:6px}
.wx .tiles{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:8px;margin-top:10px}
.wx .tile{border:2px solid rgba(128,128,128,.4);border-radius:10px;padding:8px;text-align:center;transition:all .25s}
.wx .tile .ti{font-size:1.8em;line-height:1.2}
.wx .tile .tv{font-weight:700}
.wx .tile .tl2{font-size:.76em;text-transform:uppercase;letter-spacing:.06em;opacity:.75}
.wx .tile.g{border-color:#2da44e;background:rgba(45,164,78,.1)}
.wx .tile.y{border-color:#d98e04;background:rgba(217,142,4,.1)}
.wx .tile.r{border-color:#e5534b;background:rgba(229,83,75,.1)}
.wx .tile.x{border-color:rgba(128,128,128,.6);background:rgba(128,128,128,.12)}
.wx .dots{display:grid;grid-template-columns:repeat(10,1fr);gap:4px;max-width:340px}
.wx .dots i{display:block;aspect-ratio:1;border-radius:50%;background:#e5534b;transition:background .3s}
.wx .dots i.a{background:#d98e04}.wx .dots i.g{background:#2da44e}.wx .dots i.x{background:rgba(128,128,128,.5)}
</style>

## Try it: one stale page, week by week

Follow a single stale page. Choose how reminders are sent, how the owner behaves, and how long the grace period is. Then drag the week slider, or press **Play**. On the right, the page moves in the search results, a timeline of icons shows what happened and when, and four tiles show the **impact** on the page. On the left, three people react. All numbers are illustrative.

<div class="wx" markdown="0" id="w10">
<div class="row">
<label>Reminders: <select id="w10s"><option value="0">Light (2 reminders)</option><option value="1" selected>Standard (4 reminders)</option><option value="2">Firm (weekly)</option></select></label>
<label>The owner: <select id="w10o"><option value="0">Responds promptly</option><option value="1" selected>Ignores the reminders</option><option value="2">Has left the organization</option></select></label>
<label>Grace period: <input type="range" id="w10g" min="4" max="16" value="8"> <strong id="w10gv"></strong> weeks</label>
</div>
<div class="row"><button id="w10p">&#9654; Play</button><label>Week: <input type="range" id="w10w" min="0" max="16" value="0" style="width:200px"> <strong id="w10wv">0</strong></label></div>
<div class="wc">
<div>
<div class="mm"><span class="face" id="w10fo" aria-hidden="true"></span><span><span class="note">The page owner</span><br><strong id="w10lo"></strong><br><span class="note" id="w10co"></span></span></div>
<div class="mm"><span class="face" id="w10fm" aria-hidden="true"></span><span><span class="note">The owner&rsquo;s manager</span><br><strong id="w10lm"></strong><br><span class="note" id="w10cm"></span></span></div>
<div class="mm"><span class="face" id="w10fr" aria-hidden="true"></span><span><span class="note">The reader</span><br><strong id="w10lr"></strong><br><span class="note" id="w10cr"></span></span></div>
</div>
<div>
<div class="note">Staff search for: <strong>leave policy</strong></div>
<div id="w10sr"></div>
<div class="tlw"><div class="tl" id="w10tl"></div><div class="tl" id="w10rb" aria-hidden="true"></div></div>
<div class="legend"><span>&#128681; Flagged</span><span>&#128276; Reminder: owner</span><span>&#128084; Escalated: manager</span><span>&#129517; Escalated: product owner</span><span>&#8618;&#65039; Rerouted</span><span>&#9989; Resolved</span><span>&#128230; Archived</span></div>
<div class="tiles" id="w10im"></div>
<div class="card" id="w10cap" aria-live="polite" style="margin-top:10px"></div>
<div class="card" id="w10r"></div>
</div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var S=[[[2,"owner"],[6,"manager"]],[[1,"owner"],[3,"owner"],[5,"manager"],[8,"product owner"]],[[1,"owner"],[2,"owner"],[3,"owner"],[4,"manager"],[5,"manager"],[6,"manager"],[7,"product owner"],[8,"product owner"]]];
var IM={owner:"No change yet. The page keeps its <b>Needs review</b> label.",manager:"<b>Ranked lower in search.</b> The manager sees it in their team view.",pm:"<b>Archive candidate.</b> Dropped from featured lists and menus.",bounce:"Owner record shown as out of date. Task rerouted to the product owner.",ok:"<span class=\"good\">Stale label removed. Search rank restored. Review date reset.</span>",arch:"<span class=\"bad\">Removed from search and menus.</span> Kept in the archive. Visitors see a notice with a restore link."};
var M,timer=null;
function build(){
 var sc=S[+g('w10s').value].slice(),ow=+g('w10o').value,gr=+g('w10g').value;
 sc.sort(function(a,b){return a[0]-b[0];});
 var ev=[{w:0,t:"Flagged: page not reviewed in 12 months. Task created in the owner’s My content view.",i:"<b>Marked stale.</b> Shows a <b>Needs review</b> label and ranks slightly lower in search.",k:"flag"}],done=null,res=null;
 for(var i=0;i<sc.length&&done===null;i++){
  var w=sc[i][0],to=sc[i][1];
  if(w>=gr)break;
  if(ow==2&&to=="owner"){ev.push({w:w,t:"Reminder to the owner bounced: the owner has left. Page moved to the product owner.",i:IM.bounce,k:"bounce"});
   if(w+1<gr){ev.push({w:w+1,t:"Product owner reviews the page and chooses: update it.",i:IM.ok,k:"ok"});done=w+1;res="reassigned";}else break;
  }else{
   ev.push({w:w,t:"Reminder sent to the "+to+".",i:to=="owner"?IM.owner:to=="manager"?IM.manager:IM.pm,k:to=="owner"?"ro":to=="manager"?"rm":"rp"});
   if(ow==0&&to=="owner"){ev.push({w:w+1,t:"Owner reviews the page and confirms it is still correct.",i:IM.ok,k:"ok"});done=w+1;res="current";}
  }
 }
 if(done===null){ev.push({w:gr,t:"Grace period ended with no answer. Page archived (not deleted).",i:IM.arch,k:"arch"});res="archived";}
 ev.sort(function(a,b){return a.w-b.w;});
 function first(k){var r=null;ev.forEach(function(e){if(e.k==k&&(r===null||e.w<r))r=e.w;});return r;}
 M={ev:ev,done:done,res:res,gr:gr,ow:ow,ro:first("ro"),rm:first("rm"),rp:first("rp"),bn:first("bounce"),last:ev[ev.length-1].w};
}
function stage(w){
 if(M.done!==null&&w>=M.done)return "current";
 if(M.res=="archived"&&w>=M.gr)return "archived";
 if(M.rp!==null&&w>=M.rp)return "candidate";
 if(M.rm!==null&&w>=M.rm)return "demoted";
 return "stale";
}
function ownerMood(w,st){
 if(M.ow==2)return ["&#128566;","Has left","Nobody is there to read the reminders."];
 if(st=="current")return ["&#128524;","Relieved","A few minutes, and it is done."];
 if(st=="archived")return ["&#128543;","Surprised","Where did my page go? I should have answered."];
 if(M.rm!==null&&w>=M.rm)return ["&#128556;","Pressured","My manager has been told now."];
 if(M.ro!==null&&w>=M.ro)return M.ow==0?["&#128578;","Nudged","A clear reminder. I will do it today."]:["&#128566;","Ignoring it","Another email. Later."];
 return ["&#128528;","Unaware","Nothing has reached me yet."];
}
function mgrMood(w,st){
 if(M.res=="archived"&&w>=M.gr)return ["&#128528;","Informed","A page was archived. It can be restored."];
 if(M.rm!==null&&w>=M.rm&&st!="current")return ["&#128533;","Concerned","A page in my team is stale and unanswered."];
 if(st=="current"&&w>=M.done)return ["&#128578;","Not needed","The owner handled it before it reached me."];
 return ["&#128578;","Not involved yet","Nothing to do. That is how it should be."];
}
function readerMood(st){
 return st=="current"?["&#128524;","Trusts it","Right page, clearly reviewed."]:st=="stale"?["&#128578;","Notices the label","It says Needs review. I will take care."]:st=="demoted"?["&#128528;","Finds it lower","I scroll past it and double-check."]:st=="candidate"?["&#128533;","Skips it","This looks abandoned."]:["&#128578;","Sees a clean result","Only current pages. And a restore link if I need it."];
}
function draw(){
 var w=+g('w10w').value;g('w10wv').textContent=w;g('w10gv').textContent=M.gr;
 var st=stage(w),o=ownerMood(w,st),m=mgrMood(w,st),r=readerMood(st);
 g('w10fo').innerHTML=o[0];g('w10lo').textContent=o[1];g('w10co').textContent='“'+o[2]+'”';
 g('w10fm').innerHTML=m[0];g('w10lm').textContent=m[1];g('w10cm').textContent='“'+m[2]+'”';
 g('w10fr').innerHTML=r[0];g('w10lr').textContent=r[1];g('w10cr').textContent='“'+r[2]+'”';
 var O=[["Leave: frequently asked questions"],["Leave request form"],["Leave calendar"]],our={t:"Leave policy"};
 var tag=st=="stale"?'<span class="tag">Needs review</span>':st=="demoted"?'<span class="tag">May be out of date</span>':st=="candidate"?'<span class="tag am">Archive candidate</span>':st=="current"?'<span class="tag ok">Reviewed</span>':'';
 var pos=st=="current"?0:st=="stale"?1:st=="demoted"?2:st=="candidate"?3:-1,rows=[],i;
 for(i=0;i<3;i++)rows.push('<div class="sr">'+O[i][0]+'</div>');
 if(pos>=0)rows.splice(pos,0,'<div class="sr me"><strong>'+our.t+'</strong>'+tag+'</div>');
 var h=rows.join('');
 if(st=="archived")h+='<div class="note" style="margin-top:4px">&ldquo;Leave policy&rdquo; is no longer in search. It is in the archive, with a restore link.</div>';
 g('w10sr').innerHTML=h;
 var IC={flag:"&#128681;",ro:"&#128276;",rm:"&#128084;",rp:"&#129517;",bounce:"&#8618;&#65039;",ok:"&#9989;",arch:"&#128230;"};
 var byW={};M.ev.forEach(function(e){byW[e.w]=e;});
 var SC={stale:"#f0b429",demoted:"#f08c00",candidate:"#e5534b",current:"#2da44e",archived:"#8a8f98"},SI={stale:"&#127991;&#65039;",demoted:"&#128201;",candidate:"&#9888;&#65039;",current:"&#9989;",archived:"&#128230;"};
 var tl='',rb='',prev='',k;
 for(k=0;k<=16;k++){var e=byW[k],sk=stage(k),on=k<=w,cl='c'+(on?' on':'')+(k==w?' cur':'');
  tl+='<div class="'+cl+'"><div class="n">'+k+'</div><div class="ic" title="'+(e?'Week '+k+': '+e.t.replace(/"/g,''):'')+'">'+(e?IC[e.k]:'')+'</div></div>';
  rb+='<div class="'+cl+'"><div class="rib" style="background:'+SC[sk]+'"></div><div class="ri">'+(sk!=prev?SI[sk]:'')+'</div></div>';prev=sk;}
 g('w10tl').innerHTML=tl;g('w10rb').innerHTML=rb;
 var lab={stale:["&#127991;&#65039;","Needs review","r"],demoted:["&#127991;&#65039;","May be out of date","r"],candidate:["&#127991;&#65039;","Archive candidate","r"],current:["&#127991;&#65039;","Reviewed","g"],archived:["&#127991;&#65039;","None","x"]}[st];
 var rk={current:["#1","g"],stale:["#2","y"],demoted:["#3","y"],candidate:["#4","r"],archived:["Out","x"]}[st];
 var mn={current:["Listed","g"],stale:["Listed","g"],demoted:["Listed","g"],candidate:["Dropped","r"],archived:["Removed","x"]}[st];
 var ar={current:["No","g"],stale:["No","g"],demoted:["No","g"],candidate:["Next","y"],archived:["Yes, restorable","x"]}[st];
 g('w10im').innerHTML='<div class="tile '+lab[2]+'"><div class="ti">'+lab[0]+'</div><div class="tv">'+lab[1]+'</div><div class="tl2">Label on page</div></div><div class="tile '+rk[1]+'"><div class="ti">&#128269;</div><div class="tv">'+rk[0]+'</div><div class="tl2">Search position</div></div><div class="tile '+mn[1]+'"><div class="ti">&#129517;</div><div class="tv">'+mn[0]+'</div><div class="tl2">Menus and featured</div></div><div class="tile '+ar[1]+'"><div class="ti">&#128230;</div><div class="tv">'+ar[0]+'</div><div class="tl2">Archived</div></div>';
 var lastE=null;M.ev.forEach(function(e){if(e.w<=w)lastE=e;});
 g('w10cap').innerHTML=lastE?'<span style="font-size:1.4em" aria-hidden="true">'+IC[lastE.k]+'</span> <strong>Week '+lastE.w+':</strong> '+lastE.t:'';
 var msg={current:'<span class="good">Resolved by the owner in week '+M.done+'.</span> The page stays live and its review date resets. Automation did the chasing. A person made the call.',reassigned:'<span class="good">Resolved by the product owner in week '+M.done+'.</span> Because the owner had left, the system rerouted the task instead of letting it sit. Also check why the owner field was out of date.',archived:'<span class="bad">No one answered.</span> The page was archived in week '+M.gr+' and can be restored with one click. A longer grace period is kinder to busy owners. A shorter one keeps the site cleaner.'};
 g('w10r').innerHTML=w>=M.last?msg[M.res]:'<span class="note">Keep going. Drag the week slider or press Play to see what happens next.</span>';
}
function recalc(){build();draw();}
function stop(){if(timer){clearInterval(timer);timer=null;}g('w10p').innerHTML='&#9654; Play';}
g('w10p').onclick=function(){if(timer){stop();return;}if(+g('w10w').value>=16)g('w10w').value=0;g('w10p').innerHTML='&#10074;&#10074; Pause';timer=setInterval(function(){var v=+g('w10w').value;if(v>=16){stop();return;}g('w10w').value=v+1;draw();},700);};
['w10s','w10o','w10g'].forEach(function(i){g(i).oninput=g(i).onchange=function(){stop();g('w10w').value=0;recalc();};});
g('w10w').oninput=function(){stop();draw();};
build();draw();
})();
</script>

Read the right-hand side as the price of doing nothing. The page is labelled, ranked lower in search, dropped from featured lists, and finally archived. That is the nudge. Owners act because silence has a visible effect on their own pages.

What to notice:

- **Impact grows in steps.** A label first, then lower rank, then archive candidate, then archive. Each step is gentle and reversible.
- **The three people feel different things.** The owner goes from unaware to nudged to relieved, or to pressured and surprised. The manager is only involved when needed. The reader moves from trusting to wary.
- **A departed owner needs a rule.** Without rerouting, the page sits flagged forever.
- **The grace period is a policy choice.** It trades kindness to owners against a clean site.

## Across the whole site: 100 stale pages

One page is a story. A site is a number. Here are 100 stale pages, each with an owner who behaves differently: most respond, some are slow, some ignore reminders, and some have left. Compare doing nothing with automation over twelve weeks. This is a made-up model to show the shape, not a prediction.

<div class="wx" markdown="0" id="w13">
<div class="row"><button data-m="none" aria-pressed="true">No automation</button><button data-m="auto" aria-pressed="false">With automation</button><button id="w13p">&#9654; Play</button><label>Week: <input type="range" id="w13w" min="0" max="12" value="0" style="width:180px"> <strong id="w13wv">0</strong></label></div>
<div class="wc">
<div class="dots" id="w13d" role="img" aria-label="100 pages coloured by status"></div>
<div>
<div class="row"><span><span class="bad">&#9679;</span> Stale and open: <strong id="w13a"></strong></span><span><span style="color:#d98e04">&#9679;</span> Escalated: <strong id="w13b"></strong></span></div>
<div class="row"><span><span class="good">&#9679;</span> Resolved by a person: <strong id="w13c"></strong></span><span><span style="opacity:.6">&#9679;</span> Archived (restorable): <strong id="w13e"></strong></span></div>
<div class="card" id="w13s" aria-live="polite"></div>
</div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
var seed=7;function rnd(){seed=(seed+0x6D2B79F5)|0;var t=Math.imul(seed^(seed>>>15),1|seed);t=(t+Math.imul(t^(t>>>7),61|t))^t;return((t^(t>>>14))>>>0)/4294967296;}
var P=[],i;
for(i=0;i<100;i++){var r=rnd(),ty=r<.55?"r":r<.75?"s":r<.9?"i":"l",x=rnd(),y=rnd(),z=rnd();
 var o={ty:ty,self:x<.08?3+Math.floor(y*10):99,amber:99,res:99,arch:99};
 if(ty=="r"){o.res=1+Math.floor(y*3);}
 else if(ty=="s"){o.amber=3;o.res=5+Math.floor(y*4);}
 else if(ty=="i"){o.amber=3;o.arch=8;}
 else{o.amber=1;if(z<.8)o.res=2+Math.floor(y*4);else o.arch=8;}
 P.push(o);}
var mode="none",timer=null;
function stateOf(p,t){
 if(mode=="none")return t>=p.self?"g":"";
 if(t>=p.res)return "g";if(t>=p.arch)return "x";if(t>=p.amber)return "a";return "";
}
function draw(){
 var t=+g('w13w').value;g('w13wv').textContent=t;
 var c={"":0,a:0,g:0,x:0},h='';
 P.forEach(function(p){var s=stateOf(p,t);c[s]++;h+='<i class="'+s+'"></i>';});
 g('w13d').innerHTML=h;g('w13a').textContent=c[""];g('w13b').textContent=c.a;g('w13c').textContent=c.g;g('w13e').textContent=c.x;
 var m;
 if(mode=="none")m='<span class="bad">'+c[""]+' of 100 pages are still stale at week '+t+'.</span> Nothing is flagged, so nothing changes. A few get fixed by chance.';
 else m=t<12?'<span class="note">Press Play, or drag the week slider.</span>':'<span class="good">By week 12, '+c.g+' pages were resolved by a person, '+c.x+' were archived safely, and '+((c[""]+c.a)?'only '+(c[""]+c.a)+' are':'none are')+' still open.</span> Most work was done by the owners themselves. Automation did the chasing.';
 if(mode=="auto"&&t<12)m='<span class="note">Week '+t+': '+c.g+' resolved, '+c.a+' escalated, '+c.x+' archived. Press Play to keep going.</span>';
 g('w13s').innerHTML=m;
}
function stop(){if(timer){clearInterval(timer);timer=null;}g('w13p').innerHTML='&#9654; Play';}
g('w13p').onclick=function(){if(timer){stop();return;}if(+g('w13w').value>=12)g('w13w').value=0;g('w13p').innerHTML='&#10074;&#10074; Pause';timer=setInterval(function(){var v=+g('w13w').value;if(v>=12){stop();return;}g('w13w').value=v+1;draw();},600);};
g('w13w').oninput=function(){stop();draw();};
document.querySelectorAll('#w13 button[data-m]').forEach(function(b){b.onclick=function(){stop();mode=b.dataset.m;g('w13w').value=0;document.querySelectorAll('#w13 button[data-m]').forEach(function(x){x.setAttribute('aria-pressed',x==b);});draw();};});
draw();
})();
</script>

What to notice:

- **Most owners respond to a simple nudge.** The first reminders do most of the work.
- **Escalation catches the slow ones.** The manager sees what is stuck without chasing every page.
- **Archiving handles the rest safely.** Nothing is lost, and it can all be restored.

## Where the flag goes

Different flags go to different people. This is the part that makes the report useful.

| Flag from the health report | Goes to | Typical choices |
|---|---|---|
| Stale (past review date) | Page owner | Still correct, update, retire |
| No owner | Product owner | Assign an owner, or retire |
| Orphan (nothing links to it) | Page owner and editor | Link it from a hub, or retire |
| Failed searches in an area | Product owner and editor | Add content, add a synonym, improve a title |
| Broken accessibility check | Editor | Fix before or after publishing |

## Many pages, one queue

Owners often look after dozens of pages. Give them one ranked queue with bulk actions, and give managers and the product owner roll-ups of the same data. See [One Queue]({{ '/one-queue-consolidated-views/' | relative_url }}).

## Nudge or nag?

Reminders work, up to a point. Too few and owners never notice. Too many and they filter the emails and stop listening. Drag the slider to find the sweet spot. Illustrative model.

<div class="wx" markdown="0" id="w14">
<div class="row"><label>Reminders per month: <input type="range" id="w14f" min="0" max="8" value="2" style="width:220px"> <strong id="w14v"></strong></label></div>
<div class="wc">
<div class="card"><div class="row" style="margin:0"><span class="face" id="w14e" aria-hidden="true"></span><span><span class="note">How the owner feels</span><br><strong id="w14l"></strong></span></div><div id="w14q" style="font-style:italic;margin-top:6px"></div></div>
<div>
<div class="row" style="justify-content:space-between;margin:0"><span>Pages reviewed on time</span><strong id="w14rv"></strong></div><div class="track"><div class="fill" id="w14r" style="background:#2da44e"></div></div>
<div class="row" style="justify-content:space-between;margin:8px 0 0"><span>Owner annoyance</span><strong id="w14av"></strong></div><div class="track"><div class="fill" id="w14a" style="background:#e5534b"></div></div>
<div class="note" id="w14n" style="margin-top:8px" aria-live="polite"></div>
</div>
</div>
</div>
<script>
(function(){
function g(i){return document.getElementById(i);}
function draw(){
 var f=+g('w14f').value;g('w14v').textContent=f;
 var resp=f==0?0.15:Math.min(0.85,0.15+0.75*(1-Math.exp(-1.1*f)));
 if(f>3)resp*=1-(f-3)*0.08;
 var ann=Math.min(1,Math.pow(f/8,1.7)*1.1);
 var R=Math.round(resp*100),A=Math.round(ann*100);
 g('w14r').style.width=R+'%';g('w14a').style.width=A+'%';g('w14rv').textContent=R+'%';g('w14av').textContent=A+'%';
 var m;
 if(f==0)m=["&#128566;","Never reminded","I did not know there was a problem.","No reminders means no action. This is the quiet failure."];
 else if(f==1)m=["&#128578;","Barely noticed","One email a month. Easy to miss.","Too gentle. Some owners never act."];
 else if(f<=3)m=["&#128524;","Helpful nudge","A clear reminder, and I know what to do.","Sweet spot: two or three reminders a month, plus one escalation."];
 else if(f<=5)m=["&#128533;","Starting to tune out","That is a lot of email about one page.","More reminders are not buying more answers."];
 else m=["&#128544;","Nagged","I filter these emails now.","Past this point, response falls and annoyance climbs. Send a weekly digest instead."];
 g('w14e').innerHTML=m[0];g('w14l').textContent=m[1];g('w14q').textContent='“'+m[2]+'”';g('w14n').textContent=m[3];
}
g('w14f').oninput=draw;draw();
})();
</script>

## Keep it humane

- **One digest, not many emails.** Send a weekly summary of what is due, not a message per page.
- **Make the answer one click.** "Still correct" should take seconds.
- **Escalate up, never sideways.** The manager is told once, clearly.
- **Log everything.** Who was told, who answered, when. It protects owners and the product team alike.
- **Never delete silently.** Archive, notify, and allow restore.

## Guardrails you can test

The rule is "automation flags, people decide". Try asking the automation to cross the line.

<div class="wx" markdown="0" id="w15">
<div class="row"><strong>Ask the automation to:</strong>
<button data-a="rewrite">Rewrite this page</button>
<button data-a="delete">Delete this page forever</button>
<button data-a="hide">Quietly hide this page</button>
<button data-a="remind">Remind the owner</button>
<button data-a="archive">Archive after the grace period</button>
<button data-a="task">Create a task for a person</button>
</div>
<div class="card" id="w15r" aria-live="polite"><span class="note">Pick an action.</span></div>
</div>
<script>
(function(){
var X={rewrite:[0,"Blocked.","Automation never changes what a page says. Only a person can decide it is correct."],delete:[0,"Blocked.","Nothing is deleted for good. Archive keeps the page, with a restore link."],hide:[0,"Blocked.","Silent changes break trust. Every change is visible, logged and reversible."],remind:[1,"Allowed.","Reminders are what automation is for. Keep them few and clear."],archive:[1,"Allowed, with conditions.","Only after the grace period, with a notice to the owner, a restore link and a log entry."],task:[1,"Allowed.","This is the point: the right person sees the right problem, and a person decides."]};
document.querySelectorAll('#w15 button[data-a]').forEach(function(b){b.onclick=function(){var x=X[b.dataset.a];document.getElementById('w15r').innerHTML='<span style="font-size:1.6em" aria-hidden="true">'+(x[0]?'&#9989;':'&#128274;')+'</span> <strong class="'+(x[0]?'good':'bad')+'">'+x[1]+'</strong> '+x[2];};});
})();
</script>

Automation is not about taking people out of the loop. It is about making sure the right person sees the right problem at the right time, so the people-only part, the decision, actually happens.
