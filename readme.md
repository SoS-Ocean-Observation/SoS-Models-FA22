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
		* private double **speed** : represents the speed of the command ship in km / h
		* private String **profile** : the commandship profile, define how command ship reacted if there are any scientific events near by or there is none.
	* The Functions Stated Under the Command Ship
		* public void **setCurrentLocation( double[] inputCurrentLocation )**: set the current location of the command ship
		* public double[] **getCurrentLocation()**: get the current location of the command ship
		* public void **setSpeed( double inputSpeed )**: set the speed of the command ship
		* public double **getSpeed()**: get the speed of the command ship
		* public void **setProfile( String profile )**: set the profile the command ship
		* public String **getProfile()**: get the profile of the command ship
		* private ArrayList<GISPoint> **checkCrossingIslands(GISRoute Route)**: check the input route if it pass through any indicated islands, return an arraylist of crossed islands in gispoint format.
		* private String **checkdirection(GISPoint source, GISPoint target)**: check the direction from source to target, "horizontal - north/south", "verical - east/west"
		* private ArrayList<GISPoint> **calculateLineSegments(GISPoint source, GISPoint Target, ArrayList<GISPoint> crossedIslands, String direction)**: calculate the new route if the directed route crossed any islands, the new line segments is sorted based on the distance to the source.
		* private ArrayList<GISPoint> **sortedHashMap (HashMap<GISPoint,Double> hm)**: helper function for sorting the line segments based on the distance from segments to the source
	* Logic behind generating the route(**TODO**)
* The Science
	* The science type agent represents science events shown on the map, it can be fault, front, and seamount scientific events (parent type)
	* The Variables Stated Under the Science
		* private double **Duration**: represents the duration of the scientific event will last in hours
		* private double **Volume**: represents how much data can be collected by agents from this scientific event
		* private String **type**: represents the type of this scientific event, it can be seamount, fault, and front
		* private double[] **location**: represents the location in (lon,lat) of the scientific event
		* private String **name**: the name of the scientific event


Center of mass, 

shallow water, deep water, 

shallow = aerial = UAV
deep = underwater = AUV

shallow water event: only UAV assigneed
deep water : only AUV assignmed 

shallow water AUV left, consider as missed 

fixed, random, center of mass

data storage never resets. 