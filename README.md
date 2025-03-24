# Maze-decoder 
#define MOTOR_LEFT_FORWARD  18  
#define MOTOR_LEFT_BACKWARD 19  
#define MOTOR_RIGHT_FORWARD 21  
#define MOTOR_RIGHT_BACKWARD 22  

#define ULTRASONIC_LEFT  32  
#define ULTRASONIC_FRONT 33  
#define ULTRASONIC_RIGHT 34  

int threshold = 15;  // Obstacle detection distance (cm)

// Setup function
void setup() {
    Serial.begin(115200);
}

// Main loop
void loop() {
    int leftDist = getDistance(ULTRASONIC_LEFT);
    int frontDist = getDistance(ULTRASONIC_FRONT);
    int rightDist = getDistance(ULTRASONIC_RIGHT);

    // 8 Different Movement Cases
    
}

// Function to get distance from ultrasonic sensor
int getDistance(int pin) {
    digitalWrite(pin, HIGH);
    delayMicroseconds(10);
    digitalWrite(pin, LOW);
    int duration = pulseIn(pin, HIGH);
    return duration * 0.034 / 2;  // Convert to cm
}

// Motor Control Functions
void moveForward() {
    digitalWrite(MOTOR_LEFT_FORWARD, HIGH);
    digitalWrite(MOTOR_LEFT_BACKWARD, LOW);
    digitalWrite(MOTOR_RIGHT_FORWARD, HIGH);
    digitalWrite(MOTOR_RIGHT_BACKWARD, LOW);
}

void turnRight() {
    digitalWrite(MOTOR_LEFT_FORWARD, HIGH);
    digitalWrite(MOTOR_RIGHT_FORWARD, LOW);
    delay(500);
}

void moveRightSlightly() {
    digitalWrite(MOTOR_LEFT_FORWARD, HIGH);
    delay(200);
}

void moveLeftSlightly() {
    digitalWrite(MOTOR_RIGHT_FORWARD, HIGH);
    delay(200);
}

void turnRightSharply() {
    digitalWrite(MOTOR_LEFT_FORWARD, HIGH);
    digitalWrite(MOTOR_RIGHT_BACKWARD, HIGH);
    delay(500);
}

void turnLeftSharply() {
    digitalWrite(MOTOR_LEFT_BACKWARD, HIGH);
    digitalWrite(MOTOR_RIGHT_FORWARD, HIGH);
    delay(500);
}

void moveForwardCarefully() {
    digitalWrite(MOTOR_LEFT_FORWARD, HIGH);
    digitalWrite(MOTOR_RIGHT_FORWARD, HIGH);
    delay(300);
}

void stopAndReverse() {
    digitalWrite(MOTOR_LEFT_FORWARD, LOW);
    digitalWrite(MOTOR_RIGHT_FORWARD, LOW);
    delay(300);
    turnRight();  // Turn after reversing
}
