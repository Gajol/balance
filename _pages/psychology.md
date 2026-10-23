---
title: "Psychology"
permalink: /psychology/
layout: single
author_profile: false
excerpt: "How people think, choose and change."
---

{% assign tfs = site.books | where: "title", "Think Fast, Think Slow" | first %}
{% assign dw = site.books | where: "title", "The Drunkard's Walk" | first %}
{% assign cq = site.books | where: "title", "Change Your Questions, Change Your Life" | first %}
{% assign dd = site.books | where: "title", "The Defining Decade" | first %}

I came to psychology sideways, through technology. If you design systems for people, sooner or later you have to ask why they do not use them the way you expected. Why do smart people make poor choices, trust the wrong number, or ignore the good option sitting in front of them? These notes follow that question through four books. Each one answers a different part of it.

## We are not as rational as we think

The place to start is [Think Fast, Think Slow]({{ tfs.url | relative_url }}) by Daniel Kahneman. His core idea is that we have two ways of thinking. One is fast, instinctive and emotional. The other is slow, deliberate and logical. Most of the time the fast one is in charge, and it is quietly wrong more often than we would like to admit. It prefers a good story to a statistic. It sees causes where there is only chance.

What stayed with me were the practical lessons. Simple formulas often beat expert judgement. A **premortem**, where a team imagines the plan has already failed and writes down why, is a cheap way to catch bias before it costs anything. Kahneman also helped found behavioural economics, which is why he is the first psychologist to win a Nobel Prize in Economics. That links this page to the next one.

## Chance does most of the work

Once you accept that our instincts mislead us, the next place they fail is chance. In [The Drunkard's Walk]({{ dw.url | relative_url }}), Leonard Mlodinow argues that randomness and luck shape outcomes far more than we like to believe. We want to see order, so we invent it. The book also shows how probability can surprise you. A positive medical test, for example, may be much less alarming than it feels, once you account for how rare the condition is.

These notes are short. They are mostly pointers to further reading, including related ideas such as *Fooled by Randomness*. I keep them because the lesson is useful at work. When a project succeeds or fails, ask how much was skill and how much was luck.

## Better questions, better choices

Knowing we are biased is one thing. Doing something about it is another. Marilee Adams offers a practical tool in [Change Your Questions, Change Your Life]({{ cq.url | relative_url }}). Her point is that the questions we ask ourselves steer our thinking. She describes two mindsets: the **Learner**, who is curious and asks open questions, and the **Judger**, who blames and defends. Her *Choice Map* helps you notice which one you are in, and switch.

The book comes with twelve tools. My favourites are the simple ones: question your assumptions, and pause with the **ABCD** steps (aware, breathe, curious, decide) before you react. It applies equally to leading a team, coaching a colleague, or arguing with yourself.

## Choices over a lifetime

The last book moves from how we decide to when. Meg Jay's [The Defining Decade]({{ dd.url | relative_url }}) is about your twenties. Her argument is that this decade matters more than our culture admits. Most of life's defining moments happen then, earning power is largely set in the first ten years of work, and personality and the brain change the most.

It is written for young adults, but it is also a book for anyone who parents, mentors or hires them. Its closing line is the one I remember. When a young person asks, "Am I going to make it?", the honest answer is, "I don't know. You haven't decided yet."

## How the four fit together

- **Kahneman** explains why we err.
- **Mlodinow** shows one place where we err badly, which is chance.
- **Adams** gives a way to question our own thinking.
- **Jay** reminds us that choices compound over a life.

Taken together, they come to one idea. We cannot remove bias, but we can build habits and teams that notice it.

## All notes in this theme

{% include theme-list.html theme="psychology" %}
