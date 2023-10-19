---
title: trackunit/iris-app v0.0.367 - renamed publishApp to submitApp
type: improved
---

[Breaking change] In this version of our Iris App SDK we have renamed publishApp to submitApp to avoid confusion about when an app was actually made public. 
This change means that for existing apps you should open up the `project.json` file and change:

```json
  "publishApp": {
    "executor": "@trackunit/iris-app:publish",
```

To now refer to the submit executor:

```json
  "submitApp": {
    "executor": "@trackunit/iris-app:submit",
```
