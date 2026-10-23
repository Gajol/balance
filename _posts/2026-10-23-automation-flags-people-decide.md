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

## Try it

Pick a reminder style, an owner response and a grace period. The timeline shows what happens to one stale page.

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
<div class="wx" markdown="0" id="w10">
<div class="row">
<label>Reminders: <select id="w10s"><option value="0">Light (2 reminders)</option><option value="1" selected>Standard (4 reminders)</option><option value="2">Firm (weekly)</option></select></label>
<label>The owner: <select id="w10o"><option value="0">Responds promptly</option><option value="1" selected>Ignores the reminders</option><option value="2">Has left the organization</option></select></label>
</div>
<label>Grace period before archiving: <input type="range" id="w10g" min="4" max="16" value="8"> <strong id="w10gv"></strong> weeks</label>
<div id="w10t"></div>
<div class="card" id="w10r" aria-live="polite"></div>
</div>
<script>
(function(){
var S=[[[2,"owner"],[6,"manager"]],[[1,"owner"],[3,"owner"],[5,"manager"],[8,"product owner"]],[[1,"owner"],[2,"owner"],[3,"owner"],[4,"manager"],[5,"manager"],[6,"manager"],[7,"product owner"],[8,"product owner"]]];
function g(i){return document.getElementById(i);}
function draw(){
var sc=S[+g('w10s').value],ow=+g('w10o').value,gr=+g('w10g').value;
g('w10gv').textContent=gr;
var IM={owner:"No change yet. The page keeps its <b>Needs review</b> label.",manager:"<b>Ranked lower in search.</b> The manager sees it in their team view.",pm:"<b>Archive candidate.</b> Dropped from featured lists and menus.",bounce:"Owner record shown as out of date. Task rerouted to the product owner.",ok:"<span class=\"good\">Stale label removed. Search rank restored. Review date reset.</span>",arch:"<span class=\"bad\">Removed from search and menus.</span> Kept in the archive. Visitors see a notice with a restore link."};
var ev=[[0,"Flagged: page not reviewed in 12 months. Task created in the owner’s My content view.","n","<b>Marked stale.</b> Shows a <b>Needs review</b> label and ranks slightly lower in search."]],done=null,res;
sc.sort(function(a,b){return a[0]-b[0];});
for(var i=0;i<sc.length&&done===null;i++){
 var w=sc[i][0],to=sc[i][1];
 if(w>=gr)break;
 if(ow==2&&to=="owner"){ev.push([w,"Reminder to the owner bounced: the owner has left. Page moved to the product owner.","w",IM.bounce]);
   if(w+1<gr){ev.push([w+1,"Product owner reviews the page and chooses: update it.","g",IM.ok]);done=w+1;res="reassigned";}else{break;}
 }else{
  ev.push([w,"Reminder sent to the "+to+".","n",to=="owner"?IM.owner:to=="manager"?IM.manager:IM.pm]);
  if(ow==0&&to=="owner"){ev.push([w+1,"Owner reviews the page and confirms it is still correct.","g",IM.ok]);done=w+1;res="current";}
 }
}
if(done===null){ev.push([gr,"Grace period ended with no answer. Page archived (not deleted).","w",IM.arch]);res="archived";}
ev.sort(function(a,b){return a[0]-b[0];});
var h='<table><tr><th>Week</th><th>What happens</th><th>Impact on the page</th></tr>';
ev.forEach(function(e){h+='<tr><td>'+e[0]+'</td><td style="text-align:left">'+e[1]+'</td><td style="text-align:left">'+e[3]+'</td></tr>';});
g('w10t').innerHTML=h+'</table>';
var m={current:'<span class="good">Resolved by the owner in week '+done+'.</span> The page stays live and its review date resets. Automation did the chasing. A person made the call.',reassigned:'<span class="good">Resolved by the product owner in week '+done+'.</span> Because the owner had left, the system rerouted the task instead of letting it sit. Also worth checking: why was the owner field out of date?',archived:'<span class="bad">No one answered.</span> The page was archived in week '+gr+' and can be restored with one click. This is the safe default. A longer grace period is kinder to busy owners. A shorter one keeps the site cleaner.'};
g('w10r').innerHTML=m[res];
}
['w10s','w10o','w10g'].forEach(function(i){g(i).oninput=draw;g(i).onchange=draw;});
draw();
})();
</script>

Read the **Impact** column as the price of doing nothing. The page does not just wait: it is labelled, ranked lower in search, dropped from featured lists, and finally archived. That is the nudge. Owners act because staying silent has a visible effect on their own pages.

What to notice:

- **Impact grows in steps.** A label first, then lower search rank, then archive candidate, then archive. Each step is gentle and reversible.
- **Light reminders and a busy owner end in an archive.** That is the system working, but it is a sign to ask whether the owner had a fair chance.
- **A departed owner needs a rule.** Without rerouting, the page sits flagged forever.
- **The grace period is a policy choice.** It trades kindness to owners against a clean site.

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

## Keep it humane

- **One digest, not many emails.** Send a weekly summary of what is due, not a message per page.
- **Make the answer one click.** "Still correct" should take seconds.
- **Escalate up, never sideways.** The manager is told once, clearly.
- **Log everything.** Who was told, who answered, when. It protects owners and the product team alike.
- **Never delete silently.** Archive, notify, and allow restore.

Automation is not about taking people out of the loop. It is about making sure the right person sees the right problem at the right time, so the people-only part, the decision, actually happens.
