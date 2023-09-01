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
  		* private boolean **isAssigned** : indicates if the command ship is moving towards the target location ( center of the mass ).
    		* private double[] **movingTarget** : represents the target location that the command ship is pursuing.
      		* private ArrayList<Agent> **uavDocked** : represents any docked uav holding by the command ship, useful under the profile of center of mass.
        	* private ArrayList<Agent> **auvDock** : represents any docked auv holding by the command ship, useful under the profile of center of mass.
         	* private ArrayList<Agent> **uavReturn** : represents any returning uav heading to the command ship, making sure they change their destination when the center of mass is changed.
          	* private ArrayList<Agent> **auvReturn** : represents any returning auv heading to the command ship, making sure they change their destination when the center of mass is changed.
          	* private ArrayList<Science> **activeScience** : represents any active science at the current time, the center of mass is recalculated whenever a science event is added or removed.
          	* private ArrayList<GISPoitn> **linePlanning**: an arrayList contains all the GIS Points that the command ship needs heading in order to arrive at the destination.
	* The Functions Stated Under the Command Ship
		* public void **setCurrentLocation( double[] inputCurrentLocation )**: set the current location of the command ship
		* public double[] **getCurrentLocation()**: get the current location of the command ship
		* public void **setSpeed( double inputSpeed )**: set the speed of the command ship
		* public double **getSpeed()**: get the speed of the command ship
		* public void **setProfile( String profile )**: set the profile the command ship
		* public String **getProfile()**: get the profile of the command ship
  		* public boolean **getAssigned()**: check if the command ship is assigned or not.
    		* public void **setAssigned(boolean newAssignedStatus)**: set the assigned status of the command ship.
      		* public void **getMovingTarget()**: get the moving target of the command ship in the lat/lon format.
        	* public void **setMovingTarget(double[] inputCurrentTarget)**: set the moving target of the command ship in the lat/lon format.
         	* public void **addDockedUAV(Agent incoming_uav)**: add an uav to dock at the command ship.
          	* public void **removeDockedUAV(Agent outcoming_uav)**: unload an uav from the command ship.
          	* public void **addDockedAUV(Agent incoming_auv)**: add an auv to dock at the command ship.
          	* public void **removeDockedAUV(Agent outcoming_auv)**: unload an auv from the command ship.
          	* public void **addReturnUAV(Agent return_uav)**: add an UAV agent to the arraylist when the agent starts heading back to the command ship.
          	* public void **removeReturnUAV(Agent return_uav)**: once an UAV agent arrives at the command ship, remove it from the returning list of uav.
          	* public void **addReturnAUV(Agent return_auv)**: add an AUV agent to the arraylist when the agent starts heading back to the command ship.
          	* public void **removeReturnAUV(Agent return_auv)**: once an AUV agent arrives at the command ship, remove it from the returning list of auv.
          	* public void **addActiveScience(Science science)**: add an active/valid science event to the list to calculate the center of mass.
          	* public void **removeActiveScience(Science science)**: remove an deactive science event from the list to calculate the center of mass.
          	* public void **move_center_of_profile()**: recalculate the center of mass and assign its value to the variable "center"
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
		* private String **name**: the name of the scientific event。
  		* private boolean **status**:the status of the Science, used for command ship to determine if the science is going to be removed in the active-science arrayList or to be added.
    	* The Functions stated Under the Science:
     		* public void **setDuration(double duration)**: set the duration in hours for an scientific event.
       		* public double **getDuration()**: get the duration in hours of an scientific event.
         	* public void **setDataVolume(double dataVolume)**: set the data volume of an scientific event.
          	* public double **getDataVolume()**: get the data volume of an scientific event.
          	* public void **setType(String type)**: set the type of the scientific event.
          	* public String **getType()**: get the type of the scientific event.
          	* public void **setLocation(double lon, double lat)**: set the location of the scientific event.
          	* public void **setLocation(double[] location)**: set the location of the scientific event.
          	* public double[] **getLocation()**: get the location of the scientific event.
          	* public void **setStatus(boolean status)**: set the status of the scientific event.
          	* public boolean **getStatus()**: return the status of the scientific event.
          	* public void **setScienceName(String name)**: set the science name
          	* public String **getScienceName()**: get the science name
	* The State Flows stated Under the Science:
		* **enter**: the starting point of the flow, when the agents are arriving at the science location, they would enter the state. 		
    		* **collectedData**: the starting point of the extraction process.
      			*  Queue capacity: 100
         		*  Delay time: agent.getCurrentScience().getDataVolume()/agent.getCollectionRate() // the collecion time for this agent & the scientific event
           		*  On at exit: agent.setCurrentDataStorage(agent.getCurrentDataStorage() + agent.getCurrentScience().getDataVolume());
	  	* **exit** : the end of collection process.
   			*  On exit: send("collected completed",agent); // send the message to the agent and the agent moves to the next stage (returning to the commandhship/Pearl)
  
*  The Agent:
	* The Agent type is the parental class of UAV and AUV.
	* The variables stated under the Agent:
 		* private double[] **currentLocation**: the current location of the agent
   		* private String **type**： the type of the agent, UAV or AUV.
     		* private double **speed** ： the speed of the agent.
       		* private double **batteryCapacity**: the battery capacity of the agent.
         	* private double **rechargeRate**: the recharge rate of the battery when recharging.
	        * private double **dischargeRate**: the discharge rate of the battery while not recharing.
         	*  
 	


Center of mass, 

shallow water, deep water, 

shallow = aerial = UAV
deep = underwater = AUV

shallow water event: only UAV assigneed
deep water : only AUV assignmed 

shallow water AUV left, consider as missed 

fixed, random, center of mass

data storage never resets. 
