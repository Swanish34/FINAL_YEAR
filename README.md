# FINAL_YEAR
TeleMetrix Analytics: High-Performance IoT Vehicle Monitoring
TeleMetrix is a real-time vehicle monitoring system built using an ESP32 microcontroller, an MPU6050 Inertial Measurement Unit (IMU), and a responsive web dashboard. It streams live sensor data (Acceleration, Angular Velocity, Simulated Speed, GPS) over WebSockets for real-time visualization, driver risk assessment, and performance scoring.

Target Hardware: ESP32 (acting as a server) and a browser (client).

#file & Description
testing1_7_morning_cluade.ino ----------->  "Arduino Sketch: The core firmware for the ESP32. Handles WiFi, MPU6050 initialization, WebSocket server, and data transmission."

index.html-------------------------> Landing Page/Login: The entry point to the system with a simulated login process and a riding animation before redirecting to the dashboard.
dashboard.html----------------------> "Web Dashboard: The client-side interface. Features real-time charts (Chart.js), GPS mapping (Leaflet.js), sensor data cards, and a driver risk assessment system."

# Setup & Execution Guide

## Step 1: Configure the ESP32 Firmware (testing1_7_morning_cluade.ino)
Open the Sketch: Open the testing1_7_morning_cluade.ino file in your Arduino IDE.
Update WiFi Credentials: Modify the ssid and password variables to match your local WiFi network.

## Step 2: Wire the Hardware
Connect the MPU6050 to the ESP32:
MPU6050 Pin,ESP32 Pin
VCC->3.3V
GND->GND
SCL->GPIO 22
SDA->GPIO 21
INT->(Not used in this sketch)

## Step 3: Upload the Code
Select the correct Board (e.g., "ESP32 Dev Module") and Port in the Arduino IDE.
Upload the testing1_7_morning_cluade.ino sketch to your ESP32.
Open the Serial Monitor (set baud rate to 115200).

## Step 4: Find the ESP32's IP Address
Wait for the ESP32 to connect to your WiFi. The Serial Monitor will print the device's IP address:
WiFi Connected!
IP Address: 192.168.1.XX
Connect to: ws://192.168.1.XX/ws
Note: Save this IP address (192.168.1.XX)—you will need it for the dashboard.

## Step 5: Launch the Dashboard
The dashboard is a client-side application and does not require a traditional web server.
Open the index.html file in a modern web browser (Chrome, Firefox, Edge).
Click "Access Live Telemetry (H2R)" or "System Login" and complete the simulated login to be redirected to dashboard.html.
On the Dashboard (dashboard.html):
Click the "Connect ESP32" button in the yellow banner.
Enter the IP Address you noted from the Serial Monitor (e.g., 192.168.1.XX).
Once the connection is established, the status will change to 🟢 ONLINE.

Step 6: Start Monitoring
Click the "ACTIVATE MONITORING" button. The button will turn orange and the text will change to "STOP MONITORING".
The ESP32 will now begin sending real-time sensor data over the WebSocket connection every 100ms.
Move the MPU6050 to see the Speed, Acceleration, Angular Velocity, and MPU6050 Sensor Readings update live on the dashboard! The charts and risk score will also dynamically react to the movement.
