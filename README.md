# **BMP180 Sensor to ThingSpeak (with WiFiManager + OLED Display)**

This project reads **temperature** and **pressure** data from a BMP180 sensor and sends it to **ThingSpeak, ** a popular IoT data platform. It features:
* A configuration portal for entering WiFi and API credentials
* An OLED screen for real-time sensor data display
* Integration with the Solution Builders platform for easy flashing (Thus no hard coding required)

**Step-by-Step Setup Guide**

 1. **Create a ThingSpeak Account**
1.	Go to https://thingspeak.com
2.	Click **"Sign Up"** and create a free account
3.	Once logged in, go to your **Channels** page

**Create a New Channel**
1.	Click **"New Channel"**
2.	Fill in the following:
* Name: Any name (e.g., Weather Logger)
* Field 1: temperature
* Field 2: pressure
3.	Click "Save Channel"
**N/B** Make sure the field names are exactly temperature and pressure — they must match the fields used in the code.

**Get the ThingSpeak Write API Key**
1.	Inside your newly created channel, click on the  **"API Keys"** tab
2.	Copy the **Write API Key** (not the Read Key)
   
🔸 **Why use the Write API Key?**
Because the microcontroller is sending (writing) data to ThingSpeak. The Read API Key is only used to fetch data, which we’re not doing here.

**Flash the Code via Solution Builders**
1.	Click the following link which will redirect you to Carenuity’s solution builders platform and click install on th **BMP180Thingspeak Application**: https://solutions.carenuity.com/solutions/CvNzl2HewiJ08jA2p7mN?ecosystem=mxPH5kGodhJBicKPFXwx
2.	Connect your ESP8266-based board (e.g., NodeMCU or Wemos D1 Mini)
3.	Select the correct board and COM port
4.	Click Install

**Understanding the OLED Display**
The OLED screen (SSD1306) gives you live feedback:
* **During setup:** Instructions for how to connect to the WiFi configuration portal
* **After successful connection:** A message like “Connected!”
* **During operation:** Displays current temperature and pressure from the BMP180 sensor

If the sensor is not connected or fails, the display shows an error like:

> BMP180 not found!

**Using the WiFiManager Config Portal**
After flashing, the ESP8266 will:
1.	Start a Wi-Fi Access Point named BMP180Config
2.	You should:
* Connect to this WiFi using your phone or computer
* A page will automatically open (or go to 192.168.4.1)

3.	Fill in:
* Your WiFi name and password
* Your ThingSpeak Write API Key
4.	Click Save
The device will restart and automatically connect to WiFi and start sending data to ThingSpeak.
If nothing is entered within 3 minutes, the portal will close and it will use saved credentials (if available).

**Viewing Data**
Once the board is connected:
* The OLED will show temperature and pressure every 30 seconds
* Visit your ThingSpeak channel and check the Field 1 and Field 2 charts
* You’ll see the data appear live!
