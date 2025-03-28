---
title: Understanding Environments
category: 66c49b7d61daf600186e12cb
---
Automation Studio workspaces have an environments feature, which means that the users can switch between a Development, a Test and a Production environment.

## Available Environments

![Switching environments](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/automation-studio/switch-environments.png)

**Development**
- Used for recipe development and serves as a sandbox for experimentation and iteration.
- Used to deploy projects to other environments, including Production.
- Used to maintain teams and the account, including collaborator roles, projects, folders, etc.
- Develop recipes without any financial commitment, making it an ideal space for experimentation and learning.

> 💡 Best Practice
> 
>Changes to automations should only be made in the Development environment to ensure modifications are captured and tracked accurately. Although you can change automations in the Test environment, we recommend changing automations in the Development environment only due to SDLC best practices.

**Test**	
- Used to test recipes in development to identify and fix issues.
- Ideal for involving QA teams to review and test workflows.

**Production**
- Used to run recipes that have been tested, reviewed, and approved in the development environment.
- Designed for stability and reliability, ensuring that users can depend on the workflows in operation.

## Deployment Process

Deployment is a process that pushes projects and assets from one environment in a workspace to another environment as part of the recipe development lifecycle (RDLC).

Recipes are typically developed in Development and moved to Test when they're ready for review. Issues are reported as needed and addressed in the Development environment. Then finally the recipe is moved to Production after testing and approval. You can either deploy projects and assets from Development to Test, or from Development to Production.

![Deployment of recipes](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/automation-studio/workflow-deployment.png)
