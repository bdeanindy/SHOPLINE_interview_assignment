# Social Feed Integration and Customization


## APIs Needed

* PUT - Add collection to sales channels: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/L7HL6W0r?version=v20240601
* GET - Query collection of sales channels: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/iYas0CnR?version=v20240601
* DELETE - Remove collection from sales channels: https://developer.shopline.com/docsv2/ec20/cdb180dc069f7d8d6877c0cdffe96f73/gl3SBo4h?version=v20240601


1. Influencers install the sales channel App.
2. Influencers authorize the sales channel application through OAuth 2.0, and the developer obtains a token.
3. The sales channel prompts the influencer to connect their third-party channel account. If the influencer doesn't have an account registered with the third-party platform (e.g., registering a Shopee account), they will be prompted to create an account. This account linking process occurs outside of SHOPLINE and is completed within a pop-up window provided by the third-party channel.
