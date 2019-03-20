# PhysPi

This is the PhysPi Laboratory Environmental Monitoring System, constructed as my fourth year honours project in physics at Carleton University (Ottawa ON) under the supervision of Dr. Thomas Koffas and the CU-ITk research team.

This is the repo for the project as it stood in April 2018 when I completed my time on the research team. The project is still in use and has been modified by other students and researchers.

Please note that this ReadMe provides only a basic summary of the project for at-a-glance reading.  For a very in depth explanantion of the project and the underlying physics, please refer to the thesis write up in the "Documentation" folder.

## Background

The CU-ITk research team is a branch of CERN's ATLAS project responsible for the design and development of silicon microstrip sensors for the reconstruction of the ATLAS detector's innermost part, the Inner Tracker (ITk).  These sensors are composed of extremely sensitive and fragile material and are being worked on in an undergraduate engineering laboratory alongside multiple other engineering and physics research projects.  Due to the fragility of the sensors and the nature of the research circumstances, it is essential to the project that the temperature and humidity conditions be monitored for changes and the subsequent testing and development can be calibrated accordingly.  For my undergraduate thesis in physics I constructed the PhysPi Environmental Monitoring System to do this job.

## Hardware

This system employs the use of the following hardware in a very simple setup:

* Raspberry Pi 3
* Arduino Uno board
* 2X SHT75 digital temperature and humidity sensors
* The following necessary accessories:
  * Raspberry Pi case
  * Raspberry Pi power source
  * HDMI monitor and adapter

## Software and System

This system employs the use of multiple programming languages and technology.  A bash script called run.sh is executed on Raspberry Pi startup to run the entire program automatically when the system is powered on.

### Data Read-In

The data being interpreted by the SHT75 sensors consists of values of temperature (in degrees celsius) and humidity. The sensors also record a measure of dewpoint, but this is not being used for our purposes.  Initially, the data is set up to record using programming on the Arduino board (2sht.ino) and this is sent to the Rasperry Pi via serial connection.

### Storing Data

On the Raspberry Pi, the data being sent via serial connection is analyzed using 2sht.py.  This program reads in and formats the data then posts the data to the existing MySQL database.

### Data Visualization

Once the python file has pushed the dat ato the database, a file called 2shtplot.py compiles the last hours' worth of data to be plotted and shown for visualization purposes.

Once the last hours' data has been logged, log1.plt and log2.plt use GnuPlot to plot the last hours' temperature and humidity data against time for each of the two sensors.

The plots are displayed on Chrome localhost using PHP and HTML to create a basic webpage for viewing purposes (data is displayed as an HTML table, plots are imported as images).

## Future Work and Extensions

The PhysPi has tremendous potential in a laboratory setting. Future goals include to expand the system to have more sensors attached and potentially to organize the sensors in a circular form around an area of interest for optimal measurements.  Implementing the use of multiple Raspberry Pi/Arduino setups would also allow for measurements to be taken across the lab with great accuracy.

At the time of this project the SHT75 sensors were the sensors available, however Sensiron plans to discontinue these sensors.  In the future it would be wise to update the PhysPi system to another type of sensor.

The scope of my work did not include managing the data stored in the SQL database nor the usage of the data taken.  In the future, it would be wise to destroy some or all data from before a previous date (to be determined by the research staff) and mathematical functionality could possibly be created to calibrate the existing lab software to adjust to the data recorded by the PhysPi.

## Images and Screenshots
