# Domestic-Farming-Solutions
Brief Summary of the Domestic Farming Solutions Project

The Domestic Farming Solutions project is a web-based platform designed to help individuals set up and manage their own kitchen or terrace gardens. It provides personalized plant recommendations, an AI-powered chatbot, and educational resources to promote sustainable urban farming.

Key Features
Plant Recommendation System – Suggests plants based on location, season, soil type, and garden size.
AI Chatbot – Provides instant guidance on gardening topics such as pest control, watering schedules, and soil preparation.
Weather API Integration – Uses real-time weather data to refine plant recommendations.
Interactive Content – Includes gardening tutorials, composting techniques, and watering guides.
Technology Stack
Frontend: HTML, CSS, JavaScript, (React.js optional).
Backend: Python (Flask/Django) or Node.js.
Database: MySQL or MongoDB.
APIs: OpenWeatherMap (for real-time weather updates).
Chatbot: Dialogflow or Rasa (for NLP integration).
Objectives
✔️ Make gardening accessible for beginners.
✔️ Promote sustainable urban farming.
✔️ Encourage self-reliance by reducing dependence on store-bought produce.
✔️ Educate users on eco-friendly gardening (composting, water conservation).

Novelty in the Project
Personalized recommendations based on user-specific inputs.
AI chatbot for real-time assistance.
Sustainability-focused approach to encourage small-scale urban farming.
[Watch the video here](https://drive.google.com/file/d/1Ih5xNSfupHnHKtOyWE6N0regSlxF5dyV/view?usp=sharing)
Automated Soil Moisture Monitoring and Irrigation System
This project implements an Arduino-based soil moisture monitoring and automated irrigation system using a soil moisture sensor, relay-controlled water pump, and LED indicators. The system ensures efficient water management by automatically activating irrigation when soil moisture falls below a predefined threshold.

📌 Features
Real-time soil moisture monitoring using an analog sensor.
Automatic motor control via a relay switch.
LED indicators for system status:
Red LED → Low moisture (Motor ON)
Green LED → Sufficient moisture (Motor OFF)
Prevents overwatering by stopping irrigation once the moisture level reaches the threshold.

🔧 Hardware Components
Component	Description
Arduino Uno	Microcontroller unit for processing sensor data and controlling outputs.
Soil Moisture Sensor	Analog sensor to measure soil water content.
5V Relay Module	Controls the motor (water pump) based on moisture readings.
Water Pump (Motor)	Provides irrigation when soil moisture is low.
Red LED	Indicates dry soil, motor activation.
Green LED	Indicates sufficient moisture, motor deactivation.
Power Supply (5V/12V)	Required to operate the system.

📜 System Architecture & Working Principle
The Soil Moisture Sensor continuously measures soil water content and transmits an analog signal to the Arduino Uno.
The Arduino processes the input signal and compares it with a predefined threshold value (calibrated for different soil types).
Based on the moisture level:
If moisture < threshold → The relay is activated, the water pump starts, and the red LED turns ON.
If moisture ≥ threshold → The relay is deactivated, the water pump stops, and the green LED turns ON.
The system operates in real-time, ensuring an optimal irrigation cycle without manual intervention.

💻 Arduino Code Implementation
cpp
Copy
Edit
// Pin Definitions
#define SENSOR_PIN A0  // Soil moisture sensor (analog input)
#define MOTOR_PIN  9   // Motor connected via relay
#define RED_LED    7   // Indicator for low moisture
#define GREEN_LED  6   // Indicator for sufficient moisture

int moistureValue = 0;  // Stores soil moisture sensor readings
const int THRESHOLD = 400; // Define threshold based on soil conditions

void setup() {
    pinMode(MOTOR_PIN, OUTPUT);
    pinMode(RED_LED, OUTPUT);
    pinMode(GREEN_LED, OUTPUT);
    Serial.begin(9600); // Serial monitor for debugging
}

void loop() {
    // Read soil moisture level
    moistureValue = analogRead(SENSOR_PIN);
    Serial.print("Soil Moisture Level: ");
    Serial.println(moistureValue);

    // Decision Making Logic
    if (moistureValue < THRESHOLD) {  // Soil is dry
        digitalWrite(MOTOR_PIN, HIGH); // Activate relay (start pump)
        digitalWrite(RED_LED, HIGH);   // Turn ON red LED
        digitalWrite(GREEN_LED, LOW);  // Turn OFF green LED
    } else {  // Soil moisture is sufficient
        digitalWrite(MOTOR_PIN, LOW);  // Deactivate relay (stop pump)
        digitalWrite(RED_LED, LOW);    // Turn OFF red LED
        digitalWrite(GREEN_LED, HIGH); // Turn ON green LED
    }

    delay(1000); // Sampling delay
}


