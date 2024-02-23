#include <Servo.h>

// Define motor pins
const int leftMotorPin1 = 2;  // Left motor pin 1
const int leftMotorPin2 = 3;  // Left motor pin 2
const int rightMotorPin1 = 4; // Right motor pin 1
const int rightMotorPin2 = 5; // Right motor pin 2

// Define ultrasonic sensor pins
const int trigPin = 6;  // Trigger pin
const int echoPin = 7;  // Echo pin

// Define servo pin
const int servoPin = 8; // Servo motor pin

// Define obstacle detection threshold (in centimeters)
const int obstacleThreshold = 20; 

// Create servo object
Servo cuttingServo;

void setup() {
  // Motor pins setup
  pinMode(leftMotorPin1, OUTPUT);
  pinMode(leftMotorPin2, OUTPUT);
  pinMode(rightMotorPin1, OUTPUT);
  pinMode(rightMotorPin2, OUTPUT);

  // Ultrasonic sensor pins setup
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  // Servo pin setup
  cuttingServo.attach(servoPin);

  // Initialize serial communication
  Serial.begin(9600);
}

void loop() {
  // Measure distance from ultrasonic sensor
  int distance = measureDistance();

  // Check for obstacles
  if (distance <= obstacleThreshold) {
    // Stop motors if obstacle detected
    stopMotors();
  } else {
    // Move forward if no obstacle
    moveForward();
  }

  // Control cutting mechanism
  controlCuttingMechanism();
}

// Function to measure distance using ultrasonic sensor
int measureDistance() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  int duration = pulseIn(echoPin, HIGH);
  int distance = duration * 0.034 / 2;  // Calculate distance in cm

  return distance;
}

// Function to control the movement of the prototype
void moveForward() {
  digitalWrite(leftMotorPin1, HIGH);
  digitalWrite(leftMotorPin2, LOW);
  digitalWrite(rightMotorPin1, HIGH);
  digitalWrite(rightMotorPin2, LOW);
}

// Function to stop the movement of the prototype
void stopMotors() {
  digitalWrite(leftMotorPin1, LOW);
  digitalWrite(leftMotorPin2, LOW);
  digitalWrite(rightMotorPin1, LOW);
  digitalWrite(rightMotorPin2, LOW);
}

// Function to control the cutting mechanism
void controlCuttingMechanism() {
  // Example: Move servo motor to a certain angle
  cuttingServo.write(90); // Adjust angle as needed
}
