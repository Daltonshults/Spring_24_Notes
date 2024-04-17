Dalton Shults 
Prof. Hall 
CS 493 
7 April 2024 
<h1 align="center">API Endpoints Design Documentation</h1>

## Business:
**Adding a Business:**
```request_and_response
Request: POST /businesses
Request Body:
	{
		// Required Fields
		"name": "Business Name",
		"address": "1234 Business Way 12345"
		"city": "Business City",
		"state": "BS",
		"zip": "12345",
		"phone": "123-456-7890",
		"category": "Business Category",
		
		// Optional Fields
		"url": "www.business.com",
		"email": "bus@business.com"
	}
	
Response Body: N/A
Response Status Code: 201 Created
```

**Modifying a Business:**
```request_and_response
Request: PATCH  /businesses/{businessID}
Request Body:
	{
		// Optional Fields
		"name": "Business Name",
		"address": "1234 Business Way 12345"
		"city": "Business City",
		"state": "BS",
		"zip": "12345",
		"phone": "123-456-7890",
		"category": "Business Category",
		"url": "www.business.com",
		"email": "bus@business.com"
	}

Response body: N/A
Response Code: 202 Accepted
```

**Modifying a Business Not Owned By User:**
```request_and_response
Request: PATCH  /businesses/{businessID}
Request Body:
	{
		// Optional Fields
		"name": "Business Name",
		"address": "1234 Business Way 12345"
		"city": "Business City",
		"state": "BS",
		"zip": "12345",
		"phone": "123-456-7890",
		"category": "Business Category",
		"url": "www.business.com",
		"email": "bus@business.com"
	}

Response body: 
	{
		"error": "Forbidden",
		"message": "You do not have permission"	
	}
Response Code: 403 Forbidden
```

**Removing a Business:**
```request_and_response
Request: DELETE /businesses/{buisnessID}
Request Body: N/A

Response body: 
	{
		"name": "Business Name"
		"deletion_status": true
	}
Response Code: 204 No Content
```
**Notes**: Authentication needs to verify that the user is the same user that created the business, if it is not the same user you would get an error code

**Removing Business Not Owned By User:**
```request_and_response
Request: DELETE /businesses/{businessID}
Request Body: N/A

Response body: 
	{
		"error": "Forbidden",
		"message": "You do not have permission"	
	}
Response Code: 403 Forbidden
```

**Getting a List of Businesses:**
```request_and_response
Request: GET /businesses?page={pageNumber}
Request Body: N/A

Response body: 
	{
		"pageNumber": 0,
		"totalPages": 15,
		"pageSize": 10,
		"totalCount": 150,
		"businesses": [
			{
				// Required
				"name": "Business Name 0",
				"address": "1234 Business Way 12345"
				"city": "Business City",
				"state": "BS",
				"zip": "12345",
				"phone": "123-456-7890",
				"category": "Business Category",
				
				// Optional
				"url": "www.business.com",
				"email": "bus@business.com"
			},
			{
				// Required
				"name": "Business Name 1",
				"address": "1234 Business Way 12345"
				"city": "Business City",
				"state": "BS",
				"zip": "12345",
				"phone": "123-456-7890",
				"category": "Business Category",

				// Optional
				"url": "www.business.com",
				"email": "bus@business.com"
			},
			...
		]
	}
Response Code: 200 OK
```

**Get Specific Business**
```request_and_response
Request: GET /businesses/{businessID}
Request Body: N/A

Response body: 
	{
		// Required
		"name": "Business Name",
		"address": "1234 Business Way 12345"
		"city": "Business City",
		"state": "BS",
		"zip": "12345",
		"phone": "123-456-7890",
		"category": "Business Category",
		
		// Optional
		"url": "www.business.com",
		"email": "bus@business.com"
	}
Response Code: 200 OK
```

**List All  Businesses Owned by User**
```request_and_response
Request: GET /businesseses/user?page={pageNumber}
Request Body: N/A

Response body: 
	{
		"pageNumber": 0,
		"totalPages": 1,
		"pageSize": 10,
		"totalCount": 20,
		"businesses": [
			{
				// Required
				"name": "Business Name 0",
				"address": "1234 Business Way 12345"
				"city": "Business City",
				"state": "BS",
				"zip": "12345",
				"phone": "123-456-7890",
				"category": "Business Category",
				
				// Optional
				"url": "www.business.com",
				"email": "bus@business.com"
			},
			{
				// Required
				"name": "Business Name 1",
				"address": "1234 Business Way 12345"
				"city": "Business City",
				"state": "BS",
				"zip": "12345",
				"phone": "123-456-7890",
				"category": "Business Category",

				// Optional
				"url": "www.business.com",
				"email": "bus@business.com"
			},
			...
		]
	}
Response Code: 200 OK
```
**Note:** From "Photos" portion of the requirements

****
## Reviews:
User adds a review:
```request_and_response
Request: POST /reviews/{businessID}
Request Body:
	{
		// Required
		"star": 0-5,
		"dollarSign": 1-4, 

		// Optional
		"review": "This restaurant was del..."
	}

Response body: N/A
Response Status Code: 201 Created
```
**Note**: Using post because I don't want them to be able to write two reviews.

**Modify User Review:**
```request_and_response
Request: PATCH /reviews/{businessID}
Request Body:
	{
		// All fields technically optional, but one field should be updated
		"star": 0-5,
		"dollarSign": 1-4, 
		"review": "This restaurant was del..."
	}

Response body: N/A
Response Code: 202 Accepted
```

**Delete User Review** 
```request_and_response
Request: DELETE /reviews/{businessID}
Request Body: N/A

Response body: N/A
Response Code: 204 No Content
```

**Delete User Review Incorrect User**
```request_and_response
Request: DELETE /reviews/{businessID}
Request Body: N/A

Response body: 
	{
		"error": "Forbidden",
		"message": "You do not have permission"	
	}
Response Code: 403 Forbidden
```

**Listing All Reviews From a User** 
```request_and_response
Request: GET /reviews
Request Body: N/A

Response Body:
	{
		"pageNumber": 0,
		"totalPages": 15,
		"pageSize": 10,
		"totalCount": 150,
		"reviews": [
			{
				// Required
				"business": "/businesses/{businessID}"
				"star": 0-5,
				"dollarSign": 1-4, 
	
				// Optional
				"review": "This restaurant was del..."
			},
			{
				// Required
				"business": "/businesses/{businessID}"
				"star": 0-5,
				"dollarSign": 1-4, 
	
				// Optional
				"review": "This restaurant was del..."
			},
			{
				...
			}]
	}
 
Response Code: 200 OK
```

****
## Photos:
**User Adds a Photo:**
```request_and_response
Request: POST /photos
Request Body: 
	{
		"url": "photo.url/123",
		"caption": "Photo Caption."
	}

Response body:
	{
		"photoID": 123
	}
	
Response Code: 201 Created
```
 **Note:** Might not want to return photo ID, status code may be enough
 
**User Deletes a Photo:**
```request_and_response
Request: DELETE /photos/{photoID}
Request Body: 
	{
		"url": "photo.url/123",
		"caption": "Photo Caption."
	}

Response body: N/A or 
	
	{
		"photoID": 123
	}
	
Response Code: 204 No Content
```
**Note:** Might not want to return photo ID, status code may be enough

**User Deletes a Photo Incorrect User:**
```request_and_response
Request: DELETE /photos/{photoID}
Request Body: 
	{
		"url": "photo.url/123",
		"caption": "Photo Caption."
	}

Response body: N/A or 
	
	{
		"error": "Forbidden",
		"message": "You do not have permission"	
	}
	
Response Code: 403 Forbidden
```

**List All Users Photos:**
```request_and_response
Request: GET /photos?page={pageNumber}
Request Body: N/A

Response body: 
	{
		"pageNumber": 0,
		"totalPages": 1,
		"pageSize": 10,
		"totalCount": 20,
		"photos": [
			{
				"photoID": 123,
				"url": "photo.url/123",
				"caption": "Photo Caption."
			},
			{
				"photoID": 124,
				"url": "photo.url/123",
				"caption": "Photo Caption."
			},
			...
		]
	}
Response Code: 200 OK
```

****