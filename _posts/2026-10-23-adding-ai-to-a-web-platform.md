---
layout: single
title: "Adding AI to a Web Platform: Where It Helps, Where People Decide"
date: 2026-10-23 15:40:00 -0400
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
