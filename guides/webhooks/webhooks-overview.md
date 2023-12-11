---
title: Overview
category: 652e408346c8860073a6bd12
---
Welcome to Trackunit's Webhooks guide!
In this guide, we'll walk you through the concept of webhooks and provide detailed instructions on how to consume them in your applications. Webhooks are a powerful mechanism for enabling real-time communication between our system and yours.

## What Are Webhooks?
Webhooks are user-defined HTTP callbacks. They allow our system to notify your application about events that occur in real-time. Instead of repeatedly polling our API to check for updates, your application subscribes to specific events, and we send HTTP POST requests to the provided URL whenever these events occur.

## Why Use Webhooks?
With the addition of webhooks, we are extending our Iris capabilities to make it easier to set up meaningful workflows by e.g. triggering actions and notifications in external systems that help you run your business. The Trackunit Iris platform collects and stores data about events that happened to an asset. Via our webhooks technology you can subscribe to relevant event types and get event data served in real-time. By subscribing to these events via webhooks, you can easily trigger actions across connected  programs to simplify operations or generate user notifications in your preferred interfaces. 

### Example Use Cases
- Gain valuable synergies by bringing alert or fault events into your ERP system in real-time, so critical machine issues can get addressed in a timely manner.
- Get informed in real-time if an asset leaves a depot site and correlate this event e.g. with data about it's rental status: if it is not on rent or scheduled for transfer, you are enabled to take action in case it is stolen
- Subscribe to service management events to know in real-time if a service becomes due on an asset and use this information as a trigger to schedule technician tasks

## How Webhooks Work
1. **Adding Endpoint:**
You subscribe to specific [events](https://developers.trackunit.com/docs/event-catalog) of interest by providing a callback URL in your application. This URL is where we will send HTTP POST requests when the subscribed events occur.


2. **Event Trigger:**
   An event, such as a new data entry or a system update, occurs in our system.


3. **HTTP POST Notification:**
When the subscribed event occurs, our system sends an HTTP POST request to the provided callback URL with relevant data about the event.


4. **Processing the Payload:**
Your application receives the POST request and processes the payload to take appropriate actions based on the event data.
