---
layout: post
title:  "Copilot - set global instructions for projects"
date:   2025-11-30 19:16:28 +0200
categories: copilot AI instructions
---
One of the project issues was setting up correctly naming conventions and suggestions for Copilot to receive:
* valid naming
* selected libraries

across various repositories where each repository may contain .NET and Angular code. Also projects have some specific requirements for technologies and syntax, so we have been looking for a solution where developers do not need to repeat this information when they are using Copilot chat.

As for code repository, git is used, so separate repository was created, then inside it, new `.github` folder was created and inside it, `copilot-instructions.md` is created. Then it is referenced as submodule in other projects. Then Copilot should pick it automatically for each project and each chat in this repository unless it will be disbaled.

## File structure

At the beggining, you specify if it applies to any specific technology (via file paths). If it is not specified, it will apply to all files.

```
---
applyTo: "**/*.cs"
---
```

If needed, in the same section, you can exclude AI agent eg.

```
---
excludeAgent: "code-review"
---
```

As next step, you put headers with sections, eg.

```
## Tech stack

### Backend

### Frontend
```

And then you can feel them with required details. 

```
## Tech stack
- Use descriptive names for variables, functions, modules
-

### Backend
- Use C# for backend
- Use `XUnit` for unit tests
- Use `NSubstitute` for unit tests

### Frontend
- Use Angular for frontend
- Use `@Pipe` for for custom pipes for the frontend
```

Directives and technologies mus be specified using ``, otherwise they will be ignored.

## Conclusions

The tool is very efficient, accelerating development and ensuring naming conventions are automatically enforced.