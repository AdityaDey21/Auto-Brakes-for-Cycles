```C
#include<Servo.h>
int trig=2;
int echo=4;
int dt=10;
Servo servo;


void setup()
{
pinMode(trig,OUTPUT);
pinMode(echo,INPUT);
Serial.begin(9600);
servo.attach(11);
}

void loop() {


if (dist()>20) //I've put 20 as the distance, this should be modified for practical use
{
  servo.write(0);              
  delay(500);    //I've noticed much less than 500 as delay is too less time for the SERVO to rotate, so I recomend not to reduce too much, the SERVO acts kinda funny 
}
else
{
  servo.write(90);  //Now, as for the rotation if 90 degree is enough to pull the brake string then good but, feel free to change this as well
}
}

//This code is written to calculate the DISTANCE using ULTRASONIC SENSOR

int dist()
{
  // Clear the trigPin by setting it LOW
  digitalWrite(trig, LOW);
  delayMicroseconds(5);
  // Trigger the sensor by setting the trigPin high for 10 microseconds:
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);
  // Read the echoPin, pulseIn() returns the duration (length of the pulse) in microseconds:
  int duration = pulseIn(echo, HIGH);
  // Calculate the distance:
  int distance = duration * 0.034 / 2;
  // Print the distance on the Serial Monitor (Ctrl+Shift+M):
  Serial.print("Distance = ");
  Serial.print(distance);
  Serial.println(" cm");
  delay(50);
  return distance;
}
```
