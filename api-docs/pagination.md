---
title: Pagination
category:
  uri: REST APIs OVERVIEW
---
All endpoints that return lists of objects use pagination. Pagination allows consumers to request a part of the list using a page or cursor-based pagination mechanism.

# Page-based pagination
Page-based pagination also known as offset-pagination, divides the result into smaller pages of elements.
Using page-size and page-number to control the size of each page and which page to be returned.

## Page-based Pagination Response Object

Please find a sample of a page-based paginated JSON response below. Each paginated response contains the following attributes.

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

## Requesting Page-based Paginated Results

In order to allow for a control over the pagination, Trackunit APIs expose a set of query parameters `size`, `page` and `sort` to control the result.

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

# Cursor-based pagination
Cursor-based pagination, divides the result into smaller pages of elements.
Using a combination of page-limit and Cursor to control the number of elements returned and where the subsequent request should start from.
Unlike page-based pagination, cursor-based returns an ID associated with the cursor, pointing to either the first or last elements in the returned result.
This ID can be used to control where the next result set should begin from.
## Cursor-based Pagination Response object

Find a sample cursor-paginated JSON response below. Each paginated response will contain some of the following attributes.

```json
{
    ① "before": "00ul7f8m2qkOPuXF5357",
    ② "after": "Wam4pf8m2qk8KuXF3446",
    ③ "limit": 20,
    ④ "content": [
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

① Cursor pointing to the first element in the content
② Cursor pointing to the last element in the content
③ Maximum number of content elements returned
④ A list of resources returned, each one represented as a JSON object

## Requesting cursor-based paginated result

In order to control the cursor-based pagination, Trackunit APIs expose a set of query parameters `limit`, `before`, `after` and `sort` to control the result.

For example:

```
GET https://iris.trackunit.com/public/api/operator/operators?limit=20&sort=-displayName&after=W251bGwsIjAwdXNwYTR2cnd3aTdrNngwMzU3Il0=
```

Will result in a page of the next 20 elements `after` the last element in previous result, sorted by `displayName` in descending order.

Query parameters that control pagination are optional.

| Parameter | Description                                                                                                                                                                                                                                                       | Default value                                                             |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------|
| `before`  | Request elements from before The cursor Id. Only applicable if there is any previous result.                                                                                                                                                                      | None                                                                      |
| `after`   | Request elements from after the cursor Id. Only applicable if there is more result.                                                                                                                                                                               | None                                                                      |
| `limit`   | The maximum number of elements to be returned in a page                                                                                                                                                                                                           | Default and max limit depends on a case by case basis                     |
| `sort`    | attribute(s) optionally prefixed with a + or a - sign to indicate ascending (default when prefix is missing) or descending order for each field. Please refer to the documentation of a specific endpoint to learn which attributes may be requested for sorting. | Default sorting and number of attributes depends on a case by case basis. |