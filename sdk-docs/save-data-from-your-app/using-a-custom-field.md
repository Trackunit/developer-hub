---
title: Using a Custom Field
category: 61fcd8e1a448f5004215317c
parentDocSlug: save-data-from-your-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

1. Open a Terminal or Command window and install the Iris App Runtime.

```
npm i @trackunit/iris-app-runtime-core
```



2. Use the `CustomFieldRuntime` command to retrieve custom fields definitions and values saved to the specified Asset ID. If there are no saved values of the Asset ID, only the definition will be retrieved.

```ts
import { CustomFieldRuntime, CustomFieldType } from '@trackunit/iris-app-runtime-core';

// Get all custom field values and definitions for your asset ID.
const myCustomFieldsPromise = CustomFieldRuntime.getCustomFieldsFor({
  type: 'ASSET',
  id: '<my-asset-id>',
});
```



4. Save the custom field value by entering a definition key, entity ID, and a new value.

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

Trackunit provides a React UI (User Interface) Component that renders a custom field input box according to a custom field definition.

```
npm i @trackunit/custom-field-components
```



See this complete example for how to use the component:

```ts
import React, { useEffect, useState } from 'react';
import {
  CustomFieldRuntime,
  AssetRuntime,
  AssetInfo,
  ValueAndDefinition,
} from '@trackunit/iris-app-runtime-core';
import {
  Button,
  Card,
  CardBody,
  CardFooter,
  CardHeader,
} from '@trackunit/react-components';
import { CustomField } from '@trackunit/custom-field-components';
import { useForm } from 'react-hook-form';

export const App: React.FC = () => {
  const [customFields, setCustomFields] = useState<ValueAndDefinition[]>();
  const [asset, setAsset] = useState<AssetInfo>();
  const { register, handleSubmit, formState, setValue } = useForm({
    shouldUnregister: false,
  });

  useEffect(() => {
    (async () => {
      const updatedAssetInfo = await AssetRuntime.getAssetInfo();

      setAsset(updatedAssetInfo);
      // Using the CustomFieldRuntime you will be able to obtain all custom fields values and
      // definitions owned by the app.
      const myCustomFields = await CustomFieldRuntime.getCustomFieldsFor({
        id: updatedAssetInfo.assetId,
        type: 'ASSET',
      });
      setCustomFields(myCustomFields);
    })();
  }, []);

  // With the component it is possible to render an input component for any custom field by
  // providing a field retrieved from getCustomFieldsFor to the component.
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
        <Button
          onClick={handleSubmit((data) => {
            // To save custom field values you need to provide the the entity Id and the new value.
            CustomFieldRuntime.setCustomFieldsFromFormData(
              {
                id: asset?.assetId || '',
                type: 'ASSET',
              },
              data,
              customFields || []
            );
          })}
        >
          Save Changes
        </Button>
      </CardFooter>
    </Card>
  );
};
```
