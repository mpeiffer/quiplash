# Quiplash Replacement
[![build](https://travis-ci.com/yodigi7/quiplash.svg?branch=master)](https://travis-ci.com/yodigi7/quiplash.svg?branch=master)
[![java](https://img.shields.io/badge/java-v8-blue.svg)](https://img.shields.io/badge/java-v8-blue.svg)
[![spring](https://img.shields.io/badge/spring-v5.1.5-blue.svg)](https://img.shields.io/badge/spring-v5.1.5-blue.svg)
[![vue](https://img.shields.io/badge/vue-v2-blue.svg)](https://img.shields.io/badge/vue-v2-blue.svg)
[![angular](https://img.shields.io/badge/angular-v7-blue.svg)](https://img.shields.io/badge/angular-v7-blue.svg)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

First order of business is to come up with a good name, any ideas?

## Quickstart
In order to access the GameMaster (the shared screen for all contenders) go to: https://yodigi7.github.io/quiplash/gamemaster/. The access point for each contender is https://yodigi7.github.io/quiplash/contender/. Give it a few seconds to boot up as it is likely sleeping on Heroku, it should take ~30 seconds for the server to spin up and start working.

## Project Explained
So as you guys should know by the current title this is meant to be a free open source version of quiplash. The overall architecture is
a backend that keeps track of all the game data. It then supplies that data to two frontends, one of which is the main/common screen that
all players use in the game. The other is the view for each individual contender to enter their specific data.
I currently have it setup in 3 sections:

### Backend
Purpose: supplies REST API services and keeps track of the game data
* written in Java
* Using SpringMVC and JPA
* Stores the data in an H2 in-memory database.

### GameMaster
Purpose: Showing the main/common screen
* written in Vue or Angular 7
* uses axios for HTTP REST API calls
* shows the lobby as people join
* shows the answers to vote on
* shows the voting results
* shows the final game results

### Contender
Purpose: The view for each of the contenders
* written in Vue or Angular 7
* uses axios for HTTP REST API calls
* shows the prompts for answers
* allows voting for answers

## Prerequisites
* Java
* maven
* npm
* node
* axios

## Running in the Dev environment
Currently the only available environment

### Backend
Run the Backend first to get it to run on port 8080 for easier setup with the two frontends. To run just load the 
project into an IDE such as IntelliJ with the project SDK setup and hit run to run the main file 
(Backend/src/main/java/com/yodigi/quiplash/QuiplashApplication.java).

### GameMaster
**Currently doesn't work, use the Angular frontend equivalent**

Setup whatever access point the location will be for the backend. It will likely be `http://localhost:8080` and set the 
.env.dev file
`VUE_APP_BACKEND_BASE_URL` to that value.

From the main folder (QuiplashGameMaster) then run the the following command in the commandline:

`npm run serve -- --mode dev`

Then to access the resulting frontend enter the URL specified in the console to your normal web browser.

It will display in the console but it will most likely be `http://localhost:8081`

### gamemaster-angular
Setup whatever access point the location will be for the backend. It will likely be `http://localhost:8080` and set the
environment.ts file `baseUrl` to this value. The environment.ts file can be found in the 
`quiplash-gamemaster-angular\src\environments` folder

From the main folder (quiplash-gamemaster-angular) then run the the following command in the commandline:

`ng serve -o`

This command will automatically open the browser and serve the Angular application to it.

### Contender
**Currently doesn't work, use the Angular frontend equivalent**

Setup whatever access point the location will be for the backend. It will likely be `http://localhost:8080` and set the 
.env.dev file
`VUE_APP_BACKEND_BASE_URL` to that value.

From the main folder (QuiplashGameMaster) then run the the following command in the commandline:

`npm run serve -- --mode dev`

Then to access the resulting frontend enter the URL specified in the console to your normal web browser.

It will display in the console but it will most likely be `http://localhost:8082`

### contender-angular
Setup whatever access point the location will be for the backend. It will likely be `http://localhost:8080` and set the
environment.ts file `baseUrl` to this value. The environment.ts file can be found in the 
`quiplash-contender-angular\src\environments` folder

From the main folder (quiplash-contender-angular) then run the the following command in the commandline:

`ng serve -o --port 4201`

This command will automatically open the browser and serve the Angular application to it.

The reason for the extra `--port` argument is because it will try to default to the 4200 port which is already being
used by the gamemaster which will then give an error so this will instead open it on the 4201 port.

## Running the tests
Using the commandline, enter into the Backend directory.

From there, enter the command `mvn test` which will run all current tests and return the results.

We are still in the process of writing tests for the frontend.

## Contributing
Feel free to help contribute to this project in any way, be sure to check out open issue and contact me to help get you 
up and running if you are a beginner.

## Authors
yodigi7 - Anthony Buchholz

## License
GPLv3
