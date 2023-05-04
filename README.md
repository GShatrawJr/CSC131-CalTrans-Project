# PeopleSense-Proj
![Project Logo](https://github.com/GShatrawJr/CSC131-CalTrans-Project/blob/a6ff61eb07f03abcc1cef30f093efeb5f0c5a77c/Resources/PeopleSense%20Logo.png)

# Project Description
The new PeopleSense Dashboard 2.0 website brings train occupancy utilization data from IoT sensors installed on trains through our backend system and brings it to the user in the form of easy-to-read data visualizations: historical time series line charts, bar graphs, gauges, and Maps with GPS location data for each train. With this new powerful visual data system, stakeholders can easily see the utilized capacity of the trains, both in real time and historical data, and use this to make data driven decisions about resource allocation in order to serve the community best with the often too limited resources available. The use of AWS technologies such as Cognito and Amplify allow the client to create and manage separate user groups and access controls for each group.  This ensures that each agency-based user group can only access their own agency data yet allows the client to unify the previously separate proof of concept websites for each agency into a singular powerful more fully featured and robust website, and codebase, for the client to maintain.  This makes adding features, maintaining features, and even adding new agencies far simpler going forward. 


# Setup & Usage
1. Download and install VirtualBox https://www.virtualbox.org/wiki/Downloads
2. Download Ubuntu ISO image https://ubuntu.com/download/desktop
3. Create a new virtual machine using the Ubuntu ISO image and use settings that make sense for your environment.
4. Once the virtual machine is booted, you may want to view things in full screen. This can be done by:
   * Selecting **“Devices”** and then **“Insert Guest Additions CD image”**.
   * It should automatically run but if it doesn’t, run the **“autorun.sh”** file stored on the CD image and wait for it to complete.
   * Once finished, restart the virtual machine and hit **“Ctrl f”** to view things in full screen.
5. Launch a new terminal and update packages: **sudo apt update**
   * The user might need to be added to the sudoers file:
   * Type **su** and enter the password
   * Type **sudo usermod -a -G sudo "username"** with your username
   * Restart the machine, open a new terminal, and re-enter the **sudo apt update** command.
6. Install docker https://docs.docker.com/engine/install/ubuntu/
7. Clone the PeopleSense project repo  

>**Note:**
>    
>* The carbon-relay configs are in the carbon-relay folder at PeopleSense-Proj/PeopleSense/containers/carbon-relay/ 
>* The grafana dashboard api key should be set in the carbon-relay-ng.conf file for metrics to be pushed to the dashboard.  
>* The main.py script expects a .env file with the PeopleSense API key and other items like so:
>    
>    API_KEY="api key"    
>    API_URL="url"  
>    CARBON_PICKLE_PORT=2013  
>    CARBON_SERVER=127.0.0.1  
>    DEBUG=no  
>    
>If Debug is set to "debug", the fake data generator is used instead of the PeopleSense API  
>The Carbon Pickle Port can be changed as long as it matches the carbon-relay-ng.conf file, the same goes for the ip address
  

8. Run the **setup.sh** script in PeopleSense-Proj/PeopleSense/containers/
9. Open the Grafana dashboard to see incomming metrics!

# How it works

<img src="/diagram/Project Architecture Diagram.png"/>

1.	Occupancy data are obtained and stored into AWS dynamoDB after going through a PeopleSense proprietary network.  
2.	The PeopleSense Dashboard 2.0 (this project) software queries the PeopleSense API on an interval set by the user per chart to retrieve data, current or historical based on user settings and chart type, regarding train occupancy as well as latitude and longitude information used to plot the location of the train on the Google Map API panel.  
3.	The data is then pushed to Influx which is housed in a Docker container for ease of deployment and portability.  
4.	Lastly, the PeopleSense Dashboard 2.0 front end will access and display various charts in the dashboard tiles for an improved user experience.

# User Experience

1.	Users use the Log in Page to create their account, log in with an existing account, or in the case of a forgotten password to begin the recovery process, or Continue as Guest with limited access to only current capacities.
2.	    a.	PeopleSense Dashboard 2.0 Home Page
2.	Users are restricted by their access through their assigned user group, and start with a blank Dashboard.
3.	    a.	Blank Dashboard  <img src="/diagram/Sample Empty Dashboard.png"/>
3.	Users can customize the dashboard to see specific trains, time periods, and a train's GPS location on the Google Maps API pane using the Left Side Pill.
4.	    a.	Side Pill
            i.	Choices (top to bottom): Line Chart, Bar Chart, Gauge
4.	Choosing a chart creates an empty panel.
a.	Empty Panel
5.	Users use the Right Side Panel to configure their chose chart
a.	Super Admins can Change Agency using the Agency Dropdown
i.	Agency Dropdown
b.	 The Train Dropdown selects the train to show in the unconfigured panel, filtered by the route selector to the right of the dropdown, which differs based on agency route groupings.
i.	Trains Dropdown
c.	The User can change how often the panel updates its data using the Refresh Rate dropdown
i.	Refresh Rate Dropdown
d.	The middle Button on the Left Side Pill creates an empty Map
i.	Empty Map
e.	The User then uses he Right Side Panel to configure the map, just as with a chart.
i.	Configured Map
6.	They can create multiple charts, move them, resize them, and the PeopleSense 2.0 Dashboard will save their layout between log in sessions, so they can resume where they left off without having to reconfigure their dashboard. <img src="/diagram/Sample Filled Dashboard.png"/>



# Utilities
## devfilter.py
Used for testing Bluetooth device filtering locally. Devices are blacklisted based on the UUIDs they provide. See https://www.bluetooth.com/specifications/assigned-numbers/ for lists of UUIDs and their meaning.

To use, first ensure you have Python 3.10 or later installed, along with the `bluez` and `bluez-utils` packages. Then run `python devfilter.py path_to_blacklist`, where `path_to_blacklist` is a text file listing blacklisted UUIDs. An example is provided in `utils/devfilter/blacklist.txt`. The program will scan for nearby Bluetooth devices and keep a running count of blacklisted devices.
# Timeline

<img src="/diagram/timeline.png"/>

# Testing (Coming Soon!)
