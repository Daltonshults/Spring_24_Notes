<h1 align='center'>Getting The Swagger Documentation</h1>
The swagger documentation should not be present within the production environment, but it should be available in your dev environment. To do this you need to follow a couple of quick steps that will allow you to access it.

**Steps:**
1.  Uncomment the swagger endpoints. These are located in the `/algorhythms/urls.py` file. 
	* `path('swagger<format>/', schema_view.without_ui(cache_timeout=0), name='schema-json')`
	* `path('swagger/', schema_view.with_ui('swagger', cache_timeout=0), name='schema-swagger-ui')`
	* `path('redoc/', schema_view.with_ui('redoc', cache_timeout=0), name='schema-redoc')`
2. In the same `/algorhythms/urls.py` file you should change the permission class located in the `schema_view` at the top of the file to `permissions.AllowAny`
3. Start the server by running `python3 manage.py runserver` within the same directory as `manage.py` 
4. Use a browser to find the swagger endpoints, I used `http://localhost:8000/swagger`
5. Set `DEBUG=True` in the `webserver/settings.py` file

<h3 align='center'>Getting Authentication Working</h3>
The authentication uses a JWT. You need to get this from the server in order to be able to test the endpoints in the swagger view. To do this add a print statement to the `/token/` view that prints the token to your terminal. Once you have the token you can login to the swagger authentication system. You need to enter `Bearer <your token>` into the authentication window. Once you have done this you should be able to access all the endpoints that require a token.