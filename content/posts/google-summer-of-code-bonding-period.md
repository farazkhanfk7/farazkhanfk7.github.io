+++ 
draft = false
date = 2021-06-09T14:38:09+05:30
title = "Google Summer of Code 2021 — Community Bonding Period @ Hydra Ecosystem"
description = ""
slug = "google-summer-of-code-2021-community-bonding-period-hydra-ecosystem"
authors = ["Hasan Faraz Khan"]
tags = ["gsoc","open-source"]
categories = []
externalLink = ""
series = []
+++

> Finally GSoC’21 community bonding period is over and now we’ll be moving to the coding phase. It was an amazing journey for me. I made some contributions to the projects and learned a lot of things from my mentors. In this blog, I’ll be sharing my journey with [Hydra Ecosystem](https://www.hydraecosystem.org/) as an open-source contributor.

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*2qx3yIp2EsbfPsAHaEHJ5g.jpeg)

I started my journey of open-source contributions with Hydra Ecosystem. Hydra Ecosystem aims to build a set of tools to automate the process of building REST APIs and Next-Gen smart clients which follow the principle of Semantic Web, Linked Data, and JSON-LD. Hydra is a vocabulary for APIs which machines can understand and it is currently a draft that is created and maintained by [Hydra-CG](https://www.hydra-cg.com/). _Check_ [_Specifications_](https://www.hydra-cg.com/spec/latest/core/)_._

Getting started with Hydra Ecosystem
------------------------------------

I mostly work on Python-based frameworks and libraries. Better to say I like working on stacks and frameworks that are built on top of Python. My work usually revolves around projects that are related to Backend Development, which is why I started looking for some active open-source projects to contribute in the same domain. This is when I found [HTTP-APIs](https://github.com/HTTP-APIs) on GitHub and made my first contribution. My initial days in the community were spent on understanding the tools that are being used in the organisation. It’s been 6 months since then, and I got to learn so many things from the community. Contributing to open-source made a good impact on my way of writing codes, test cases, and debugging. It also changed my way of refactoring codes and maintaining my personal projects. More details about my project can be found here:

[https://summerofcode.withgoogle.com/projects/#6336003247177728](https://summerofcode.withgoogle.com/projects/#6336003247177728)

What is the Community Bonding Period ?
--------------------------------------

> The community bonding period is when you work out further details of your project plan, schedule regular upcoming meetings with your mentor, get your development environment set up and start to engage with the project’s open source community. This is the time to work with your mentor on setting expectations for your interactions and how your progress is measured during the GSoC program. [Source](https://google.github.io/gsocguides/student/working-with-your-mentor#community-bonding-period)

The community bonding period for GSoC 2021 officially started right after the student’s projects were announced i.e on 17th May 2021. We had a conference meeting with all the mentors, and we discussed our plans for this year’s projects. During the meet, [Samesh Lakhotia](https://github.com/sameshl) and [Priyanshu Nayan](https://github.com/priyanshunayan) talked about their experiences from last year's GSoC in which they participated as students.

One of my mentors, [Lorenzo (Mec-iS)](https://github.com/Mec-iS) suggested me to start learning about Python Packaging and Google Cloud Platform, which could be very useful for this year’s [Banking Service with Open Risk and Hydra Ecosystem](https://summerofcode.withgoogle.com/projects/#4830252137709568) project. I also dived deeper into testing frameworks and spent some time creating CI pipelines with Gitlab CI and Github Actions.

I was also asked to review a PR in the [hydra-python-core](https://github.com/HTTP-APIs/hydra-python-core) library and realized that it needs some more changes. The issue was about changing the format of URIs. It took me some days to understand the issue and debug the core library to find the required changes. I submitted the following PRs to solve the issue:

*   [https://github.com/HTTP-APIs/hydra-python-core/pull/81](https://github.com/HTTP-APIs/hydra-python-core/pull/81)
*   [https://github.com/HTTP-APIs/hydra-python-core/pull/84](https://github.com/HTTP-APIs/hydra-python-core/pull/84)
*   [https://github.com/HTTP-APIs/hydrus/pull/578](https://github.com/HTTP-APIs/hydrus/pull/578)

Also, I had conversations with [Purvansh Singh](https://github.com/Purvanshsingh) who is also participating as a GSoC student this summer and we discussed our projects and plans for the next few months.

**What’s next ?**

![captionless image](https://miro.medium.com/v2/resize:fit:1222/format:webp/1*RhmWY1QoSs5kkrIM3OBjvw.png)

I revisited my proposal and made plans for Phase-1. I’ll be opening some issues that I’ll be working on and will manage my weekly plans on GitHub Projects. For this month — I’ll add some more changes to existing endpoints and will create some new ones to delete multiple members from a Collection. I’ll also explore the issue of Dynamic Endpoints and will discuss its implementation with mentors. Apart from this, I’ll also spend some time learning and diving deeper into _pytest framework_ as it’s related to a change we would like to have in the next phase.
