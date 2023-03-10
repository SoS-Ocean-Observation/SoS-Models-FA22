# Sos Fall 22

Hi In this document , I will summierzie every details for the Project Sos Fall 22, the document will make every details clear for anyone in the team or any future members
------Jordan 


## Setting up the Environment

1. The project is currently requireing the following components: 
	*  AnyLogic Professional Version 8.8.1 [Download Link Attached](https://www.anylogic.com/downloads/)
	* MIT VPN set up for retrieving the license from the server [GuideLine Link](https://ist.mit.edu/prisma/globalprotect)
	* An MIT student id, plus duo security setup
2. Connecting to the mit server
	* Sample connecting page once you start the anylogic application
	![connection](https://user-images.githubusercontent.com/112024195/224403687-c17208f0-191e-46bd-ab34-9e7f7bb3b926.png)
		* url : > aa-anylogic-lic.mit.edu
		* port: > 8443


## Agents
*  The Command Ship
	* The command ship acts as the recharging station and data center for AUVs and UAVs agents to drop their collected data.
	*  State Flow Chart:
	![the command ship state flow chart](https://user-images.githubusercontent.com/112024195/224406542-93bacc56-f6cc-4e04-a570-e6ae914bbd15.JPG)
	* The Variables Stated Under the Command Ship
		* private double[] **currentLocation** : represents the current location in (lon, lat) of the command ship, the variable would be updated once the command ship is assigned and reaches a new destination.
		* private double **speed** : represnets the speed of the command ship in km / h
		* private String **profile** : the commandship profile, define how command ship reacted if there are any scientific events near by or there is none.
	* The Functions Stated Under the Command Ship
		* public void **setCurrentLocation( double[] inputCurrentLocation )**: set the current location of the command ship
		* public double[] **getCurrentLocation()**: get the current location of the command ship
		* public void **setSpeed( double inputSpeed )**: set the speed of the command ship
		* public double **getSpeed() **: get the speed of the command ship
		* public void **setProfile( String profile )**: set the profile the command ship
		* public String **getProfile()**: get the profile of the command ship


