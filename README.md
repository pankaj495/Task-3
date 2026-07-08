// Task 3: Smart Automatic Light Control and Alert System
// Prepared By: Pankaj - Maincraft Technologies Training Program

int ldrPin = A0;       // LDR Sensor connected to Analog Pin A0
int redLedPin = 2;     // Red LED connected to Digital Pin 2
int greenLedPin = 3;   // Green LED connected to Digital Pin 3
int buzzerPin = 4;     // Piezo Buzzer connected to Digital Pin 4

void setup() {
  pinMode(redLedPin, OUTPUT);
  pinMode(greenLedPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  
  Serial.begin(9600);  // Initialize Serial Monitor at 9600 baud rate
}

void loop() {
  int ldrValue = analogRead(ldrPin); // Read analog light intensity
  
  if (ldrValue < 500) {
    // Condition: Dark Environment Detected (LDR Value < 500)
    digitalWrite(redLedPin, HIGH);
    digitalWrite(greenLedPin, LOW);
    digitalWrite(buzzerPin, HIGH);   // Turn ON Buzzer Alert
    
    Serial.println("Dark Environment Detected");
    Serial.print("LDR Value = ");
    Serial.println(ldrValue);
  }
  else {
    // Condition: Bright Environment Detected (LDR Value >= 500)
    digitalWrite(redLedPin, LOW);
    digitalWrite(greenLedPin, HIGH);
    digitalWrite(buzzerPin, LOW);    // Turn OFF Buzzer Alert
    
    Serial.print("LDR Value = ");
    Serial.println(ldrValue);
    Serial.println("Bright Environment");
  }
  
  delay(1000); // 1-second delay between readings
}
