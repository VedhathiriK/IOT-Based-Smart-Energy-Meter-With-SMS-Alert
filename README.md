🔌 IoT-Based Smart Energy Meter with SMS Alert (ESP32 + PZEM-004T)

An IoT-based real-time energy monitoring system using ESP32, PZEM-004T energy meter, MQTT dashboard, LCD display, and SMS alerts via Circuit Digest Cloud API.
This project enables remote monitoring of electrical parameters and instant fault notifications with low latency and minimal hardware complexity.

📌 Features
📊 Real-time monitoring of:

Voltage

Current

Power

Energy consumption

Frequency

Power Factor

📱 Live MQTT dashboard

📟 16×2 LCD local display (I2C)

🚨 SMS alert for abnormal conditions

⚡ Factory-calibrated energy measurement (PZEM-004T)

🌐 Low-latency MQTT communication

🔒 Safe isolation from mains voltage



🧠 Why PZEM-004T?

The PZEM-004T (V4.0) is a reliable AC energy measurement module that eliminates complex calibration required by sensors like ACS712 or ZMPT101B.

Measured Parameters
Parameter	Range
Voltage	80 – 260V
Current	0 – 100A
Active Power	0 – 23kW
Power Factor	0.00 – 1.00
Frequency	45 – 65Hz
Energy	0 – 250000 kWh



⚙️ How It Works

PZEM-004T measures AC electrical parameters using:

Direct voltage input

External CT (Current Transformer) on live wire

ESP32 reads data via UART (Modbus)

Data is:

Displayed on LCD

Published to MQTT dashboard

If abnormal conditions are detected:

SMS alert is sent using Circuit Digest Cloud API



🧩 Components Required
No	Component	Quantity
1	ESP32	1
2	PZEM-004T (V4.0)	1
3	External CT	1
4	16×2 LCD	1
5	I2C LCD Module	1
6	Breadboard	1
7	Jumper Wires	As required
8	Arduino IDE	Software
🧱 Block Diagram
AC Load → PZEM-004T → ESP32 → 
        → LCD Display
        → MQTT Dashboard
        → SMS Alert (Cloud API)


        

🔌 Circuit Overview

ESP32 UART:

TX → GPIO 17

RX → GPIO 16

LCD connected via I2C (Address: 0x27)

CT clamped only on the live wire

PZEM handles high-voltage isolation internally

⚠️ Do NOT connect neutral and live both through CT




💻 Software & Libraries
Required Libraries
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <PZEM004Tv30.h>
#include <WiFi.h>
#include <PubSubClient.h>
#include <HTTPClient.h>

🧪 Fault Detection Logic
if (V > 50 && I <= 0.001) {
    sendSMS();
}

Trigger Condition

Voltage present

No current flow detected

🕒 SMS cooldown implemented to avoid spamming.

📟 Display Behavior

LCD cycles automatically through:

Voltage

Current

Power

Power Factor

Frequency

Data displayed simultaneously on:

Serial Monitor

LCD

MQTT Dashboard

📡 MQTT Dashboard

Live real-time streaming

Low bandwidth usage

Ideal for IoT monitoring

Supports multiple data subscribers

📲 SMS Alert Feature

Uses Circuit Digest Cloud API

No paid SMS gateway required

Triggered during abnormal electrical conditions

Internet (Wi-Fi) required



🏠 Applications

Smart home energy monitoring

Electrical fault detection

Remote energy tracking

Industrial load monitoring

Farmhouses & remote sites

Predictive maintenance systems



✅ Advantages

Factory-calibrated measurements

Minimal ESP32 processing load

Secure cloud-based alerts

Scalable for future automation

Beginner-friendly hardware setup


🔐 Safety Notes

PZEM-004T provides isolation from mains voltage

Do not touch AC terminals while powered

Ensure proper insulation and enclosure



📌 Future Improvements

Web dashboard UI

Over-voltage & overload detection

Energy billing estimation

Mobile app integration

Data logging & analytics



❓ FAQs

Q1. Why MQTT instead of HTTP?
MQTT is lightweight, faster, and consumes less bandwidth.

Q2. Is Wi-Fi mandatory?
Yes, for MQTT data and SMS alerts.

Q3. Is it safe with mains electricity?
Yes, PZEM-004T isolates high voltage from ESP32.

Q4. Can this detect power failure?
Yes, voltage drop and zero-current conditions.




🧾 Conclusion

This project demonstrates a practical, scalable, and reliable IoT-based energy monitoring system using ESP32 and PZEM-004T. With real-time monitoring, MQTT streaming, and instant SMS alerts, it provides both convenience and safety, making it ideal for modern smart energy applications.
