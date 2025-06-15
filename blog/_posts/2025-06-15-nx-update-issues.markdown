---
layout: post
title:  "Angular NX issues after update"
date:   2025-06-15 19:23:21 +0200
categories: frontend nx angular
---

## Update nx

Recently I was forced to update NX on local machine as project was updated. The issues start just after completion - project does not start, no message, no errors - litterly nothing. 

What typical does developer? Let's Google it! A list of most popular ideas:
* Remove `node_modules`
* Restart machine

Both done and issue still persist. Google again. Clean up project folder, checkout again, remove `package-lock.json`, rebuild. Done and issue persist. Next idea - use `verbose` flag again. Here we have an issue - you are using old version of `node.js`. Update node - issue gone!