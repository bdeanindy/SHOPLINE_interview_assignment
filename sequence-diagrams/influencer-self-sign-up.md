# Self-Sign-Up for Influencers

**Self-Sign-Up tor influencers:** Enable influencers to onboard themselves and automatically set up personalized websites where the can sell products across up to ten (10) distinct categories of branded product lines.

## Developer Center App
* App Scope: Public
	* Influencer > Show
	* Storefront Oauth Applications > Show, Create, Delete
* Submit for approval
* Webhook: Register for Application > Install, Application > Uninstall , Access Token > Create and Access Token > Revoke webhooks, > Sales Channel > Order Paid Successfully.

## On-board Influencers (Register Influencer)

### Influencer Installs App

```mermaid
sequenceDiagram
    participant I as Influencer
    participant A as Application
    participant API as SHOPLINE API
    participant DB as Database

    Note over I, A: Preparation
    I->>A: Install App
    A->>API: Register webhook (Install, Uninstall, Token Create/Revoke)
    A->>DB: Store webhook information

    Note over I, A: When Influencer Installs App
    I->>A: Initiate App Installation
    A->>API: Obtain Open API Access Token
    API->>A: Return Access Token
    A->>API: Setup Storefront OAuth Application
    API->>A: Return OAuth App Details
    A->>DB: Store OAuth App Details in DB

    Note over I, A: Clean up when Influencer Uninstalls App
    I->>A: Uninstall App
    A->>API: DELETE /storefront/oauth_applications/{id}
    API->>A: Confirm Deletion

    Note over I, A: Perform OAuth for Customer
    I->>A: Request OAuth Authorization
    A->>I: Redirect to Influencer URL /oauth/authorize
    I->>A: Redirect to OAuth Callback URL with code
    A->>API: POST /oauth/token with code
    API->>A: Return Access Token and other details
    A->>API: GET /oauth/token/info
    API->>A: Return Detailed User Info

```



### Create Website for Influencer

1. Create storefront oauth app when influencer installs app: POST https://open.shopline.io/v1/storefront/oauth_applications

### Select Product Categories to add to storefront


```mermaid
sequenceDiagram
    participant I as Influencer
    participant A as Application
    participant API as SHOPLINE API
    participant DB as Database

    Note over I, A: Influencer Assigns Product Category
    I->>A: View Product Categories
    A->>API: GET /admin/openapi/v20240601/products/collects.json?fields=collection_id,product_id
    API->>A: {"collects: [{"collection_id": "123", "product_id": "567"}, {"collection_id": "123", "product_id": "567"}]
    A->>I: Display list of Product Categories available to assign
    I->>A: Selected Product Category `collection_id`
    A->>DB: Store selected `collection_id`

    Note over I, A: Influencer Unassigns Product Category 
    I->>A: Unassign Product Category
    A->>API: DELETE /storefront/oauth_applications/{id}
```
