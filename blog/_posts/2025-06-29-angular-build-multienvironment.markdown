---
layout: post
title:  "Angular - build once for multiple environments"
date:   2025-06-29 18:23:21 +0200
categories: frontend angular build environments
---

## Angular in multiple environments

When building frontend applications that rely on a backend, one of the main challenges is handling configuration settings that change depending on the environment (development, staging, production, etc.).

According to [The Twelve-Factor App](https://12factor.net/){:target="_blank"}, an application should be built once and deployed many times. This means configuration must be kept separate from the code itself. Since frontend code runs entirely in the browser, it is especially important to ensure it can access the resources it needs — without hardcoding environment-specific values into the application.

## Common Approaches to Environment Configuration

If you are working with multiple environments, here are two popular strategies you can consider:

### 1. Centralized Settings Service

A single configuration service can be created and exposed under a shared DNS name across environments.

**Pros:**

- Simple and fast to implement

**Cons:**

- Requires careful compatibility management between environments
- Can introduce access or permission challenges when switching between environments

### 2. Variable Substitution

This approach involves preparing a template file and substituting variables at deployment time. There are two main ways to do this:

- **Pipeline substitution**: Replace variables during deployment
- **Runtime substitution**: Use environment variables at container startup (if the app is containerized)

In both cases, the final configuration file is served to the frontend when the site loads.

**Pros:**

- Easy to support multiple environments without changing the codebase

**Cons:**

- Versioning and tracking configuration changes can be more complex

## What’s the Best Option?

The right solution depends on your project’s specific needs. Personally, I prefer using containers with runtime variable substitution. It is flexible, easy to maintain, and avoids the need for frequent redeployments just to update configuration settings.