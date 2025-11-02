---
layout: post
title:  ".NET & OpenXML - empty line issue in Excel"
date:   2025-11-02 16:23:21 +0200
categories: openxml dotnet .net 
---

## Empty line issue in Excel

I had to implement read and write from Excel including empty lines (.NET 9, OpenXML). When I implemented it on local environment, it was writing and reading data correctly. However after deployment to AppService, it appeared empty line is not added properly when cell (data in row) is null. It must be literally specified as empty string, otherwise it skipps write to XML (checked in raw xlsx - unzipped XML), so with it, OpenXML adds empty tags for it.

I tested both MacOS and Windows, and I have no idea why it behaves differently on local environments and Azure. I bypassed it with adding empty string however I am very curious where is the exact difference. Maybe somebody from you know and can share with me?