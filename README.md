# Web-Based Plant Watering System

## Overview

This project is a web-based plant watering system designed to automate the watering process for plants using a Raspberry Pi. The system provides a user-friendly web interface to manually water the plants, check soil moisture status, and toggle an auto-watering feature. It is built using Python, Flask, and the RPi.GPIO library to interface with the Raspberry Pi's GPIO pins.

## Components

1. **Hardware**:
   - Raspberry Pi
   - Soil moisture sensor
   - Water pump
   - GPIO pins for interfacing with the hardware components

2. **Software**:
   - `Flask` for the web server and user interface
   - `RPi.GPIO` for controlling the GPIO pins on the Raspberry Pi
   - Python scripts for handling the watering logic and web interface

## Files and Functionality

1. **web_plants.py**:
   - Main entry point for the Flask web application.
   - Defines routes for various actions such as manual watering, checking last watered time, checking soil status, and toggling auto-watering.
   - Uses the `water` module for hardware interactions.

2. **water.py**:
   - Contains functions to interact with the GPIO pins and control the watering system.
   - Functions include:
     - `get_last_watered()`: Reads the last watering time from a file.
     - `get_status(pin)`: Checks the status of the soil moisture sensor.
     - `init_output(pin)`: Initializes a GPIO pin as an output.
     - `auto_water(delay, pump_pin, water_sensor_pin)`: Runs an automatic watering loop.
     - `pump_on(pump_pin, delay)`: Activates the water pump for a specified duration and logs the watering time.

3. **main.html**:
   - HTML template for the web interface.
   - Displays the current server time, status messages, and provides buttons for user actions such as manual watering, checking soil status, and toggling auto-watering.

4. **auto_water.py**:
   - Script to run the `auto_water` function from the `water` module in a separate process.
   - Used by the Flask app to enable or disable auto-watering.

## Installation and Setup

1. **Hardware Setup**:
   - Connect the soil moisture sensor to a GPIO pin on the Raspberry Pi.
   - Connect the water pump to a GPIO pin on the Raspberry Pi.
   - Ensure the Raspberry Pi is powered and connected to your local network.

2. **Software Installation**:
   - Clone the repository to your Raspberry Pi.
   - Install the necessary Python libraries:
     ```bash
     pip install flask RPi.GPIO psutil
     ```
   - Set up the GPIO pins as per the pin configuration in the `water.py` script.

3. **Running the Application**:
   - Start the Flask web server by running `web_plants.py`:
     ```bash
     python web_plants.py
     ```
   - Access the web interface from a browser on the same network using the Raspberry Pi's IP address:
     ```
     http://<raspberry_pi_ip>:80
     ```

## Usage

- **Manual Watering**:
  - Click the "Water Once" button to activate the pump for a short duration.
  
- **Check Soil Status**:
  - Click the "Check Soil Status" button to get a real-time status of the soil moisture.

- **Check Last Watered Time**:
  - Click the "Check Time Last Watered" button to see when the plant was last watered.

- **Toggle Auto-Watering**:
  - Click "Turn ON Auto Watering" to start automatic watering based on the soil moisture status.
  - Click "Turn OFF Auto Watering" to stop the automatic watering process.

## Notes

- Ensure the `last_watered.txt` file is writable and accessible by the script for logging watering times.
- Properly handle GPIO cleanup to avoid conflicts when restarting the application or running other GPIO-related scripts.

## Contributions

Contributions to enhance the functionality, improve security, or add new features are welcome. Please fork the repository and submit a pull request with your changes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
