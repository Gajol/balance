---
layout: single
title: "Running a Web Platform as a Product: A Reading Guide"
date: 2026-10-23 09:35:00 -0400
description: "A short guide to seven articles on search, analytics, content ownership, operating models and teams, and how they fit together into one product management approach."
excerpt: "A short guide to seven articles on search, analytics, content ownership, operating models and teams, and how they fit together into one product management approach."
theme: digital
author_profile: false
classes: wide
tags: [product management, ux, intranet, governance, operating model, search, analytics]
---

A web platform is not finished at launch. It is a product. People use it, it ages, and someone has to look after it.

These seven short articles share one idea: **a site stays useful when people can trust it, and trust comes from ownership, evidence and a team that stays.** They are written generically, so they apply to any intranet or content-heavy website. Each has a small interactive piece you can play with.

## The big picture

Read them as a chain.

1. **Readers need to trust a page.** That comes from visible owners and review dates.
2. **Trust has to be measured.** That is content health reporting.
3. **Search shows whether it is working.** It also depends on owned, current content.
4. **One shared vocabulary lets the tools line up.**
5. **Someone must run it day to day.** That is the operating model.
6. **Someone must decide what to improve.** That is the product owner.
7. **The team must exist and stay.** That is skills, experience and resourcing over time.

## The seven articles

### For readers: trust

- [Can I Trust This Page?]({{ '/can-i-trust-this-page/' | relative_url }}) Three signals (owner, last reviewed, status) that let a reader act without phoning a colleague. *Try it: switch the signals on and off, and age the page.*

### For measurement: evidence

- [Content Health: Measuring Whether Your Website Is Current and Owned]({{ '/content-health-reporting/' | relative_url }}) Four simple measures, reported by branch, that turn "how good is our content?" into a to-do list. *Try it: switch measures and click a branch.*
- [Your Search Box Is Only as Good as Your Content Owners]({{ '/search-needs-content-owners/' | relative_url }}) Why search quality is mostly a people problem, and how owners and review dates help the right page rank first. *Try it: turn ranking rules on and watch results reorder.*
- [One Vocabulary: Sharing a Taxonomy Across Search, Analytics and Navigation]({{ '/one-vocabulary-for-search-analytics-navigation/' | relative_url }}) One controlled list of terms, so search, reports and menus can finally be compared. *Try it: switch between a shared and separate vocabularies.*

### For delivery: people and roles

- [Who Runs the Website? A Simple Operating Model]({{ '/who-runs-the-website-operating-model/' | relative_url }}) Five roles and a RACI, with what each role needs and what the system shows them. *Try it: hover a role to see its skills, tools and views.*
- [Why Your Website Needs a Product Manager After Launch]({{ '/product-manager-after-launch/' | relative_url }}) What happens to content freshness when nobody owns the product. *Try it: choose habits and watch the three-year curve.*
- [Getting and Keeping the Team]({{ '/getting-and-keeping-the-team/' | relative_url }}) Which skills a team covers, how experience changes it, and how hiring delays and turnover open gaps. *Try it: hire a team and see how much of the vision is realized.*

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
["Search keeps returning the wrong page","{{ '/search-needs-content-owners/' | relative_url }}","Your Search Box Is Only as Good as Your Content Owners"],
["Our reports, menus and search do not match up","{{ '/one-vocabulary-for-search-analytics-navigation/' | relative_url }}","One Vocabulary"],
["I do not know who should do what after launch","{{ '/who-runs-the-website-operating-model/' | relative_url }}","Who Runs the Website?"],
["The site gets worse every year once the project ends","{{ '/product-manager-after-launch/' | relative_url }}","Why Your Website Needs a Product Manager After Launch"],
["We cannot get or keep the right people","{{ '/getting-and-keeping-the-team/' | relative_url }}","Getting and Keeping the Team"]];
var s=document.getElementById('w9q'),a=document.getElementById('w9a');
Q.forEach(function(q,i){var o=document.createElement('option');o.value=i;o.textContent=q[0];s.appendChild(o);});
function show(){var q=Q[s.value];a.innerHTML='Start with: <a href="{{ site.baseurl }}'+q[1]+'"><strong>'+q[2]+'</strong></a>';}
s.onchange=show;show();
})();
</script>

## The thread running through all of them

- **Automation flags, people decide.** Systems should remind and report. People make the call.
- **Show owners their own numbers.** Few people fix what they cannot see.
- **Do not promise what you cannot keep true.** A "Current" label on an unreviewed page does harm.
- **Plan the run, not just the build.** The day after launch is when the product starts.

Every figure in the interactive pieces is made up for illustration. Use your own data.
