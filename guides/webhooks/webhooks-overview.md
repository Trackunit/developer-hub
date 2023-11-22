---
title: Overview
category: 652e408346c8860073a6bd12
---
Welcome to our Webhooks guide. In this guide, we'll walk you through the concept of webhooks and provide detailed instructions on how to consume them in your applications. Webhooks are a powerful mechanism for enabling real-time communication between our system and yours.

## What Are Webhooks?
Webhooks are user-defined HTTP callbacks. They allow our system to notify your application about events that occur in real-time. Instead of repeatedly polling our API to check for updates, your application subscribes to specific events, and we send HTTP POST requests to the provided URL whenever these events occur.

## How Webhooks Work
1. **Adding Endpoint:**
You subscribe to specific [events](https://developers.trackunit.com/docs/event-catalog) of interest by providing a callback URL in your application. This URL is where we will send HTTP POST requests when the subscribed events occur.


2. **Event Trigger:**
   An event, such as a new data entry or a system update, occurs in our system.


3. **HTTP POST Notification:**
When the subscribed event occurs, our system sends an HTTP POST request to the provided callback URL with relevant data about the event.


4. **Processing the Payload:**
Your application receives the POST request and processes the payload to take appropriate actions based on the event data.