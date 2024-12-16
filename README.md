[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/KSk4F6vj)

6.7 Final Report (Website)
Description
It’s time for a retrospective (sometimes called a post-mortem). Reflect on and respond to the following questions to better understand your successes and failures.

Note: Your project need not be feature-complete to receive full credit. We like to see students taking calculated risks on projects, which can still result in failure - or what we call productive failure. Taking risks and failing is an excellent way to learn, so we’d like to reward that.

Review your IoT Venture Pitch assignment. Identify what changed throughout the project, including:
Target Market & Demographics
Security, Hardware, & Software Requirements
Product Function & Components
Power & Cost Budgeting
What parts of your project would you consider a success? Why?
What parts of your project didn’t go well? Why?
If you had to do it again, how might you change your development approach given the finite time and money resources?
Would you change your system design after this development cycle? For example:
Was your wireless communication protocol the correct choice?
Would other sensors or actuators work better?
Did your target market want something different?

In addition to these questions, include evidence of your product working.
Images of your MVP device
Remember, we have a light box in the Detkin Lab for taking nicer photos with good lighting.
You might not want a sterile environment for these photos - consider taking the photos where your device would be operating!
A video demonstrating:
Your Core Product Function
Memfault integration features
Anything else you think is relevant to the project
Imagine you’d like to show your family or a potential employer what you did this semester. What would you want to include?

Answer these questions in your README. Then, using GitHub Pages, make this repository a publicly viewable website. Feel free to create a more beautiful webpage, but the baseline is a webpage generated from the README.md file.
Submission Details
The GitHub repository README is updated with all pertinent information.



## 1. The Idea
The original idea for the IoT Venture was to create a smart dog feeder. Significant research was put into this and can be referenceed here. However, it was decided to pivot to a more ambitious project and due to some interesting use cases of RTK-GPS for aerial robots, a decision was made to research applications for ground robots instead. Leveraging similar technology, there is a uniqe advantage to accurately knowing the location of a ground robot for using a tool, end effector, or actuator in the real world.

This led to the idea of developing an RTK-GPS system for mobile robots by creating a rover and base station module using a combined RTK-GPS module, a LoRa module, and leveraging the nRF 5340 where the base station corrects the relative position of the rover using RTCM correction data. This would allow the mobile robot to have a painting tool and follow a specified path with GPS coordinates that form trajectories for the robot to navigate and paint sport field lines.

So, all areas were changed, including:
1. Target Market & Demographics
2. Security, Hardware, & Software Requirements
3. Product Function & Components
4. Power & Cost Budgeting

*more reflection*

## 2. Reflecting on the Venture Pitch
Going back to the original Venture Pitch, the main concerns with the smart dog feeder that were discussed were unique features for market penetration, reliability of the dispensing mechanism being a mechanical factor limiting progress, and an innovative user interface. Reflecting on this, the project was changed because a newer market that transfers technology would better benefit from IoT features integrated into a novel product.

A second Venture Pitch was done that highlighted the wireless communication with WiFi and LoRa, development with an RTK-GPS module (ZED-F9P), andthe use of off the shelf robot solutions. This combines into a feasible demo with a lean team for engineering and scalability considerations to integrate with existing stadium infrastructure. The primary focus for the product and demo is to target professional sports fields to acquire credibility, funding, and marketability from working with an initial high profile client.

## 3. Successes

1. NTRIP Server:

The NTRIP server from RTK2go.com was successfully leverage to gather GPS correction data based on a station in Pottstown, Pennsylvania. The connection is made following the specification of the NTRIP host, port, and mount point. A TCP connection is made to the NTRIP server, then a formatted HTTP GET request is sent to the specified mount point, and finally the nRF 5340 receives RTCM correction data.

2. Filtering RTCM Correction Data:

The RTCM correction data is filtered to ensure that only the necessary RTCM message types required by the ZED-F9P cinluding 1005, 1074, 1084, 1094, 1124, 1230 for high precision positioning. This also improves the bandwidth and prevents overloading of the ZED-F9P by reducing the amount of data sent from the nRF 5340.

3. UART Transmission:

Using Zephyr and the device tree, UART 1 is specified for communication allowing for this code to be better transferred between development boards. Specifying the device tree required a more complex configuartion through nRF Connect but would hopefully result in easier development moving forward.

4. Procedural Processes:

All steps of connecting to the NTRIP server up to the transmission of RTCM correction data detail the current step of the process and any possible errors including the network connection, binding the UART device, and resolving the host. This allows for all devices in a fleet on boot up to easily show errors for fixing any possible formatting issues most likely related to specifiying the correct information for the NTRIP server, the WiFi network, or possible UART availability. The first two are primarily of interest to customers or technicians who need to implement a specific setup. Callbacks are implemented as well for dealing with network connections to capture errors with WiFi. This allows for the device to trigger a response and would further help with reporting issues in a fleet of wireless devices.

5. Technology for Clients:

The technology developed for this project looks to use an engineered device in a way that is designed for use by those without an engineering background. This is because many of the workers maintaining sports fields likely are not exposed to these topics. The opportunity presented would allow for a business model leveraging technicians familar with the system to service and possibly operate multiple autonomous systems in a metropolitan area.***


## 4. Failures

1. Project Timeline:

The pivot from the initial idea required more attention from the group to focus on the change in technology. Many tasks were pushed off relating to Memfault and the LoRa module. Parts did not arrive on the expected timeline due to orders from Detkin falling behind so the time to work with the nRF 7002 DK and the ZED-F9P was less than expected.

2. Full Memfault Integration:

The full Memfault integration was not achieved because of misunderstandings with using the Memfault metrics feature. Core dumps were achieved and an event was triggered but not reported to the Memfault graphs. Setup was done within the methodology of the code for Memfault integration to implement code for tracking metrics.

3. Full RTCM data for RTK Lock:

The RTCM data for RTK lock is transmitted out of the nRF 7002 DK but it is not recognized by the ZED-F9P. This is likely due to a message formatting issue with how the RTCM data is packaged. Attempts were made to try and identify the message structure based off of a Sparkfun guide but were not fully formatted correctly for the demo.

## 5. Improving Workflow
If you had to do it again, how might you change your development approach given the finite time and money resources?

## 5. Improving Technology
Would you change your system design after this development cycle? For example:
Was your wireless communication protocol the correct choice?
Would other sensors or actuators work better?
Did your target market want something different?

## More Stuff
SEE doc for more stuff:

In addition to these questions, include evidence of your product working.
Images of your MVP device
Remember, we have a light box in the Detkin Lab for taking nicer photos with good lighting.
You might not want a sterile environment for these photos - consider taking the photos where your device would be operating!
A video demonstrating:
Your Core Product Function
Memfault integration features
Anything else you think is relevant to the project
Imagine you’d like to show your family or a potential employer what you did this semester. What would you want to include?