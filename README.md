# IoT Accident Detection System

## Overview

This project implements an accident detection system using an Arduino Nano, GPS module, and GSM module (SIM800). It detects impacts through vibration sensors, retrieves GPS coordinates upon detection, and sends alerts via SMS and phone calls to a designated emergency number.

## Features

- **Impact Detection**: Utilizes vibration sensors to detect sudden impacts.
- **GPS Tracking**: Retrieves GPS coordinates for location tracking during an accident.
- **Emergency Alerts**: Sends SMS and makes a phone call to an emergency contact when an accident is detected.
- **Manual Override**: Allows manual cancellation of alerts through a button press.

## Components Required

- Arduino Nano
- SIM800 GSM module
- GPS Module (e.g., Neo-6M)
- Vibration Sensors (3-axis accelerometer)
- Buzzer
- Push Button
- Connecting wires
- Breadboard (optional)

## Connections

| Component        | Arduino Pin |
|------------------|-------------|
| SIM800 TX        | Pin 2       |
| SIM800 RX        | Pin 3       |
| GPS TX           | Pin 8       |
| GPS RX           | Pin 9       |
| Vibration Sensor X| A1         |
| Vibration Sensor Y| A2         |
| Vibration Sensor Z| A3         |
| Buzzer           | Pin 12      |
| Push Button      | Pin 11      |

## Code Explanation

### Libraries Used

- `AltSoftSerial`: Used for communicating with the GPS module.
- `TinyGPS++`: A library to decode GPS data.
- `Wire`: Used for I2C communication (if required).
- `SoftwareSerial`: Used for communication with the SIM800 GSM module.

### Key Functions

- **setup()**: Initializes serial communications, sets up the SIM800 module, and reads initial values from the accelerometer.
- **loop()**: Continuously checks for impacts, handles alerts, and processes incoming SMS messages.
- **Impact()**: Detects impacts by comparing changes in vibration sensor readings.
- **getGps()**: Retrieves the current GPS coordinates.
- **sendAlert()**: Constructs and sends an accident alert SMS with GPS coordinates.
- **makeCall()**: Initiates a phone call to the emergency contact.
- **sendSms()**: Sends an SMS message using the SIM800 module.
- **parseData()**: Processes incoming SMS messages and checks for commands.

## Usage

1. **Configure Emergency Contact**: Replace `EMERGENCY_PHONE` in the code with your emergency contact number.
2. **Upload the Code**: Use the Arduino IDE to upload the code to your Arduino Nano.
3. **Power Up the System**: Connect the Arduino Nano to a power source.
4. **Testing**: Simulate impacts on the vibration sensors to test the alert system.

## Important Notes

- Ensure that the SIM800 module has a valid SIM card with SMS and calling capabilities.
- The GPS module may take some time to acquire a fix; ensure it has a clear view of the sky.
- Adjust the sensitivity threshold in the code as needed for your specific application.

## Troubleshooting

- **No GPS Data**: Ensure that the GPS module is receiving a clear signal.
- **SMS Not Sending**: Check the SIM card for balance and ensure it's not locked or blocked.
- **Buzzer Not Working**: Verify the connections and test the buzzer independently.

## License

This project is open source. Feel free to modify and distribute the code as needed.