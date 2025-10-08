---
title: Catalog Environments
category:
  uri: "/branches/1.0/categories/guides/Analytics & Insights"
---

IrisX analytics provides separate catalogs denoted with "dev", "test" and "prod" to facilitate your workflow. Here's how to effectively use each environment:

## Development Environment (dev)
The dev catalog serves as your experimental workspace where data engineers and scientists can:

- Develop new data transformation logic and experiment with different approaches and algorithms
- Refine code without impacting other users when making frequent changes

This environment provides freedom to explore and make mistakes without consequences to downstream processes or production data.

## Testing Environment (test)
Once your logic is established and your code functions as expected in development, move to the test environment to:

- Validate your code against test datasets
- Ensure transformations produce expected outputs
- Verify job scheduling and dependencies work correctly
- Identify potential issues before they impact production systems

The test environment closely mirrors production but provides a safe space for final verification.

## Production Environment (prod)
The prod catalog is where your thoroughly tested and validated code runs on real business data:

- Execute workflows that stakeholders depend on
- Process current, business-critical information
- Generate reports and insights used for decision-making
- Maintain strict governance and change control

## Environment Switching
To streamline development across these environments, we recommend implementing parameterized code that can reference the appropriate catalog dynamically:

- Pass a dev/test/prod parameter in your code to switch target environments
- Create configuration files for each environment
- Use environment variables to control execution context

This approach allows your workflows to seamlessly transition between environments without code modifications, reducing errors and ensuring consistency across the development lifecycle. By following this structured approach to environment management, you can maintain higher code quality, reduce risks, and create more reliable data products.
