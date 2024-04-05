Dalton Shults 
Prof. Hall 
CS 493 
7 April 2024 

# API Endpoints Design Documentation

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
		"number": "123-456-7890",
		"category": "Business Category",
		
		// Optional Fields
		"url": "www.business.com",
		"email": "bus@business.com"
	}
	
Response Body: N/A
Response Status Code: 200 OK
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
		"number": "123-456-7890",
		"category": "Business Category",
		"url": "www.business.com",
		"email": "bus@business.com"
	}

Response body: N/A
Response Code: 200 OK
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
		"number": "123-456-7890",
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
Response Code: 200 OK
```
Notes: Authentication needs to verify that the user is the same user that created the business, if it is not the same user you would get an error code

Removing Business Not Owned By User:
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
				"number": "123-456-7890",
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
				"number": "123-456-7890",
				"category": "Business Category",

				// Optional
				"url": "www.business.com",
				"email": "bus@business.com"
			},
			...
		]
	}
Response Code: 200
```

**Get Specific Business**
```request_and_response
Request: GET /business/{businessID}
Request Body: N/A

Response body: 
	{
		// Required
		"name": "Business Name",
		"address": "1234 Business Way 12345"
		"city": "Business City",
		"state": "BS",
		"zip": "12345",
		"number": "123-456-7890",
		"category": "Business Category",
		
		// Optional
		"url": "www.business.com",
		"email": "bus@business.com"
	}
Response Code: 200 
```
## Reviews:

User adds a review:
```request_and_response
Request: /POST /reviews/{businessID}
Request Body:
	{
		// Required
		"star": 0-5,
		"dollarSign": 1-4, 

		// Optional
		"review": "This restaurant was del..."
	}

Response body: N/A
Response Code: 200 OK
```
Note: Using post because I don't want them to be able to write two reviews.

Delete User Review 
```request_and_response
Request: /DELETE /reviews/{businessID}
Request Body: N/A

Response body: N/A
Response Code: 200 OK
```

Delete User Review Incorrect User
```request_and_response
Request: /DELETE /reviews/{businessID}
Request Body: N/A

Response body: 
	{
		"error": "Forbidden",
		"message": "You do not have permission"	
	}
Response Code: 403 Forbidden
```

Listing All Review From a User 
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
			}
	}
 
Response Code: 200
```

##### Photos:
User adds a photo
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
	
Response Code: 200
```

User Deletes a Photo
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
	
Response Code: 200
```
##### Users
List All User's Businesses
```request_and_response
Request: GET /users/businesses?page={pageNumber}
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
				"number": "123-456-7890",
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
				"number": "123-456-7890",
				"category": "Business Category",

				// Optional
				"url": "www.business.com",
				"email": "bus@business.com"
			},
			...
		]
	}
Response Code: 200
```

List All Users Photos
```request_and_response
Request: GET /users/photos?page={pageNumber}
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
Response Code: 200
```