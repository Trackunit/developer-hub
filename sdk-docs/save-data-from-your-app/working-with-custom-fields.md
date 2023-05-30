---
title: Working with Custom Fields
category: 61fcd8e1a448f5004215317c
parentDocSlug: save-data-from-your-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

# Trackunit SDK: Working with Custom Fields

In this guide, we'll be using the Trackunit SDK to define and manipulate custom fields in the Iris app. We will walk you through how to:

- Define a STRING and a DROPDOWN type field in the iris-app-manifest.json.
- Implement regex patterns in the STRING field.
- Use the @trackunit/iris-app-runtime-core library to render our custom fields.
- Update DROPDOWN custom field values.
- Handle incompatible STRING field values when updating regex patterns.

## Prerequisites
Before we start, you need to install the Iris App Runtime. Open a terminal and type:

```bash
npm install @trackunit/iris-app-runtime-core
```

You'll also need the React UI components to render the fields later:

```bash
npm install @trackunit/custom-field-components
```

## Step 1: Defining a Custom Field
To start, we need to define our custom fields in the `iris-app-manifest.json` file. Let's add a STRING and a DROPDOWN field. To do this, add a `customFieldDefinitions` array to your iris app manifest:

```json
"customFieldDefinitions": [
  {
    "type": "STRING",
    "entityType": "ASSET",
    "key": "myKey",
    "title": "String Field",
    "uiEditable": true,
    "uiVisible": true,
    "pattern": "^\\w+$" // (letters, digits, and underscores) 
  },
  {
    "type": "DROPDOWN",
    "entityType": "ASSET",
    "key": "myDropdownKey",
    "title": "Dropdown Field",
    "uiEditable": true,
    "uiVisible": true,
    "options": ["Option 1", "Option 2", "Option 3"]
  }
]
```

Here we added a STRING field with key `myKey` and a DROPDOWN field with key `myDropdownKey`. The STRING field includes a `pattern` property with a simple regex that enforces alphanumeric input (letters, digits, and underscores).

## Step 2: Rendering Custom Fields
Now that we have defined our custom fields, let's render them. Navigate to your `app.tsx` file and use the @trackunit/iris-app-runtime-core library:

```ts
import React from 'react';
import { CustomField } from '@trackunit/custom-field-components';
import { useForm } from 'react-hook-form';
import { useAssetRuntime, useCustomFieldRuntimeForEntity } from '@trackunit/react-core-hooks';

export const App: React.FC = () => {
  const { assetInfo } = useAssetRuntime();
  const { customFields, setCustomFieldsFromFormDataForEntity } = useCustomFieldRuntimeForEntity( {
    id: assetInfo?.assetId || '',
    type: 'ASSET'
  });

  const { register, handleSubmit, formState, setValue } = useForm({
    shouldUnregister: false,
  });

  return (
    <div>
      {customFields?.map((field) => {
        return (
          <CustomField
            field={field}
            key={field.definition.key}
            register={register}
            formState={formState}
            setValue={setValue}
          />
        );
      })}
      <button onClick={handleSubmit(setCustomFieldsFromFormDataForEntity)}>
        Save Changes
      </button>
    </div>
  );
};
```

This script will render our custom fields on the page. Run your app and navigate to any Asset to see your fields.
```bash
nx run <your_app>:serve
```
Fill out the values and hit Save Changes to store values in your fields. Pick `Option 1` for the dropdown and type `abc123` for the string.

## Step 3: Updating the DROPDOWN Field
Let's say you want to remove `Option 1` from the dropdown list and replace it with `Option 4`. From the previous step, you already have data that uses Option 1, so that's problematic. We can do this using the `dropDownValueReplacements` property. Navigate to the `iris-app-manifest.json` and update the DROPDOWN field as follows:

```json
{
  "type": "DROPDOWN",
  "entityType": "ASSET",
  "key": "myDropdownKey",
  "title": "Dropdown Field",
  "uiEditable": true,
  "uiVisible": true,
  "options": ["Option 2", "Option 3", "Option 4"],
  "dropDownValueReplacements": {
    "Option 1": "Option 4"
  }
}
```

Run your app again and you'll see that "Option 1" has been replaced by "Option 4".

## Step 4: Updating the STRING Field
Finally, let's demonstrate how to change the regex pattern for our STRING field. Currently, the pattern allows numbers. We'll change it to disallow numbers. We'll also specify a `defaultStringValue` that will replace any non-compliant existing values:

```json
{
  "type": "STRING",
  "entityType": "ASSET",
  "key": "myKey",
  "title": "String Field",
  "uiEditable": true,
  "uiVisible": true,
  "pattern": "^\\D+$", // no numbers allowed
  "defaultStringValue": "default"
}
```

Here, `^\\D+$` enforces a pattern that disallows digits. If an existing value contains a digit, it will be stored in a special table in the database, and the `defaultStringValue` "default" will be set as the new value on the field.

To retrieve the old, incompatible values, use the API. Note that we do not keep history, so only the latest incompatible value is stored.

That's it! You have successfully defined, rendered, and updated custom fields using the Trackunit SDK.