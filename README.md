// Relay and Motor Pins
const int relayPin = 26;  // Relay connected to GPIO 26

// Stepper Motor Pins
const int dirPin = 18;    // Direction pin
const int stepPin = 19;   // Step pulse pin
const int enPin = 21;     // Enable pin

// Serial Input Variable
String incomingCommand;

void setup() {
  // Initialize Relay Pin
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH);  // Ensure relay is off initially

  // Initialize Stepper Motor Pins
  pinMode(stepPin, OUTPUT);
  pinMode(dirPin, OUTPUT);
  pinMode(enPin, OUTPUT);
  digitalWrite(enPin, LOW);  // Enable stepper driver (LOW to enable)

  // Start Serial Communication
  Serial.begin(115200);
  Serial.println("System Initialized.");
  Serial.println("Send '1000' to activate the relay and rotate the motor.");
}

void startMotor(int speedDelayMicroseconds, int steps) {
  // Rotate Motor Clockwise
  Serial.println("Motor rotating clockwise...");
  digitalWrite(dirPin, HIGH); // Set direction
  for (int x = 0; x < steps; x++) {
    digitalWrite(stepPin, HIGH);
    delayMicroseconds(speedDelayMicroseconds);
    digitalWrite(stepPin, LOW);
    delayMicroseconds(speedDelayMicroseconds);
  }

  delay(5000); // Pause before reversing direction

  // Rotate Motor Counterclockwise
  Serial.println("Motor rotating counterclockwise...");
  digitalWrite(dirPin, LOW); // Reverse direction
  for (int x = 0; x < steps; x++) {
    digitalWrite(stepPin, HIGH);
    delayMicroseconds(speedDelayMicroseconds);
    digitalWrite(stepPin, LOW);
    delayMicroseconds(speedDelayMicroseconds);
  }

  Serial.println("Motor rotation sequence complete.");
}

void loop() {
  // Check for Serial Input
  if (Serial.available() > 0) {
    incomingCommand = Serial.readStringUntil('\n');
    incomingCommand.trim(); // Remove any trailing newline characters

    if (incomingCommand.equals("1000")) {
      // Activate Relay
      Serial.println("Activating relay...");
      digitalWrite(relayPin, LOW);  // Turn relay on
      delay(1000);                  // Keep relay on for 1 second
      digitalWrite(relayPin, HIGH); // Turn relay off
      Serial.println("Relay deactivated.");

      // Rotate Motor
      Serial.println("Starting motor rotation...");
      startMotor(200, 800); // Adjust delay and steps as needed
    } else {
      // Invalid Input Handling
      Serial.println("Invalid command. Send '1000' to activate the relay and rotate the motor.");
    }
  }
}
