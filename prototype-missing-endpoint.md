# Prototype Missing API Endpoints
Suppose, during develoment, you identify an essential APl endpoint is missing from SHOPLINE's Developer Portal.

Explain how you would go about prototyping this endpoint, including:

* Defining endpoint requirements (functionality, method, etc.)
* Designing the API interface (URI design, request/response structures)
* Documenting the endpoint for use by the development team


# ASSIGNMENT DELIVERABLE

## Explain how I would approach prototyping a missing API endpoint;

1. I would first check with the Engineering team to determine if API exists, but has not been published, if it does exist unpublished then I would invest time to evaluate the publish readiness of the API:

2. Define endpoint requirements

* Does an object or API Resource already exist for the essential endpoint? If yes, use it. If not, and it is not a reserved keyword or slated for future development per the roadmap, then add it to the API Taxonomy on the roadmap.
* URI design must follow IDIOMATIC best practices, so if it is restful in nature, adhere to resful best practices:
	* Three levels or less deep (for heirarchical objects)
	* /collections/{resource_id}, etc... (up to three deep, but ideally two or less)
	* Implement HTTP verbs properly (do not include actions in PATH)
	* Use Path Variables to contextualize
	* Use Query Parameters on all GET endpoints
	* etc...
* Request/Response structures should be JSON, and the data should be as normalized as possible, but if we have customers who require other request/response structures or formats we could potentially support content negotiation
* I would make sure to include all standard HTTP Error Codes, with detailed descriptions, for things such as missing Path Variable, or invalid Query Parameters/Body Parameters. Additionally, I would include a set of Custom Error Objects unique to this specific API that provides linked-actionable error responses to developers and points them directly to where they can get specific help for that API Resource's exact error state.
* I would use OASv3+ to define the interface of the new API, assign authentication requirements, and to fully document the specifications of the API itself, including any request/response body, path variables, or query parameters...making sure to include reference links wherever possible, and adhering to company's Data & API Governance Policies (or defining those policies if they don't exist). This documentation "could" suffice for the development team, but I don't feel that is satisfactory enough, and I would make sure to include a summary of the new API Resource, what the object represents, how it can/cannot be used, limitations, prerequisites, and include links to existing documentation for the object (if it exists, but the company is not using API-first best practices for product development).
