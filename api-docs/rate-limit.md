---
title: Rate & Size Limiting
category: 6295ae369ba4b1001464c9e5
---
## Rate Limits

To ensure a consistant experience for all consumers of the Trackunit REST APIs, a basic rate limit and page size limit is enforced.
Individual rate limits may be specified for certain APIs and their endpoints. Those can be viewed in the specific API related documentation.

> 🚧 Rate Limits may change
> 
> Trackunit might adjust the rate limits to balance our demand and reliability.

Requests that are rate limited will get an error with a HTTP response code `429` back.


## Size Limits

In addition to limiting number of calls, a limit is also put on the max number of elements returned from our collection resources.

Unless other limits are specified in the API documentation the page size is

| Page Size         |      |
| :---------------- | :--- |
| Default page size | 20   |
| Max Page Size     | 1000 |


## Fair Use Policy

#### In summary
To uphold peak performance of all Trackunit APIs and ensure a positive experience for all partners and customers, we strongly encourage developers to review and optimize their API calls and workflows. If an application or an integration creates an excessive load on our APIs, Trackunit is at liberty, without warning, to restrict the integration's access to our APIs. We are happy to offer help and guidance on how to optimise your technical implementation.

#### Scope
This policy governs the use of Trackunit's APIs by all users, including developers, businesses, and individuals.

#### Acceptable Use:
- Integrate our APIs to enhance software or applications.
- Retrieve useful data using our APIs.
- Develop and test software with our APIs.

#### Unacceptable Use:
- Violation of laws or regulations.
- Copy, reproduce, or distribute our APIs without consent.
- Use our APIs for illegal, harmful, or malicious purposes.
- Attempt to reverse engineer or decompile our APIs.
- Use our APIs in ways that harm our services, infrastructure, or users.
- Collect personal data without appropriate consent.
- Resell or commercialize our APIs.

#### Usage Limits
We may establish usage limits for our APIs, including limits on the number of requests per minute, day, or other time period. If you exceed these limits, we may take measures to ensure compliance with this Policy, including limiting or suspending your access to our APIs.

#### Enforcement
We reserve the right to take any action we deem necessary to enforce this Policy, including, but not limited to, limiting or suspending your access to our APIs, terminating your account, or taking legal action.
