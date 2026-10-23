---
layout: single
title: "Running a Web Platform as a Product: A Reading Guide"
date: 2026-10-23 09:35:00 -0400
description: "A short guide to ten articles on search, analytics, content ownership, operating models and teams, and how they fit together into one product management approach."
excerpt: "A short guide to ten articles on search, analytics, content ownership, operating models and teams, and how they fit together into one product management approach."
theme: digital
author_profile: false
classes: full-width
tags: [product management, ux, intranet, governance, operating model, search, analytics]
---

A web platform is not finished at launch. It is a product. People use it, it ages, and someone has to look after it.

These ten short articles share one idea: **a site stays useful when people can trust it, and trust comes from ownership, evidence and a team that stays.** They are written generically, so they apply to any intranet or content-heavy website. Each has a small interactive piece. Read them in order as a chain, or jump to the one that matches your problem.

## Which one should I read first?

Pick the question closest to yours.

<div class="wx" markdown="0" id="w9">
<style>
.wx{border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:14px;margin:1.2em 0;font-size:.95em}
.wx select{font:inherit;padding:4px 10px;border:1px solid rgba(128,128,128,.55);border-radius:6px;background:transparent;color:inherit;max-width:100%}
.wx .card{border:1px solid rgba(128,128,128,.4);border-radius:8px;padding:10px;margin:8px 0}
</style>
<label>My question: <select id="w9q"></select></label>
<div class="card" id="w9a" aria-live="polite"></div>
</div>
<script>
(function(){
var Q=[
["People do not believe what is on our pages","{{ '/can-i-trust-this-page/' | relative_url }}","Can I Trust This Page?"],
["I cannot tell which parts of the site are healthy","{{ '/content-health-reporting/' | relative_url }}","Content Health"],
["Reports tell us what is wrong but nothing gets fixed","{{ '/automation-flags-people-decide/' | relative_url }}","Automation Flags, People Decide"],
["Owners have too many pages and too many separate tasks","{{ '/one-queue-consolidated-views/' | relative_url }}","One Queue"],
["Search keeps returning the wrong page","{{ '/search-needs-content-owners/' | relative_url }}","Your Search Box Is Only as Good as Your Content Owners"],
["Our reports, menus and search do not match up","{{ '/one-vocabulary-for-search-analytics-navigation/' | relative_url }}","One Vocabulary"],
["I do not know who should do what after launch","{{ '/who-runs-the-website-operating-model/' | relative_url }}","Who Runs the Website?"],
["The site gets worse every year once the project ends","{{ '/product-manager-after-launch/' | relative_url }}","Why Your Website Needs a Product Manager After Launch"],
["We want to add AI to the site without losing trust","{{ '/adding-ai-to-a-web-platform/' | relative_url }}","Adding AI to a Web Platform"],
["We cannot get or keep the right people","{{ '/getting-and-keeping-the-team/' | relative_url }}","Getting and Keeping the Team"]];
var s=document.getElementById('w9q'),a=document.getElementById('w9a');
Q.forEach(function(q,i){var o=document.createElement('option');o.value=i;o.textContent=q[0];s.appendChild(o);});
function show(){var q=Q[s.value];a.innerHTML='Start with: <a href="'+q[1]+'"><strong>'+q[2]+'</strong></a>';}
s.onchange=show;show();
})();
</script>


## The ten articles

<style>
.gcards{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:14px;margin:1em 0}
.gcard{display:flex;flex-direction:column;gap:6px;border:1px solid rgba(128,128,128,.4);border-radius:10px;padding:14px;text-decoration:none;color:inherit;border-bottom:1px solid rgba(128,128,128,.4)}
.gcard:hover{border-color:#1f6feb;box-shadow:0 2px 10px rgba(31,111,235,.2)}
.gcard .gn{font-size:.8em;text-transform:uppercase;letter-spacing:.06em;opacity:.7}
.gcard strong{font-size:1.1em}
.gcard em{font-size:.88em;opacity:.8;margin-top:auto}
</style>
<div class="gcards" markdown="0">
<a class="gcard" href="{{ '/can-i-trust-this-page/' | relative_url }}"><span class="gn">1 &middot; Trust</span><strong>Can I Trust This Page?</strong><span>Owner, last reviewed and status: three signals that let a reader act without phoning anyone.</span><em>Try it: Age a page and switch signals.</em></a>
<a class="gcard" href="{{ '/content-health-reporting/' | relative_url }}"><span class="gn">2 &middot; Measure</span><strong>Content Health</strong><span>Four simple measures, reported by branch, that turn quality into a to-do list.</span><em>Try it: Sort branches and open an action.</em></a>
<a class="gcard" href="{{ '/automation-flags-people-decide/' | relative_url }}"><span class="gn">3 &middot; Act</span><strong>Automation Flags, People Decide</strong><span>Reminders, escalation and safe archiving, with the impact on each page at every step.</span><em>Try it: Pick reminders and an owner response.</em></a>
<a class="gcard" href="{{ '/one-queue-consolidated-views/' | relative_url }}"><span class="gn">4 &middot; Act in bulk</span><strong>One Queue</strong><span>A ranked, roll-up view for owners, managers and the product owner, with bulk actions.</span><em>Try it: Switch views and clear a queue.</em></a>
<a class="gcard" href="{{ '/search-needs-content-owners/' | relative_url }}"><span class="gn">5 &middot; Find</span><strong>Search Needs Content Owners</strong><span>Why search quality is mostly a people problem, and how owners and review dates help.</span><em>Try it: Turn ranking rules on and off.</em></a>
<a class="gcard" href="{{ '/one-vocabulary-for-search-analytics-navigation/' | relative_url }}"><span class="gn">6 &middot; Connect</span><strong>One Vocabulary</strong><span>One list of terms shared by search, analytics and navigation, so reports line up.</span><em>Try it: Compare shared and separate lists.</em></a>
<a class="gcard" href="{{ '/who-runs-the-website-operating-model/' | relative_url }}"><span class="gn">7 &middot; Run</span><strong>Who Runs the Website?</strong><span>Five roles and a RACI, with skills, tools and what the system shows each role.</span><em>Try it: Hover a role for its details.</em></a>
<a class="gcard" href="{{ '/product-manager-after-launch/' | relative_url }}"><span class="gn">8 &middot; Improve</span><strong>A Product Manager After Launch</strong><span>What happens to content freshness when nobody owns the product.</span><em>Try it: Choose habits, watch three years.</em></a>
<a class="gcard" href="{{ '/getting-and-keeping-the-team/' | relative_url }}"><span class="gn">9 &middot; Staff</span><strong>Getting and Keeping the Team</strong><span>Skills, experience and resourcing over time, including hiring delays and turnover.</span><em>Try it: Hire a team, see the vision realized.</em></a>
<a class="gcard" href="{{ '/adding-ai-to-a-web-platform/' | relative_url }}"><span class="gn">10 &middot; Extend</span><strong>Adding AI to a Web Platform</strong><span>Two front doors, one shared layer, four uses ranked by risk, and the guardrails that keep trust.</span><em>Try it: Pick a use, toggle guardrails.</em></a>
</div>

## The thread running through all of them

- **Automation flags, people decide.** Systems should remind and report. People make the call.
- **Show owners their own numbers.** Few people fix what they cannot see.
- **Do not promise what you cannot keep true.** A "Current" label on an unreviewed page does harm.
- **Plan the run, not just the build.** The day after launch is when the product starts.

Every figure in the interactive pieces is made up for illustration. Use your own data.
