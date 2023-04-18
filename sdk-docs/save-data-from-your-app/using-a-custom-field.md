---
title: Using a Custom Field
category: 61fcd8e1a448f5004215317c
parentDocSlug: save-data-from-your-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

1. Open a Terminal or Command window and install the Iris App Runtime.

```
npm install @trackunit/iris-app-runtime-core
```



2. Use the `CustomFieldRuntime` command to retrieve custom fields definitions and values saved to the specified `Asset ID`. If there are no saved values of the Asset ID, only the definition will be retrieved.

```ts
import { CustomFieldRuntime, CustomFieldType } from '@trackunit/iris-app-runtime-core';

// Get all custom field values and definitions for your asset ID.
const myCustomFieldsPromise = CustomFieldRuntime.getCustomFieldsFor({
  type: 'ASSET',
  id: '<my-asset-id>',
});
```



3. Save the custom field value by entering a definition `key`, `entity ID`, and a new `value`.

```ts
// Save a custom field value
customFieldRuntime.setCustomFieldsFor(
  {
    type: 'ASSET',
    id: '<my-asset-id>',
  },
  [
    {
      definitionKey: 'myKey',
      value: {
        type: CustomFieldType.STRING,
        stringValue: 'My new value',
      }
    }
  ]
);
```



## React UI (User Interface) Components

Trackunit provides a React UI Component that renders a custom field input box according to a custom field definition.

```
npm install @trackunit/custom-field-components
```



See this complete example for how to use the component:

```ts
import React from 'react';
import {
  Button,
  Card,
  CardBody,
  CardFooter,
  CardHeader,
} from '@trackunit/react-components';
import { CustomField } from '@trackunit/custom-field-components';
import { useForm } from 'react-hook-form';
import { useAssetRuntime } from '@trackunit/react-core-hooks';
import { useCustomFieldRuntimeForEntity } from './useCustomFieldRuntimeForEntity';

export const App: React.FC = () => {
  const { assetInfo } = useAssetRuntime();
  const { customFields, setCustomFieldsFromFormDataForEntity } = useCustomFieldRuntimeForEntity( {
    id: assetInfo?.assetId || '',
    type: 'ASSET'
  });

  const { register, handleSubmit, formState, setValue } = useForm({
    shouldUnregister: false,
  });

  // With the component it is possible to render an input component for any custom field by
  // providing a field retrieved from useCustomFieldRuntimeForEntity to the component.
  return (
    <Card>
      <CardHeader
        heading="Custom Fields"
        subHeading="Showcase for custom fields."
      />
      <CardBody>
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
      </CardBody>
      <CardFooter>
        <Button onClick={handleSubmit(setCustomFieldsFromFormDataForEntity)}>
          Save Changes
        </Button>
      </CardFooter>
    </Card>
  );
};
```
