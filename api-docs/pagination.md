---
title: Pagination
category: 6295ae369ba4b1001464c9e5
---
All endpoints that return lists of objects use pagination. Pagination allows consumers to request a part of the list using an offset-based pagination mechanism.

## Pagination Response Objects

Please find a sample paginated JSON response below. Each paginated response contains the following attributes.

```json
{
    ① "totalPages": 2,
    ② "totalElements": 28,
    ③ "number": 1,
    ④ "size": 20,
    ⑤ "numberOfElements": 8,
    ⑥ "content": [
        {
            ...
        },
        {
            ...
        },
        ...
    ]
}
```

 ① Total number of pages  
 ② Total number of elements across all pages  
 ③ 0-based number of the page  
 ④ Maximum number of elements in the page  
 ⑤ Number of elements in the current page  
 ⑥ A list of resources in the page, each one represented as a JSON object

## Requesting Paginated Results

In order to allow for a control over the pagination, Trackunit APIs expose a set of `size`, `page` and `sort` query parameters.

For example:

```
GET https://iris.trackunit.com/api/organization/v1/groups?size=25&page=1&sort=name,-description
```

results in showing a second page of maximum 25 elements per page, sorted by `name` ascending and `description` descending.

Query parameters that control pagination are optional.

| Parameter | Description | Default value |
| :-- | :-- | :-- |
| `size` | The size of the page to be returned | 20 |
| `page` | 0-based page number. The response for a sample request above results in showing a second page. | 0 (first page) |
| `sort` | Comma-separated list of attributes optionally prefixed with a + or a - sign to indicate ascending (default when prefix is missing) or descending order for each field. Please refer to the documentation of a specific endpoint to learn which attributes may be requested for sorting. | Default sorting depends on a case by case basis. |