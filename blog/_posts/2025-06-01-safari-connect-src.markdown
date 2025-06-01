---
layout: post
title:  "CSP header - connect-src"
date:   2025-06-01 19:16:28 +0200
categories: security csp headers
---
One of recent assignment was integration with external resource on frontend via http request. Domain was not added to `default-src` or any other place as it contains only request from application which handles response (no external scripts, CSS etc). Firefox and Chrome blocked the request while Safari allowed on it. That was surprising. Quick search for RFC - I did not find any document describing how to treat CSP when `connect-src` is absent. However [OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html){:target="_blank"} and [Mozilla](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/connect-src){:taget="_blank"} came with help.

It is clearly specified: if `connect-src` is not present, it should take domain list from `default-src`. Safari does not follow this principle, just allow for calls. It is a bit unsecure as by documentation, it should not. Solution? Test your code always on multiple browsers and operating systems. 