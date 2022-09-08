# Introduction

We are actively seeking accomplished programmers to join our growing team and actively participate in design, architecture, implementation and deployment of web based applications.

The purpose of this project is to test a candidate's programming aptitude, style and knowledge of best practices. 

The following challenge should be built using PHP ^8.1 and Symfony ^6.1 to test your knowledge using MVC frameworks and OOP methodologies.

## Scenario

Design and develop a Symfony Project, which uses a console command to parse a GTFS Real-time TripUpdates feed in JSON format to an Object, then store the `TripUpdate` entity with it's unique identifier, and also each `StopTimeUpdate` within it's own entity which is related to the TripUpdate parent using Doctrine ORM and Symfony Entities.

Use the GTFS-RT feed provided in the instructions below.

an example command will be as follows:

`php bin/console data:parse-feed`

Extra Credit example:

`php bin/console data:parse-feed {{url}} --apiKey={{apiKey}} --format=json`

`Extra Credit:` Running this command should output successful indicators of each step to the terminal using `SymfonyStyle`, the result should be each TripUpdate and related StopTimeUpdates being stored within a database and easily accessible via an API `GET` request.

*Existing records within the database should be skipped, and new ones should be appended.*


## Instructions

*DO NOT Fork This Repository*

Make use of GitHub for development: commits, PRs, issues

Create a private GitHub, GitLab or BitBucket repository for this coding challenge.

Utilize a database or service to store information using Doctrine ORM.

Provide documentation for deployment, if we cannot get the project up and running based on the README, we will not acknowledge the challenge.

1. Use the Swiftly API provided in this repository to parse and store TripUpdates and the related StopTimeUpdates within a database.
2. Create an Entity for the TripUpdates with relational properties to a StopTimeUpdate entity that relates the StopTimeUpdates with the corresponding Trip.
3. Create a console command that parses the TripUpdates file, iterates through each TripUpdate, and stores the data for each `TripUpdate` and `StopTimeUpdate` as a new row in the database, where the StopTimeUpdates are related to the parent TripUpdate.
4. When storing the TripUpdates, make sure to also store the ID of each entity.
5. *Existing records within the database should be skipped, and new ones should be appended.*
6. Make an API endpoint in the same application that returns up to 100 results from the database.
7. Must be able to query the endpoint with the following URL: `GET /real-time/trip-updates` and return the stored TripUpdates in JSON similar to the Swiftly API response.
8. Use the following API endpoint and API Key to retrieve the Trip Updates Feed:
   -  Endpoint: `https://api.goswift.ly/real-time/vta/gtfs-rt-trip-updates`
   -  API Key: `59af72683221a1734f637eae7a7e8d9b`
   -  format: json
   -  Full Endpoint: https://api.goswift.ly/real-time/vta/gtfs-rt-trip-updates?apiKey=59af72683221a1734f637eae7a7e8d9b&format=json
   -  Documentation: https://swiftly-inc.stoplight.io/docs/standalone/99a5881ffdb83-gtfs-rt-trip-updates
9. Must be able to run this project using `symfony server:start`
10. Commit often and frequently, use branches, issues, and pull requests where needed.
11. DO NOT USE code from stackoverflow or other websites, this code must be your own.

### Extra Credit

1. Add arguments to the command for the API endpoint with arguments for the API key and GET parameters. (ex: format=json), which is then used to pull the TripUpdates feed.
2. Create PHPUnit tests for the command and supporting methods.
3. Remove expired TripUpdates every time the command is executed.
4. Deploy to the cloud using `bref.sh` and the serverless.com (serverless) framework.


### Requirements
- PHP ^8.1
- Symfony ^6.0|^6.1
- MySQL ^5.7
- Doctrine ORM

## Resources
- https://developers.google.com/transit/gtfs-realtime/reference
- https://swiftly-inc.stoplight.io/docs/standalone/99a5881ffdb83-gtfs-rt-trip-updates
- https://symfony.com/doc/current/console/style.html
- https://developers.google.com/protocol-buffers/docs/reference/php-generated
- https://developers.google.com/protocol-buffers/docs/downloads
