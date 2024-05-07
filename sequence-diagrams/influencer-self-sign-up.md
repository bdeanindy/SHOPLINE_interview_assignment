# Self-Sign-Up for Influencers

**Self-Sign-Up tor influencers:** Enable influencers to onboard themselves and automatically set up personalized websites where the can sell products across up to ten (10) distinct categories of branded product lines.

## Developer Center App
* App Scope:
	* Merchant > Show
	* Storefront Oauth Applications > Show, Create, Delete
* Submit for approval
* Webhook: Register for Application > Install, Application > Uninstall , Access Token > Create and Access Token > Revoke webhooks.

## On-board Influencers (Register Influencer)

### Influencer Installs App

```mermaid
sequenceDiagram
    participant M as Merchant
    participant A as Application
    participant API as SHOPLINE API
    participant DB as Database

    Note over M, A: Preparation
    M->>A: Install App
    A->>API: Register webhook (Install, Uninstall, Token Create/Revoke)
    A->>DB: Store webhook information

    Note over M, A: When Merchant Installs App
    M->>A: Initiate App Installation
    A->>API: Obtain Open API Access Token
    API->>A: Return Access Token
    A->>API: Setup Storefront OAuth Application
    API->>A: Return OAuth App Details
    A->>DB: Store OAuth App Details in DB

    Note over M, A: Clean up when Merchant Uninstalls App
    M->>A: Uninstall App
    A->>API: DELETE /storefront/oauth_applications/{id}
    API->>A: Confirm Deletion

    Note over M, A: Perform OAuth for Customer
    M->>A: Request OAuth Authorization
    A->>M: Redirect to Merchant URL /oauth/authorize
    M->>A: Redirect to OAuth Callback URL with code
    A->>API: POST /oauth/token with code
    API->>A: Return Access Token and other details
    A->>API: GET /oauth/token/info
    API->>A: Return Detailed User Info

```



### Required APIs
* Client (MLM Platform Provider)
	Influencer Management
		* App Install/Uninstall
	Influencer Signup
		* App Install/Uninstall
	Influencer Config (post-signup)


		* PUT - Add collection to sales channels: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/L7HL6W0r?version=v20240601
		* GET - Query collection of sales channels: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/iYas0CnR?version=v20240601
		* DELETE - Remove collection from sales channels: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/gl3SBo4h?version=v20240601
* Influencer (Affiliate, promoter of products)
	WEBSITE (TODO)
	* GET - Query products of sales channels
	* GET - Query sales channels specify collection Product Id: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/QYddvv3s?version=v20240601
* Customer (Purchaser of Products)
	*

## Setup Personalized Websites (

1. Create storefront oauth app when influencer installs app: POST https://open.shopline.io/v1/storefront/oauth_applications

### Select Product Categories

1. Get list of categories to display to influencer
2. When influencer selects a product category, get the collection_id, and store in db
3. If influencer has selected 10 product categories:
	1. Disable adding new product categories
	2. Display message must remove one before adding another
	3. If influencer removes a product category, toggle ability to add product category 
