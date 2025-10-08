---
title: Using a Custom Field
category:
  uri: "/branches/1.0/categories/guides/Apps & Extensions"
parent:
  uri: save-data-from-your-app
---



1. Open a Terminal or Command window and install the custom fields API.

```
npm install @trackunit/custom-field-api
```

2. Use the hook `useUpdateCustomFieldValues` to save the custom field value by entering a definition `key`, `entity ID`, and a new `value`.

```ts
// initialize the hook
const { updateCustomFields, inProgress } = useUpdateCustomFieldValues(
  assetId,
  "ASSET",
  fields,
  systemOfMeasurement ?? "SI",
);

// Save a custom field value
updateCustomFields({
  definitionId: "my-id",
  value: {
    stringValue: "My new value",
  },
});
```

3. Use the `useCustomFieldsValueAndDefinition` hook to retrieve custom fields definitions and values saved to the specified `Asset ID`. The `useCustomFieldsValueAndDefinition` hook will return the definition of a custom field only if it's value is set. Use the hook `useCustomFieldDefinitions` if you need to get all available definitions.

> Note: In order to use custom fields your app needs the correct consent scopes.
> `asset.view` to read, and `account.asset.manage` to be able to update values.

```ts
import {
  CustomFieldValueAndDefinition,
  useCustomFieldsValueAndDefinition,
  useUpdateCustomFieldValues,
} from "@trackunit/custom-field-api";

// Get all custom field values and definitions for your asset ID.
const { fields, loading } = useCustomFieldsValueAndDefinition({
  entityType: "ASSET",
  entityId: assetId,
  systemOfMeasurement: systemOfMeasurement ?? "SI",
});
```

## React UI (User Interface) Components

Trackunit provides a React UI Component that renders a custom field input box according to a custom field definition.

```
npm install @trackunit/custom-field-components
```

See this complete example for how to use the component:

```ts

import {
  CustomFieldValueAndDefinition,
  useCustomFieldsValueAndDefinition,
  useUpdateCustomFieldValues,
} from "@trackunit/custom-field-api";
import { CustomField } from "@trackunit/custom-field-components";
import { Button, Card, CardBody, CardFooter, CardHeader, Spinner } from "@trackunit/react-components";
import { SystemOfMeasurementType } from "@trackunit/react-core-contexts-api";
import { useAssetRuntime, useCurrentUserSystemOfMeasurement } from "@trackunit/react-core-hooks";
import { Control, FieldValues, FormState, UseFormRegister, UseFormSetValue, useForm } from "react-hook-form";

export const App = () => {
  const { assetInfo } = useAssetRuntime();
  if (assetInfo && assetInfo.assetId) {
    return <CustomFieldsForm assetId={assetInfo.assetId} />;
  } else {
    return null;
  }
};

const CustomFieldsForm = ({ assetId }: { assetId: string }) => {
  const { register, handleSubmit, formState, setValue, control } = useForm({
    shouldUnregister: false,
  });
  const { systemOfMeasurement } = useCurrentUserSystemOfMeasurement();
  const { fields, loading } = useCustomFieldsValueAndDefinition({
    entityType: "ASSET",
    entityId: assetId,
    systemOfMeasurement: systemOfMeasurement ?? "SI",
  });
  const { updateCustomFields, inProgress } = useUpdateCustomFieldValues(
    assetId,
    "ASSET",
    fields,
    systemOfMeasurement ?? "SI"
  );

  return (
    <Card>
      <CardHeader heading="Custom Fields" subHeading="Showcase for custom fields." />
      <CardBody>
        {loading ? (
          <Spinner />
        ) : (
          <Fields {...{ fields, register, formState, setValue, control, systemOfMeasurement }} />
        )}
      </CardBody>
      <CardFooter>
        <Button loading={inProgress} onClick={handleSubmit(updateCustomFields)}>
          {inProgress ? "Saving..." : "Save Changes"}
        </Button>
      </CardFooter>
    </Card>
  );
};

const Fields = ({
  fields,
  formState,
  register,
  setValue,
  control,
  systemOfMeasurement,
}: {
  fields: CustomFieldValueAndDefinition[];
  register: UseFormRegister<FieldValues>;
  formState: FormState<FieldValues>;
  setValue: UseFormSetValue<FieldValues>;
  control: Control<FieldValues>;
  systemOfMeasurement: SystemOfMeasurementType | null;
}) => {
  return (
    // eslint-disable-next-line react/jsx-no-useless-fragment
    <>
      {fields.map(field => {
        const isEditable = field.valueEditable && (field.definition.uiEditable ?? true);
        return (
          <CustomField
            control={control}
            field={field}
            formState={formState}
            isEditable={isEditable}
            key={field.definition.key}
            register={register}
            setValue={setValue}
            unitPreference={systemOfMeasurement}
          />
        );
      })}
    </>
  );
};

```
