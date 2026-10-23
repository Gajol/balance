---
layout: single
title: "Adding AI to a Web Platform: Where It Helps, Where People Decide"
date: 2026-10-23 12:00:00 -0400
description: "Two ways to bring AI to a website or intranet, one shared integration layer, four uses ranked by risk, and the guardrails that keep answers trusted."
excerpt: "Two ways to bring AI to a website or intranet, one shared integration layer, four uses ranked by risk, and the guardrails that keep answers trusted."
theme: digital
author_profile: false
classes: full-width
tags: [product management, AI, architecture, governance, search]
---

Staff and visitors already ask AI tools questions. The real question for a web platform is not *whether* AI touches your content. It is **how, under whose rules, and who is still responsible for the answer.**

This article keeps it general. It works for a public site or an internal one, on any content system. It builds on [Automation Flags, People Decide]({{ '/automation-flags-people-decide/' | relative_url }}) and [Your Search Box Is Only as Good as Your Content Owners]({{ '/search-needs-content-owners/' | relative_url }}). The same rule applies: **the machine finds and drafts, people decide.**

## Why bother?

Four everyday problems AI can help with:

- People spend time searching for approved content across several pages.
- The same questions get asked of the same people, again and again.
- Editors repeat the same summaries, tags and plain-language checks.
- Staff look up status in more than one system.

These are working assumptions. Check them with your own users before you build anything.

## Five words to know

- **Retrieval (RAG):** the AI first finds approved content, then writes an answer with links back to it.
- **Tools:** defined actions the AI may call, such as "search the site". You decide what each tool may do.
- **MCP (Model Context Protocol):** an open standard that connects AI tools to data and actions in one common way.
- **Gateway:** the checkpoint that knows who is asking and logs each step.
- **Permissions:** the limits on what that person is allowed to see.

## Two front doors, one integration layer

There are two ways in. Both can work.

- **Pattern 1: the AI chat calls your platform.** People keep the AI tool they already use. Your site is a tool it can call. You build no chat screen, but you depend on that AI tool supporting your connector.
- **Pattern 2: a chat box on your own page.** Help appears where people already read. You control the look, logs and behaviour. You also build and run more.

**The useful idea: build the integration layer once, then choose the front doors.** Both patterns call the same tool server, the same gateway and the same permission checks. Start with the cheaper door. Add the second only when people show they want it.

### The picture

Pick a front door to follow its path. Everything inside the dashed box is yours to control.

<style>
.fd{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:12px;margin:1.2em 0}
.fd .row{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:8px;align-items:center}
.fd button{font:inherit;padding:4px 10px;border:1px solid rgba(128,128,128,.55);border-radius:6px;background:transparent;color:inherit;cursor:pointer}
.fd button[aria-pressed=true]{background:#1f6feb;color:#fff;border-color:#1f6feb}
.fd svg{width:100%;height:auto;display:block}
.fd .bx{fill:rgba(128,128,128,.08);stroke:rgba(128,128,128,.6);stroke-width:1.5}
.fd .bd{fill:none;stroke:rgba(128,128,128,.7);stroke-width:1.5;stroke-dasharray:6 4}
.fd text{fill:currentColor;font-size:13px;font-family:inherit}
.fd .t1{font-weight:700;font-size:14px}.fd .t2{font-size:11.5px;opacity:.8}
.fd .ln{stroke:rgba(128,128,128,.6);stroke-width:2;fill:none;marker-end:url(#fda)}
.fd .shared{stroke:#7d4cdb;opacity:.9}
.fd [data-p]{opacity:.28;transition:opacity .25s}
.fd.d1 [data-p~="1"],.fd.d2 [data-p~="2"],.fd.d0 [data-p]{opacity:1}
.fd .a1 .bx{stroke:#1f6feb}.fd .a2 .bx{stroke:#d98e04}.fd .sh .bx{stroke:#7d4cdb;fill:rgba(125,76,219,.12)}
.fd.d1 .ln.p1,.fd.d0 .ln.p1{stroke:#1f6feb}.fd.d2 .ln.p2,.fd.d0 .ln.p2{stroke:#d98e04}
.fd #fdn{margin:.4em 0 0;font-size:.92em}
</style>
<div class="fd d0" id="fd" markdown="0">
<div class="row" role="group" aria-label="Front door"><button data-d="0" aria-pressed="true">Show both</button><button data-d="1" aria-pressed="false">Door 1: AI chat tool</button><button data-d="2" aria-pressed="false">Door 2: chat box on a page</button></div>
<svg viewBox="0 0 900 420" role="img" aria-label="Two front doors, a shared gateway and tool server, then search and content">
<defs><marker id="fda" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0 0L10 5L0 10z" fill="rgba(128,128,128,.9)"/></marker></defs>
<text x="10" y="22" class="t2">PEOPLE</text><text x="205" y="22" class="t2">FRONT DOORS</text>
<rect class="bd" x="395" y="30" width="495" height="380" rx="10"/><text x="410" y="50" class="t2">YOUR HOSTING BOUNDARY (confirm with security and privacy)</text>

<g data-p="2" class="a2"><rect class="bx" x="10" y="75" width="150" height="70" rx="8"/><text x="22" y="105" class="t1">Visitors on</text><text x="22" y="124" class="t1">the site</text></g>
<g data-p="1" class="a1"><rect class="bx" x="10" y="215" width="150" height="70" rx="8"/><text x="22" y="245" class="t1">People in their</text><text x="22" y="264" class="t1">own AI chat</text></g>
<g data-p="1"><rect class="bd" x="10" y="335" width="150" height="62" rx="8"/><text x="22" y="361" class="t1">Outside AI model</text><text x="22" y="380" class="t2">out of scope</text></g>

<g data-p="2" class="a2"><rect class="bx" x="205" y="75" width="170" height="70" rx="8"/><text x="217" y="100" class="t1">Door 2</text><text x="217" y="119" class="t2">Chat box on a page</text><text x="217" y="135" class="t2">You build and run it</text></g>
<g data-p="1" class="a1"><rect class="bx" x="205" y="215" width="170" height="70" rx="8"/><text x="217" y="240" class="t1">Door 1</text><text x="217" y="259" class="t2">AI chat tool calls you</text><text x="217" y="275" class="t2">No chat screen to build</text></g>

<g data-p="2" class="sh"><rect class="bx" x="425" y="75" width="150" height="70" rx="8"/><text x="437" y="100" class="t1">Gateway</text><text x="437" y="119" class="t2">Who is asking?</text><text x="437" y="135" class="t2">Logs, remove personal info</text></g>
<g data-p="1 2" class="sh"><rect class="bx" x="425" y="215" width="150" height="70" rx="8"/><text x="437" y="240" class="t1">Tool server</text><text x="437" y="259" class="t2">Search, get page,</text><text x="437" y="275" class="t2">find contact, last updated</text></g>

<g data-p="1 2"><rect class="bx" x="670" y="75" width="200" height="70" rx="8"/><text x="682" y="100" class="t1">Search</text><text x="682" y="119" class="t2">Index with access tags</text><text x="682" y="135" class="t2">Fresh via change events</text></g>
<g data-p="1 2"><rect class="bx" x="670" y="215" width="200" height="70" rx="8"/><text x="682" y="240" class="t1">Page reads</text><text x="682" y="259" class="t2">Checked against the</text><text x="682" y="275" class="t2">user's permissions</text></g>
<g data-p="1 2"><rect class="bx" x="670" y="330" width="200" height="66" rx="8"/><text x="682" y="357" class="t1">Content store</text><text x="682" y="377" class="t2">Source of truth</text></g>

<path class="ln p2" data-p="2" d="M160 110H205"/><path class="ln p2" data-p="2" d="M375 110H425"/><path class="ln p2" data-p="2" d="M500 145V215"/>
<path class="ln p1" data-p="1" d="M160 250H205"/><path class="ln p1" data-p="1" d="M375 250H425"/><path class="ln p1" data-p="1" d="M85 335V285"/>
<path class="ln shared" data-p="1 2" d="M575 235C620 235 620 120 670 115"/>
<path class="ln shared" data-p="1 2" d="M575 255H670"/>
<path class="ln shared" data-p="1 2" d="M770 285V330"/>
</svg>
<p id="fdn" class="note"></p>
</div>
<script>
(function(){
var el=document.getElementById('fd'),n=document.getElementById('fdn');
var T=["Both doors end at the same purple layer. You build the tool server, the permission checks and the logging once.",
"Door 1: people keep the AI tool they already use. It sends who they are with each request. The tool server checks their access. You build no chat screen, but you depend on that tool supporting your connector.",
"Door 2: a chat box on your own page. The gateway reads the user's sign-in, then calls the same tool server. You control the look, logs and behaviour, and you build and run more."];
function set(d){el.className='fd d'+d;n.textContent=T[d];[].forEach.call(el.querySelectorAll('button'),function(b){b.setAttribute('aria-pressed',b.dataset.d==d);});}
[].forEach.call(el.querySelectorAll('button'),function(b){b.onclick=function(){set(+b.dataset.d);};});
set(0);
})();
</script>

## Try it: four uses, ranked by risk

Pick a use. Then switch the guardrails on and off and watch what people feel.

<style>
.wx{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:14px;margin:1.2em 0;font-size:.95em}
.wx button{font:inherit;padding:4px 10px;border:1px solid rgba(128,128,128,.55);border-radius:6px;background:transparent;color:inherit;cursor:pointer}
.wx button[aria-pressed=true]{background:#1f6feb;color:#fff;border-color:#1f6feb}
.wx .row{display:flex;flex-wrap:wrap;gap:8px 12px;margin:8px 0;align-items:center}
.wx .card{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:10px;margin:6px 0}
.wx .note{opacity:.85;font-size:.9em}
.wx .face{font-size:2.4em;line-height:1}
.wx .wc{display:grid;grid-template-columns:minmax(0,1fr) minmax(0,1fr);gap:16px;align-items:start}
@media (max-width:820px){.wx .wc{grid-template-columns:1fr}}
.wx .mm{display:flex;gap:10px;align-items:center;border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:8px}
.wx .risk{display:inline-block;padding:1px 9px;border-radius:9px;font-size:.85em;color:#fff}
</style>
<div class="wx" id="w16" markdown="0">
<div class="row" id="w16u" role="group" aria-label="Use case"></div>
<div class="row" id="w16g" role="group" aria-label="Guardrails"></div>
<div class="wc">
<div class="card" id="w16d"></div>
<div class="mm"><span class="face" id="w16f"></span><div id="w16t"></div></div>
</div>
<p class="note">Illustrative only. Risk levels are a first view to test with your security and privacy advisors.</p>
</div>
<script>
(function(){
var U=[
{n:"1. Ask the AI chat about the site",r:"Low",c:"#2da44e",who:"Nobody needs to approve. The reader judges the answer.",what:"Answers questions from approved content and links to each source.",g:"Reads only what that person can see. Always shows sources."},
{n:"2. Page helper",r:"Low to medium",c:"#d98e04",who:"Content owner approves the topic scope.",what:"A chat box on a page answers questions about that topic, with links.",g:"Scoped to the page topic. Offers a link to the full page."},
{n:"3. Editor assistant",r:"Medium",c:"#e07b00",who:"An editor approves every change.",what:"Drafts summaries, suggests tags and checks plain language.",g:"Drafts only. Nothing is published without an editor."},
{n:"4. Workflow agent",r:"High",c:"#e5534b",who:"A named person approves every write.",what:"Looks up case or service status and drafts next steps.",g:"Read-only at first. Any write needs human approval."}];
var G=[["src","Show sources"],["perm","Respect permissions"],["human","Human approves"]];
var u=0,on={src:true,perm:true,human:true};
var bu=document.getElementById('w16u'),bg=document.getElementById('w16g'),d=document.getElementById('w16d'),f=document.getElementById('w16f'),t=document.getElementById('w16t');
function draw(){
 bu.innerHTML='';U.forEach(function(x,i){var b=document.createElement('button');b.textContent=x.n;b.setAttribute('aria-pressed',i==u);b.onclick=function(){u=i;draw();};bu.appendChild(b);});
 bg.innerHTML='<span class="note">Guardrails:</span>';G.forEach(function(x){var b=document.createElement('button');b.textContent=x[1];b.setAttribute('aria-pressed',on[x[0]]);b.onclick=function(){on[x[0]]=!on[x[0]];draw();};bg.appendChild(b);});
 var x=U[u];
 d.innerHTML='<strong>'+x.n+'</strong> <span class="risk" style="background:'+x.c+'">'+x.r+' risk</span><p>'+x.what+'</p><p><strong>Who decides:</strong> '+x.who+'</p><p><strong>Main guardrail:</strong> '+x.g+'</p>';
 var off=3-(on.src+on.perm+on.human);
 var e,m;
 if(!on.perm){e='😨';m='<strong>Alarmed.</strong> The AI showed something the person should never have seen. Trust is hard to win back.';}
 else if(!on.src&&!on.human){e='😕';m='<strong>Unsure.</strong> A confident answer with no link and no check. People cannot tell right from wrong.';}
 else if(!on.src){e='🤔';m='<strong>Doubtful.</strong> The answer sounds fine, but there is no source to check it against.';}
 else if(!on.human&&u>=2){e='😟';m='<strong>Worried.</strong> Changes go out with no person checking. One error spreads fast.';}
 else {e='😊';m='<strong>Confident.</strong> The answer links to its source, respects who is asking, and a person stays in charge.';}
 f.textContent=e;t.innerHTML=m;
}
draw();
})();
</script>

## What sits behind the front doors

A few plain building blocks do most of the work:

- **A search index** built from your content. It must carry access tags, or restricted pages can leak into answers.
- **Change events** that update the index when a page is published or changed. Without them, answers go stale.
- **A small tool server** with read-only tools to start: *search*, *get one page*, *find a contact* and *when was this last updated*. Nothing that writes.
- **The user's identity** passed with every request. The tool server checks access for that person, every time.

Drafts, archived pages and restricted pages stay out of the general index. Each answer shows the page's last-updated date, so people can judge freshness. This is the same idea as the signals in [Can I Trust This Page?]({{ '/can-i-trust-this-page/' | relative_url }}).

## Security checklist

- **Classification:** confirm the classification of the content before indexing anything.
- **Hosting:** keep the index, tool server and any model inside your approved hosting boundary.
- **Personal information:** filter it before a prompt leaves your boundary.
- **Logging:** record every search, tool call and answer, and keep logs as policy requires.
- **Rate limits:** per user and per tool, to stop runaway loops and misuse.
- **Vendor terms:** the AI platform must not train its models on your content. Put it in the contract.

## The human side: confident does not mean correct

AI answers read smoothly. That is the risk. Our brains tend to accept a fluent, confident answer without checking it, and to lean on the first number or story we are given. I wrote about this in my notes on [Think Fast, Think Slow]({{ '/books/Think-Fast-Think-Slow/' | relative_url }}), and the same book is why the guardrails above are design choices, not extras.

- **Show sources** so the careful, slow part of the brain has something to check.
- **Show freshness** so an old page does not look current.
- **Keep a person in the loop** for anything that changes content or records.
- **Make it easy to flag a wrong answer,** and send that flag to the page owner, as in [One Queue]({{ '/one-queue-consolidated-views/' | relative_url }}).

For government work, also check current guidance on generative AI and on automated decision-making before you go live.

## A small first step

1. Confirm that your AI platform can call your tools with the user's identity.
2. Choose the top two uses with the people who will own them.
3. Have security and privacy advisors review classification and hosting.
4. Build a small proof of concept with the search and get-page tools on a copy of the content.
5. Agree how you will measure success before you start.

Not yet: no write access to records, and no model or vendor chosen until the earlier steps are done.

**Build the integration once, and let each front door reuse it.**
