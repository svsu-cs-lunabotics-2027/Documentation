# Software & Automation Team PDR
This is the initial preliminary design review for the Software & Automation (CS) team for the NASA Lunabotics 2027 challenge. <br>
<br>
<em>Written by James Meyers.</em>
<br>

## Requirements
The following are the requirements pertaining to the software system and its related subsystems. These requirements include requirements from other teams and the systems that they create i.e. interface hooks and systems that are created by the CS team. This is a since this is a PDR more are expected to be added as we move through the systems engineering process.

### External Requirements

- <b> 1.0: Power </b>
    - 1.1: The Jetson shall be supplied a power input of at least 38W (ECE)
    - 1.2: The Jetson shall be supplied power via its onboard DC jack
    - 1.3: Other peripherals attached to the Jetson shall be powered by the Jetson via USB or other means
- <b> 2.0: Mounting </b>
    >Note: These are left vague right now so we can discus these and finalize and narrow them down :)
    - 2.1: The OAK-D W shall be mounted so that it is facing the side of the robot that the material will be dumped out
        - 2.1.1: This side shall be designated the front of the robot for the CS teams purposes
        - 2.1.2: The purpose of this is to only require one camera hopefully
    - 2.2: The OAK-D W shall be mounted either on its 75mm VESA mounting points or its tripod mount
    - 2.3: The OAK-D W shall be mounted in a position where it's vision is the least obstructed by the robot body
    - 2.4: The mounting hardware shall secure the OAK-D W at an angle that maximizes valid point cloud generation and prevents autonomy degradation resulting from poor environmental visibility
    - 2.5 : The Jetson, Picos, & other relevant hardware shall have a secure mounting point
    - 2.6: The Jetson shall have adequate cooling provided so that it does not overheat
    - 2.7: The RPLIDAR C1 shall be mounted in a position high enough to only detect rocks and walls
- <b> 3.0: Interfaces </b>
    >Note: This will definitely need to be discussed further as the project goes on!
    - 3.1: Motor interfaces shall use xxx to connect to the Pico/Jetson
    - 3.2: Actuator interfaces shall use xxx to connect to the Pico/Jetson

### Internal Requirements

- <b> 4.0: Connectivity </b>
    - 4.1: The Jetson shall connect to the MCC over Wi-Fi
    - 4.2: The MCC shall connect to the Jetson over Wi-Fi
    - 4.3: A standard router shall be used to facilitate the Wi-Fi connection
    - 4.4: The Jetson shall connect to Picos via USB
- <b>5.0: Drive System</b>
    - 5.1: The drive system shall translate velocity and heading commands into individual motor commands
    - 5.2: The drive system shall publish telemetry about motor data
- <b>6.0: Dig System</b>
    - 6.1: The dig system shall translate dig commands into individual motor and actuator commands
    - 6.2: The dig system shall publish telemetry about related motor and actuator data
- <b>7.0: Dump System</b>
    - 7.1: The dump system shall translate dump commands into individual motor and actuator commands
    - 7.2: The dump system shall publish telemetry about related motor and actuator data
- <b>8.0: Teleoperation</b>
    - 8.1: Teleoperation shall be a backup robot control method as autonomy is the goal.
    - 8.2: The Jetson shall receive and route mapped inputs from the MCC game controller directly to the corresponding system control.
    - 8.3: The rover shall transmit real-time telemetry data to the MCC.
    - 8.4: The RVis2 sensor visualization application shall be preferred over a camera feed to mitigate average bandwidth usage
        - 8.4.1: The Jetson shall compress and stream the OAK-D W RGB feed to the MCC at a minimum of [X] fps and [Y] resolution to ensure drivability if RVis2 becomes unsuitable for use.
        - 8.4.2: The MCC shall have the ability to turn the camera stream on or off at any time.
    - 8.5: The teleoperation system shall have a lockout toggle to prevent unwanted inputs for safety.
- <b>9.0: Autonomy</b>
    - 9.1: The Jetson shall process depth, RGB, and Lidar data from the OAK-D W and RPLIDAR C1 to generate a cost map of the arena.
    - 9.2: The Jetson shall compute collision-free paths to target coordinates
    - 9.3: The Jetson shall fuse wheel odometry with the LSM6DSOX data to estimate local position at [X] Hz
    - 9.4: The rover shall autonomously transition between driving, digging, and dumping states based on its location and payload weight.
    - 9.5: The Jetson shall automatically halt movement if an obstacle is detected within [X] meters of the front chassis.
    - 9.6: Autonomy mode shall be activated via one command on the MCC
    - 9.7: Autonomy mode shall display a prompt on the MCC for the duration of autonomy mode for judges visual confirmation
    - 9.8: Autonomy mode shall not accept any user input for the duration except to exit autonomous mode or perform the software E-Stop
    - 9.9: RVis2 shall be used to visualize autonomous capability and actions to judges
- <b>10.0: Safety & Reliability</b>
    - 10.1: If the Jetson loses Wi-Fi connection to the MCC for more than [X] seconds, all motors and actuators shall immediately halt (Watchdog Timer)
    - 10.2: The MCC shall feature a software Emergency Stop that bypasses all autonomy and teleop queues to cut motor commands
    - 10.3: The MCC shall have the ability to override Autonomy mode and force the rover into Teleoperation mode at any time

## System Overview
This section shows our initial software system overview. As we progress with our design this will be filled out better.
>The modules for the architecture

<br>

![ArchitectureImage](./CS%20Team%20System%20Architecture.drawio.png)