---
title: Getting started with Automation Studio
category: 66c49b7d61daf600186e12cb
---

IrisX Automation Studio is a powerful, low-code platform designed to help developers and business users build, test, and deploy automated workflows with ease. With an intuitive drag-and-drop interface, built-in integrations, and support for custom scripts, Automation Studio enables rapid development of automation solutions across various systems and services.

Whether you're orchestrating complex backend processes or streamlining repetitive tasks, Automation Studio provides the flexibility and control needed to scale automation efficiently. This documentation will guide you through key features, components, and best practices to get the most out of IrisX Automation Studio.

## Key Concepts

### Workflow Automation Projects
Projects serve as repositories for your integration assets, including recipes, connections, and sub-folders. Organize your projects by department, use case, or project type to create a clear, logical structure. This enables you to efficiently locate and manage related assets.

### Recipes
A recipe is an automated workflow that executes a series of steps to integrate and process data across multiple applications. Every recipe includes a trigger that initiates the workflow and one or more actions that execute when a trigger event occurs. Recipes use connectors to interact with different apps, ensuring seamless data flow across systems.

Recipes run in the background, continuously monitoring for trigger events and executing actions automatically. If a recipe is stopped and later restarted, it resumes processing from where it left off.

### Connections
A connection authorizes a recipe to interact with apps like Salesforce and Zendesk through triggers and actions. Connections are reusable, allowing you to use the same connection across multiple recipes.

### Triggers
A trigger specifies the event that initiates the actions in a recipe. Triggers can be activated in various ways. For example, they might activate when a specific event occurs in an app, a new line is added to a file, or on a scheduled basis.

### Steps and actions
A recipe executes steps each time a trigger event occurs. Every recipe requires at least one step. The simplest step is an action, such as creating an organization in Zendesk.

Steps in Automation Studio can include actions, conditional actions, list actions, actions that call other recipes, or try/catch blocks.

### Jobs
A job represents the flow of a trigger event through the recipe. Each time a trigger event occurs, the recipe executes its actions. Jobs succeed when all actions execute successfully. If an error occurs, subsequent actions do not run unless error handling is configured.
