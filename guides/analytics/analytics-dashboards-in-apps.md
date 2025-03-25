---
title: Embedding IrisX Analytics Dashboards in Iris Apps
category: 66c49b0049fa5200312dc835
---

## Overview

When creating actionable insights in IrisX analytics, you maybe want to make it accessible to all your Trackunit Manager users. Let’s say you for instance want to show your users a custom dashboard that you built in IrisX analytics, this is how you can proceed: 

**1. Develop Your Analytics Solution:** Create a notebook to explore and transform IrisX catalog data which contains telematics data prepared for you by Trackunit. This way, you can build custom tables tailored to your specific business requirements. You can experiment with your code and refine your calculations until they deliver the insights you need.
    
**2. Automate Data Updates:** Once your code is final, you probably want your new table to remain updated with fresh data. You can set up a workflow to run your notebook on a regular schedule. You can adapt the frequency of the job to your needs.
    
**3. Create a Trackunit Manager App:** Now that you have real-time insights, you can design an app to your custom analytics to Trackunit manager. This approach allows you to transform specialized analytics into accessible dashboards for all Trackunit Manager users, regardless of their technical expertise.

This guide walks through the process of embedding IrisX Analytics dashboards into your IrisX applications, allowing you to provide data visualization capabilities while maintaining proper security context.

## When to Use This Approach

This embedding approach is particularly well-suited for:

- **Small-scale applications or proof-of-concepts**: When you need to quickly demonstrate value without extensive development work
- **Internal usage applications**: For teams that need to share insights within your organization
- **Daily aggregation use cases**: When working with data that doesn't require real-time updates
- **Data professional-led development**: When your team has strong data analysis skills but more limited full-stack development capabilities

### Key Considerations

- This approach relies on the IrisX Data Lake, which is updated on a batch schedule rather than in real-time
- Embedded dashboards are only accessible to users within the developer's Manager organization
- While implementation is simpler, customization options are more limited
- The approach offers significantly faster time-to-value compared to building custom visualization components

For applications requiring real-time data interaction, that will be offered on the Marketplace, or that need more extensive customization, consider more advanced approaches using the App SDK with custom UI components and direct API integrations.

## Prerequisites

- An IrisX Analytics workspace with dashboard creation permissions
- An Iris app development environment
- Appropriate data access permissions for the dashboard content

## Step 1: Create Views for Dashboard Data

Begin by creating views in IrisX Analytics that will provide the data for your dashboard. Views allow you to:

- Control which data users can access without granting direct table permissions
- Filter data based on the current user's access rights
- Present only relevant information to each user

### Best Practice: Use `current_user()` for Security

Implementing the `current_user()` function in your view definitions ensures that users only see data they have permission to access.

### Example Views

Here are two example views you might create:

1. **Asset Count View**: Displays the number of assets the current user can access
   ```sql
   CREATE VIEW current_user_asset_count AS
   SELECT COUNT(*) as asset_count
   FROM assets
   WHERE owner = current_user();
   ```

2. **Cumulative Operating Hours View**: Shows operating hours for accessible assets
   ```sql
   CREATE VIEW current_user_operating_hours AS
   SELECT asset_id, timestamp, cumulative_hours
   FROM asset_operating_hours
   WHERE asset_id IN (
     SELECT id FROM assets WHERE owner = current_user()
   )
   ORDER BY timestamp DESC;
   ```

## Step 2: Create and Configure Your Dashboard

1. Create a new dashboard in IrisX Analytics
2. Give it a meaningful title that reflects its purpose
3. Add data sources:
   - Navigate to the **Data** tab
   - Add the views you created in Step 1
4. Return to the main dashboard view and add appropriate visualizations:
   - Charts
   - Tables
   - Metrics
   - Other visualization types that best represent your data

## Step 3: Publish the Dashboard for Embedding

1. Click the **Publish** button in the dashboard interface
2. In the publishing options, select **Don't embed credentials**
   - This critical step ensures users authenticate with their own credentials
   - It maintains proper data access controls when embedded
3. After publishing, click **Embed Dashboard**
4. Copy the generated iframe code for integration into your Iris app

## Step 4: Integrate Dashboard into Your Iris App

1. [Create an Iris app](https://developers.trackunit.com/docs/getting-started) if you haven't already
2. Add the iframe code to your app's HTML
   ```html
   <iframe
     src="https://your-irisx-instance.cloud.databricks.com/dashboard/your-irisx-analytics-id"
     width="100%"
     height="800px"
     frameborder="0">
   </iframe>
   ```

3. Update your app's manifest to include IrisX Analytics in the Content Security Policy headers:
   ```json
   {
     "manifest_version": 1,
     "content_security_policy": {
       "frame-src": ["https://your-irisx-instance.cloud.databricks.com"]
     }
   }
   ```

## Step 5: Serve and Test Your App

1. Serve your app using the Iris CLI
   ```bash
   iris serve
   ```
2. Open the provided URL in your browser
3. Verify that the dashboard displays correctly and shows data specific to the current user

## Security Considerations

- User authentication flows through both systems (Iris and IrisX Analytics)
- Each user sees only the data they have permission to access
- Dashboard filters apply based on the authenticated user context

## Troubleshooting

If your dashboard doesn't appear:
- Verify that the IrisX Analytics domain is correctly added to the CSP headers
- Ensure users have appropriate permissions in IrisX Analytics
- Check browser console for potential errors

## Next Steps

Consider enhancing your implementation with:
- Interactive dashboard elements
- Customized theming to match your Iris app design

## Related Resources

- [Iris App Development Guide](https://developers.trackunit.com/docs/getting-started)
- [IrisX Analytics Embedding Documentation](https://docs.databricks.com/dashboards/embedding.html)
