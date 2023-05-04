# PeopleSense-Proj
![Project Logo](https://github.com/GShatrawJr/CSC131-CalTrans-Project/blob/a6ff61eb07f03abcc1cef30f093efeb5f0c5a77c/Resources/PeopleSense%20Logo.png)

1. Level 1 item
    1. Level 2 item
        * Level 3 bullet
        * Level 3 bullet
            1. Level 4 item
            2. Level 4 item
    2. Level 2 item
        * Level 3 bullet
        * Level 3 bullet
2. Another level 1 item
    1. Level 2 item
        * Level 3 bullet
        * Level 3 bullet
    2. Level 2 item




# Project Description
The new PeopleSense Dashboard 2.0 website brings train occupancy utilization data from IoT sensors installed on trains through our backend system and brings it to the user in the form of easy-to-read data visualizations: historical time series line charts, bar graphs, gauges, and Maps with GPS location data for each train. With this new powerful visual data system, stakeholders can easily see the utilized capacity of the trains, both in real time and historical data, and use this to make data driven decisions about resource allocation in order to serve the community best with the often too limited resources available. The use of AWS technologies such as Cognito and Amplify allow the client to create and manage separate user groups and access controls for each group.  This ensures that each agency-based user group can only access their own agency data yet allows the client to unify the previously separate proof of concept websites for each agency into a singular powerful more fully featured and robust website, and codebase, for the client to maintain.  This makes adding features, maintaining features, and even adding new agencies far simpler going forward. 


# How it works

<img src="/diagram/Project Architecture Diagram.png"/>

1.	Occupancy data are obtained and stored into AWS dynamoDB after going through a PeopleSense proprietary network.  
2.	The PeopleSense Dashboard 2.0 (this project) software queries the PeopleSense API on an interval set by the user per chart to retrieve data, current or historical based on user settings and chart type, regarding train occupancy as well as latitude and longitude information used to plot the location of the train on the Google Map API panel.  
3.	The data is then pushed to Influx which is housed in a Docker container for ease of deployment and portability.  
4.	Lastly, the PeopleSense Dashboard 2.0 front end will access and display various charts in the dashboard tiles for an improved user experience.

# User Experience


1. Users use the Log in Page to create their account, log in with an existing account, or in the case of a forgotten password to begin the recovery process, or Continue as Guest with limited access to only current capacities.
    * PeopleSense Dashboard 2.0 Home Page  
    <img src="/diagram/Log In Page.png"/>
2. Users are restricted by their access through their assigned user group, and start with a blank Dashboard.
    * Blank Dashboard  
    <img src="/diagram/Sample Empty Dashboard.png"/>
3. Users can customize the dashboard to see specific trains, time periods, and a train's GPS location on the Google Maps API pane using the Left Side Pill.
    * Side Pill  
    <img src="/diagram/Left Side Pill.png"/>  
4. Choosing the top icon opens the Chart Maker.
    * Chart Choices(top to bottom): Line Chart, Bar Chart, Gauge  
    <img src="diagram/Chart Creator.png"/>  
5. Choices (top to bottom): Line Chart, Bar Chart, Gauge. Picking one opens an empty panel.
    * Empty Panel  
    <img src="/diagram/Blank Chart.png"/>
6. Users can customize the dashboard to see specific trains, time periods, and a train's GPS location on the Google Maps API pane using the Ride Side Panel.
    1. Super Admins can Change Agency using the Agency Dropdown  
    	  <img src="/diagram/Chart Configuration Agency.png"/>
    2. The Train Dropdown selects the train to show in the unconfigured panel, filtered by the route selector to the right of the dropdown, which differs based on agency route groupings.
	  <img src="/diagram/Chart Configuration Trains.png"/>  
    3. The User can change how often the panel updates its data using the Refresh Rate dropdown.
    	  <img src="/diagram/Chart Configuration Refresh.png"/>  	
    4. The middle Button on the Left Side Pill creates an empty Map.
    	  <img src="/diagram/Map Unconfigured.png"/>
    5. The User then uses he Right Side Panel to configure the map, just as with a chart.
    	  <img src="/diagram/Map Configured.png"/>
7. They can create multiple charts, move them, resize them, and the PeopleSense 2.0 Dashboard will save their layout between log in sessions, so they can resume where they left off without having to reconfigure their dashboard.
    * Configured Dashboard  
    <img src="/diagram/Sample Filled Dashboard.png"/>    	



# Utilities
## devfilter.py
Used for testing Bluetooth device filtering locally. Devices are blacklisted based on the UUIDs they provide. See https://www.bluetooth.com/specifications/assigned-numbers/ for lists of UUIDs and their meaning.

To use, first ensure you have Python 3.10 or later installed, along with the `bluez` and `bluez-utils` packages. Then run `python devfilter.py path_to_blacklist`, where `path_to_blacklist` is a text file listing blacklisted UUIDs. An example is provided in `utils/devfilter/blacklist.txt`. The program will scan for nearby Bluetooth devices and keep a running count of blacklisted devices.
# Timeline

<img src="/diagram/timeline.png"/>

# Testing (Coming Soon!)
