# Improvement Recommendations

Comparing SHOPLINE open e-commerce capabilities to Shopify, where do I feel the biggest improvement opportunities are?


## Developer Portal Search Results 

When developers cannot quickly find what they are seeking by scanning the list of available APIs or an API's documentation, they will resort to using SHOPLINE's Developer Portal Search Tool (located at top-right of UI). However, the results produced are very poor quality:

**EXAMPLE(s):**
Use Case: As a client's developer trying to understand how SHOPLINE `Product` object types are structured and function, specifically, the developer wants to figure out how to organize their products into categories. I open the [SHOPLINE Dev Docs](https://developer.shopline.com/docsv2), and type `product` in the Search UI component (located in the top right of the view) and see the following results.

![SHOPLINE DevPortal Search for product](/images/dev_portal_serps_for_product.png)

1. If you click the first element in the results list, you receive an HTTP 404 status code
![SHOPLINE DevPortal 404](/images/dev_portal_404.png)

2, If you click the second element in the results list, the developer is taken to Templates->product, but there was no indication this was a product template in the search engine result - poor experience (wasting developer time, increasing frustration)

3. If you click the third element in the results list, the developer is taken to Helpers->Form->product, but there was no indication this was a product within a Helper Form object in the search engine result - poor experience (wasting developer time, increasing frustration)

4. If you click the fourth element in the results list, the developer is taken to Object Definitions, which seems promising, but while viewing the list of properties for the `Product` object, NOTHING is named `category` or `categories`. The only thing remotely close to product categories are `collections`, but when I click to fly out the details of the `collections` property, the only information I receive is:

![Object Definition for Product Collection](/images/object_product_collection.png)

### Projected Outcome/Result
* Low CSAT for developers
* Increased drop/bounce rate
* Increased customer/developer churn 
* Increased developer support cases

## Documentation MUST speak to the LEAST SKILLED developers

SHOPLINE API documentation makes assumptions about developers, and seems to expect developers already have a deep technical understanding of how SHOPLINE e-commerce operates, despite having a very complex data model.

**EXAMPLE(s):**
1. Products have Categories, not Collections (collections are a technical term for a list of similar objects)
2. Full list of Webhook Events is not included in the documentation anywhere, and there is no way to know what the webhook schema for an event type will be or how it can be used unless the developer actually spends time to build the webhook

### Projected Outcome/Result
* Low developer adoptions
* Orphaned developer accounts
* Low CSAT for customers with inexperienced developers building private apps using SHOPLINE for the first time
* Increased developer support cases
* Negative impact to NPS by technical users (and possibly business users)
