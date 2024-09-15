Name:Uppara Pavani

Company:CODTECH IT SOLUTIONS

ID:CT08DS7245

Domain:Embedded Systems

Duration:August to September 2024

Mentor:Neela Santhosh Kumar



PROJECT OVERVIEW:
![Task2](https://github.com/user-attachments/assets/114c3864-822e-450c-8da5-2f2ed2816ae2)




This project involves interfacing a DHT (Digital Humidity and Temperature) sensor with an Arduino board to measure ambient temperature and humidity. The sensor readings are then displayed on an LCD screen or serial monitor.

Components Required

- Arduino Board (e.g., Arduino Uno)
- DHT Sensor (e.g., DHT11 or DHT22)
- LCD Screen (optional)
- Breadboard
- Jumper Wires
- USB Cable

DHT Sensor

The DHT sensor is a popular, low-cost sensor for measuring temperature and humidity. There are two common versions:

- DHT11: ±2°C temperature accuracy, 20-90% RH humidity accuracy
- DHT22: ±0.5°C temperature accuracy, 0-100% RH humidity accuracy

Project Objectives

1. Interface DHT sensor with Arduino
2. Read temperature and humidity data from DHT sensor
3. Display readings on LCD screen or serial monitor
4. Monitor ambient temperature and humidity levels

Circuit Connection

1. Connect VCC pin of DHT sensor to Arduino's 5V pin
2. Connect GND pin of DHT sensor to Arduino's GND pin
3. Connect DATA pin of DHT sensor to Arduino's digital pin (e.g., D2)
4. Connect LCD screen's VCC, GND, SCL, and SDA pins to Arduino's corresponding pins (if using LCD)

Software Requirements

1. Arduino IDE
2. DHT library (install via Library Manager)

Code Overview

The code reads temperature and humidity data from the DHT sensor using the DHT library. It then displays the readings on the serial monitor or LCD screen.

Example Code:-
const int analogIn = A0;
int humiditysensorOutput = 0;
// Defining Variables
int RawValue= 0;
double Voltage = 0;
double tempC = 0;
double tempF = 0;

void setup(){  
  Serial.begin(9600);
  pinMode(A1, INPUT);
}

void loop(){
  
  RawValue = analogRead(analogIn);
  Voltage = (RawValue / 1023.0) * 5000; // 5000 to get millivots.
  tempC = (Voltage-500) * 0.1; // 500 is the offset
  tempF = (tempC * 1.8) + 32; // convert to F  
  Serial.print("Raw Value = " );                  
  Serial.print(RawValue);      
  Serial.print("\t milli volts = ");
  Serial.print(Voltage,0); //
  Serial.print("\t Temperature in C = ");
  Serial.print(tempC,1);
  Serial.print("\t Temperature in F = ");
  Serial.println(tempF,1);
  humiditysensorOutput = analogRead(A1);
  Serial.print("Humidity: "); // Printing out Humidity Percentage
  Serial.print(map(humiditysensorOutput, 0, 1023, 10, 70));
  Serial.println("%");

  delay(5000);  //iterate every 5 seconds

}

  

Project Applications

1. Weather monitoring stations
2. Indoor climate control systems
3. Greenhouse automation
4. Industrial process monitoring

Tips and Variations

- Use a relay module to control heating/cooling systems based on temperature readings
- Add a real-time clock module to log data with timestamps
- Use Wi-Fi or Bluetooth modules to send data to online platforms or mobile apps
- Experiment with different DHT sensor types and accuracy levels

This project provides a basic framework for temperature and humidity monitoring using DHT sensors and Arduino. You can expand upon this project by incorporating additional features and components.
