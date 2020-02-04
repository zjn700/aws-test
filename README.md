# AwsTest

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 8.3.24.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).


---

## A few other tasksi had to perform

## On AWS
	- Had to add RAM. 512 MB was too small to compile an Angular app 
		-  had to create an new instance first
		- DigitalOcean process looks easier. May switch later
	- SSH public key from the ipad. This is done when the instance is created
	- SSH rule on port 22 in Security Group
	- UDP rule on ports 60000 - 61000 for MOSH connectivity in Security Group
	- Had to delete the Cloud9 instance. Couldn't connect
	
## On iPad
	- Added the following apps
		- Blink: terminal with SSH and MOSH (for sturdier connections on mobile)
		- Working Copy: git client with an editor
		- Textastic: Code editor with its own terminals and SSH connectivity
	- 
	
## On AWS instance installed
	- nvm (for node and npm)
		curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
	- angular cli
		npm install -g @angular/cli
	- ngrok (to display http site from ng server)
		https://dashboard.ngrok.com/get-started
	- mosh
		https://www.digitalocean.com/community/tutorials/how-to-install-and-use-mosh-on-a-vps
	
## Running Angular app from Ubuntu server
	- This works:
		ng serve --port 4200 --disable-host-check
		
## SSH required a few iterations to get right (royal pain in the ass)
	- Ended up using the keys created on the Blink app
	- Then copied BOTH to the local files in Textasic
	- And uploaded the public key to AWS
	
##  NOTES 
	- Some issues with Blink, mosh, and ngrok
		- ngrok would not run in the background
		- fortunately Blink allows multiple windows, but only one mosh connection
		-  Blink freezes occasionally and leaves a zombie process running on the server. Had to reboot the AWS server to reset
	- It's possible to edit files pulled from Github to Working Copy in Textastic, but then it's a two or three step process to run them on the server: 
		- Switch to WorkingCooy to push the changes to Github.
		- Then switch back to Textastic to merge the changes on Github with the files on the AWS server
		- If watch is not enabled on the ng server, then restart it
	- This is not ideal, but it works!
	