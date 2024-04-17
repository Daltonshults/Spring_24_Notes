##### Business:
* Add: /POST
	* Required request fields:
		* name
		* street address
		* city
		* state 
		* zip
		* phone number
		* business category
	* Optional request fields"
		* Website
		* Email
* Modify: /PATCH
	* Required Path Parameters:
		* `BusinessID`
	* Optional Fields:
		* name
		* street address
		* city
		* state 
		* zip
		* phone number
		* business category
		* Website Email
* Remove: /DELETE 
* Get List: /GET
* Get specific business: /GET
##### Reviews
* Add: /POST (MOST 1 REVIEW FOR A SINGLE BUSINESS)
	* Required Fields:
		* star: A rating from 0-5
		* dollar sign: a price estimate from 1-4
	* Optional Fields:
		* Written review
* Modify: /PATCH
* Delete: /DELETE
* List all: /GET
##### Photos
* Upload: /POST
* Delete: /DELETE
##### Users
* List owned businesses: /GET
* List all photos: /GET

Beej Question: 

Hey Beej, I was designing the API endpoints for Project 1 in CS 493, and was wondering about identifying a specific user. Can I assume that our authentication methods allow me to identify the user that is logged in? I am curious about this because when I am listing all of the a specific user has written I either need a `userID` within the path. For example, `GET reviews/{userID}`, but If I can assume authentication can identify the user, I can do something like this, `GET /reviews` and assume the user will be able to be identified by the authentication system.

