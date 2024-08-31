2024/07/18 14:41
Status: #idea
Tags:

# Flask Server

*Just some notes to compile my thoughts on the features and capabilities that this server should have.*

## Features


### UI

**Tailwind CSS**

- Upload Files Button
	- Text
	- CSV
	- JSON
	- Option to update, create, or delete index
	- Maybe a feature to keep file stored on server in a minimal db like sqlalchemy, backlogged

- File Preview | Modal
	- Text
		- View text to confirm it was uploaded correctly
	- CSV
		- View fields to confirm values are appropriately assigned
	- JSON
		- View fields to confirm values are appropriately assigned
	- Maybe a feature to update values within the app, but this will be backlogged.

- POST file to Elastic Button
	- View POST request result
		- Upon success a link to kibana dashboard will be created.
		- Upon failure elastic failure response will be displayed.


### API/Back-end

- src folder
	- /public
		- Contains any images used by server
	- /scripts
		- Might want some js scripts to help display info if I'm unable to do it with python
	- /templates 
		- Will contain all html files that are supported by jinja templating
	- views.py
		- Contains all routes with function calls needed to display page information
	- api.py
		- All routes that will make post or get requests to elastic search to upload or pull information.
	-  _\_init__.py 
		- Instantiates our app with the appropriate settings
		- Initially site will be ran in debug mode
			- This is insecure and should be replaced with proper ssl/tls config

### Authentication

**Backlogged feature as we would need to implement db but should probably be added**

- Use werkzeug.security


---
# References
