# Readme documentation for developer-hub

All documentation for the Trackunit Developer Hub is written in Markdown and stored in this repository.
This is done to have version control and allow for collaboration on all the documentation for the developer hub.

## Structure
The documentation is structured in the following way:
- `api-docs` - Contains all the documentation for the APIs
- `sdk-docs` - Contains all the documentation for the App SDK
- `custompages` - Contains all the documentation for the custom pages

## How to contribute
To know more about the file format and how to contribute to the documentation, please read the [Readme documentation](https://docs.readme.com/main/docs/rdme) and the [Readme markdown documentation](https://docs.readme.com/rdmd/docs/syntax-extensions).

### Categories
The documentation is structured in categories. Each category has a unique id, which is used to reference the category in the documentation. The id is used in the frontmatter of the markdown file. The id is also used to reference the category in the navigation.

> To find the id of a category, you can use the following API endpoint.
> Note, if you are logged into the developer portal the api key is provided for you. If you are not logged in, you need to provide your api key in the request.
https://docs.readme.com/main/reference/getcategories

