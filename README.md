# line_follower_aurdino

      // Define pin numbers for sensors
const int leftSensorPin = 2;  // Pin connected to the left sensor
const int rightSensorPin = 3; // Pin connected to the right sensor

// Define pin numbers for motor control
const int leftMotorPin1 = 4;  // Pin connected to the left motor input 1
const int leftMotorPin2 = 5;  // Pin connected to the left motor input 2
const int rightMotorPin1 = 6; // Pin connected to the right motor input 1
const int rightMotorPin2 = 7; // Pin connected to the right motor input 2

void setup() {
  // Initialize sensor pins as inputs
  pinMode(leftSensorPin, INPUT);
  pinMode(rightSensorPin, INPUT);
  
  // Initialize motor pins as outputs
  pinMode(leftMotorPin1, OUTPUT);
  pinMode(leftMotorPin2, OUTPUT);
  pinMode(rightMotorPin1, OUTPUT);
  pinMode(rightMotorPin2, OUTPUT);
}

void loop() {
  // Read sensor values
  int leftSensorValue = digitalRead(leftSensorPin);
  int rightSensorValue = digitalRead(rightSensorPin);

  // Check sensor readings and control the motors accordingly
  if (leftSensorValue == HIGH && rightSensorValue == HIGH) {
    // Both sensors are on the line, move forward
    moveForward();
  } else if (leftSensorValue == LOW && rightSensorValue == HIGH) {
    // Left sensor is off the line, turn right
    turnRight();
  } else if (leftSensorValue == HIGH && rightSensorValue == LOW) {
    // Right sensor is off the line, turn left
    turnLeft();
  } else {
    // Both sensors are off the line, stop
    stopMotors();
  }
}

void moveForward() {
  digitalWrite(leftMotorPin1, HIGH);
  digitalWrite(leftMotorPin2, LOW);
  digitalWrite(rightMotorPin1, HIGH);
  digitalWrite(rightMotorPin2, LOW);
}

void turnLeft() {
  digitalWrite(leftMotorPin1, LOW);
  digitalWrite(leftMotorPin2, HIGH);
  digitalWrite(rightMotorPin1, HIGH);
  digitalWrite(rightMotorPin2, LOW);
}

void turnRight() {
  digitalWrite(leftMotorPin1, HIGH);
  digitalWrite(leftMotorPin2, LOW);
  digitalWrite(rightMotorPin1, LOW);
  digitalWrite(rightMotorPin2, HIGH);
}

void stopMotors() {
  digitalWrite(leftMotorPin1, LOW);
  digitalWrite(leftMotorPin2, LOW);
  digitalWrite(rightMotorPin1, LOW);
  digitalWrite(rightMotorPin2, LOW);
}


