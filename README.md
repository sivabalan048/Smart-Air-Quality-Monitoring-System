# Smart-Air-Quality-Monitoring-System
This system that uses sensors to detect and monitor air pollutants, providing real-time data on air quality and alerting users to potential health risks.
// Smart Air Quality Monitoring System

#define GAS_PIN A0     // MQ-135 analog output pin to Arduino A0
#define BUZZER_PIN 7   // Buzzer pin for alert

int gasValue = 0;
int threshold = 300;   // Adjust experimentally

void setup() {
  Serial.begin(9600);
  pinMode(BUZZER_PIN, OUTPUT);
  digitalWrite(BUZZER_PIN, LOW);
  Serial.println("Smart Air Quality Monitoring System Started");
}

void loop() {
  gasValue = analogRead(GAS_PIN);   // Read sensor value
  Serial.print("Air Quality Value: ");
  Serial.println(gasValue);

  if (gasValue > threshold) {
    Serial.println("Warning: Poor Air Quality!");
    digitalWrite(BUZZER_PIN, HIGH);  // Turn buzzer ON
  } else {
    digitalWrite(BUZZER_PIN, LOW);   // Turn buzzer OFF
  }

  delay(1000); // 1 second delay
}
