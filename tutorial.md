1. Download
	1. visit http://lsq.io
	2. In the navbar, select "Getting Started"
	3. click "Download Now!"
	
2. Install
	1. drag app to folder to install
	
		>####Tip
		>run app from app directory
		
3. Setup
	1. enter email address
	2. confirm working directory
	3. click "go to App List"
	
4. Create pre-built app
	1. select from list
	2. Run and monitor
	
5. Create a service
	1. Navigate to "Create Service" 
	2. Enter a name for your service
	3. Select "node-micro" from dropdown
	4. Modify port
		- choose a port in 3000 - 4000 range
	5. Post to another service
		>####Tip
		>`config = LSQ.config.get()`
		>
		>`hostnameAndPort = LSQ.services.get(<service name>)`
		> 
		>LINK TO DOCS
		
		- `request.post("http://" + hostnameAndPort + "/" + path, {body})`

7. Deploy (coming soon)
