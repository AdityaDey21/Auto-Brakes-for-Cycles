# Auto-Brakes-for-Cycles
So I was thinking of making some project, had some cool ideas. Also started working on something, but one day I was getting back from somewhere and witnessed an accident. It got me thinking, if there was something that could be done about it. So, I decided to make an automatic brake. That will reduce the number of accidents even if the driver isn't attentive. So, I saterted doing my research. There were different types of brakes on numerous different types of vehicles. So, I needed to choose the easy one to start. BIKES!!!
Yup, lesser wheels, easier to stop using brake. But, bikes had four types of brakes and cycles had three. So, I decided to work on mechanical disc brakes.
I needed something that can pull the brake string whenever the bike/cycle gets too close to something. 
Now, making something react with distance as input was ez. Got my ULTRASONIC DISTANCE SENSOR. 
Now, as for the machanism to pull the string. Ummmmmm, it got me thinking hard. May be RACK AND PINION? or Lead Screw?
But, none of them were available to me, so I tried a motor that'll roll in the string and lossen it. So, may be a Servo motor will do!!!

So, I started on it and did this code for ARDUINO.

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

Here comes the schematics for the Circuit.
![PROJECT](https://user-images.githubusercontent.com/94229992/142219814-4d6736d6-9931-42fd-ac32-76c6db90b69f.png)

Now, I've made the mechanism but never experimented it practically. So, some modification should be needed for that.

~THANK YOU!!!
