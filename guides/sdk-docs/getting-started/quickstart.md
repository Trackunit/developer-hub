---
title: Quickstart
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

# Trackunit App SDK Quickstart Guide

## Introduction

The Trackunit App SDK enables developers to create applications that integrate seamlessly with the Trackunit Manager. This guide provides a quick overview of the steps to start developing your own IrisX Apps.

## Disclaimer

This is a Quickstart guide intended to help you set up a basic development environment and start a simple IrisX App. For comprehensive details, advanced features, and best practices, please refer to the full [Trackunit Developers Documentation](https://developers.trackunit.com/docs/introduction).

## Prerequisites

- Node LTS
- NX version 21.1.3 or higher
- Git
- WSL (Windows only)

## Step 1: Set Up Your Environment

1. **Install Node.js**: Download and install Node.js LTS version from [Node.js](https://nodejs.org/).
2. **Install NX**: Use npm to install the NX CLI globally with `npm install -g nx`.
3. **Set up WSL**: For Windows users, follow the guide [here](https://docs.microsoft.com/windows/wsl/install) to install WSL.

## Step 2: Create a Workspace

1. **Generate Workspace**: Run `npx @trackunit/create-iris-app-workspace your-workspace-name`.
2. **Navigate to Workspace**: Use `cd your-workspace-name` to move into your new workspace directory.

## Step 3: Create Your First IrisX App

1. **Generate IrisX App**: Execute `npx nx generate @trackunit/iris-app:create your-app-name`.
2. **Navigate to App Directory**: Find your app in the `apps` directory.

## Step 4: Create an Extension

1. **Generate Extension**: Use `npx nx g @trackunit/iris-app:extend your-extension-name`.
2. **Configure Extension**: Follow the prompts to configure the extension (e.g., select the type of extension, name, etc.).
3. **Develop Extension**: Add your custom logic and UI components in the extension directory.

## Step 5: Develop Your App

1. **Write Your Code**: Start coding your app and extension in the respective `src` directories.
2. **Local Development**: Use `npx nx run your-app-name:serve` to serve your app locally for testing.

## Step 6: Build and Deploy

1. **Build Your App**: Run `npx nx run your-app-name:build` to build your app.
2. **Submit for Approval**: Use `npx nx run your-app-name:submitApp` to submit your app for approval.

## Next Steps

- **Explore Extension Points**: Investigate different extension points like Asset Home, Site Home, or Fleet Wide.
- **Read Documentation**: Refer to [Trackunit Developers](https://developers.trackunit.com/docs/) for detailed documentation.
