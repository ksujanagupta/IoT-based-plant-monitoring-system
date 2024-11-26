# IoT-Based Plant Monitoring System

The **IoT-Based Plant Monitoring System** is a smart solution designed to automate and optimize plant care using IoT devices and sensors. This project is ideal for home gardeners, agricultural professionals, or anyone interested in enhancing their plant care routine with technology.

## Features
- **Soil Moisture Monitoring**: Tracks soil moisture levels to ensure plants receive the right amount of water.
- **Temperature and Humidity Monitoring**: Monitors the environment using a DHT11 sensor and provides real-time feedback.
- **Motion Detection**: Uses a PIR motion sensor to detect movement near the plants, which could help with garden security.
- **LCD Display**: Displays live data for temperature, humidity, and soil moisture.
- **Blynk Integration**: Allows remote monitoring and control of the system via the Blynk app.
- **Relay Control**: Operates devices such as irrigation systems or lights based on environmental conditions or manual commands.
- **Physical Button Input**: Provides local manual control of the relay for additional convenience.

---

## Components and Requirements
### Hardware:
1. **ESP8266 NodeMCU** - Microcontroller for managing sensors and Wi-Fi connectivity.
2. **DHT11 Sensor** - Measures temperature and humidity.
3. **Soil Moisture Sensor** - Monitors the soil moisture levels.
4. **PIR Sensor** - Detects motion in the plant area.
5. **Relay Module** - Controls external devices (e.g., water pump, grow light).
6. **Push Button** - Provides manual control over the relay.
7. **16x2 LCD Display with I2C Module** - Displays real-time sensor data.

### Software:
- **Arduino IDE** for code development and uploading.
- **Blynk App** for remote monitoring and control.
- Libraries:
  - `LiquidCrystal_I2C`
  - `ESP8266WiFi`
  - `BlynkSimpleEsp8266`
  - `DHT`

---

## Getting Started
1. **Install Required Libraries**:
   Install the following libraries in the Arduino IDE through the Library Manager or download them from the respective repositories:
   - `LiquidCrystal_I2C`
   - `ESP8266WiFi`
   - `BlynkSimpleEsp8266`
   - `DHT`

2. **Connect the Components**:
   - Refer to the circuit diagram for connecting the DHT11, soil moisture sensor, PIR sensor, LCD, relay, and push button to the ESP8266.

3. **Setup Blynk**:
   - Download the [Blynk App](https://blynk.io/).
   - Create a new project in the app and copy the authentication token.
   - Set up virtual pins in the Blynk app:
     - Virtual Pin `V6`: Toggles PIR sensor.
     - Virtual Pin for the push button: Adjust according to your setup.

4. **Update Wi-Fi Credentials**:
   - Add your Wi-Fi SSID and password, as well as the Blynk auth token, in the code:
     ```cpp
     char auth[] = "YourAuthToken";
     char ssid[] = "YourWiFiSSID";
     char pass[] = "YourWiFiPassword";
     ```

5. **Upload the Code**:
   - Upload the provided code to the ESP8266 using the Arduino IDE.

6. **Power On**:
   - Power the ESP8266 and monitor the system via the LCD display and Blynk app.

---

## Code Explanation

### Libraries and Initial Setup:
- **Libraries**: The project uses `LiquidCrystal_I2C` for LCD control, `ESP8266WiFi` and `BlynkSimpleEsp8266` for Wi-Fi and Blynk integration, and `DHT` for temperature and humidity readings.
- **Global Variables**:
  - Wi-Fi credentials (`auth`, `ssid`, `pass`) for Blynk connectivity.
  - Sensor pins for soil moisture and PIR sensors.
  - States for relay and physical button.

### Setup:
- Initializes all components (LCD, DHT sensor, Wi-Fi).
- Sets up the Blynk connection and schedules periodic tasks for reading sensor data.

### Sensor Functions:
1. **DHT11sensor**:
   - Reads temperature and humidity values.
   - Sends data to the Blynk app and displays it on the LCD.
2. **soilMoistureSensor**:
   - Maps soil moisture raw data to a percentage.
   - Sends moisture level to Blynk and displays it on the LCD.
3. **PIRsensor**:
   - Detects motion and logs events to Blynk.

### Blynk Functions:
- Syncs the PIR sensor and relay states with the app.
- Updates relay state when toggled via the app.

### Physical Button:
- Monitors the state of the push button to toggle the relay locally.

### Main Loop:
- Continuously updates the LCD with sensor data and manages tasks through Blynk and timers.

---

## How It Works
1. **Data Collection**: Sensors gather data about temperature, humidity, and soil moisture.
2. **Real-Time Display**: Sensor data is displayed on the LCD and sent to the Blynk app.
3. **Automation**: The relay can be controlled based on sensor readings or manually through the app or push button.
4. **Motion Alerts**: The PIR sensor detects motion and alerts the user via the app.

---

## Future Enhancements
- Add support for more sensors (e.g., light intensity).
- Implement advanced automation rules.
- Enable data logging for long-term analysis.
- Integrate with other IoT platforms 

---

## Contact
For questions or contributions, feel free to reach out via GitHub issues or email at [your-email@example.com].

