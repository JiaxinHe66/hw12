Automatic bubble machine
One-sentence summary of your project goes here; then fill out each of the following sections.

Summary
I use Arduino to build my project. I mainly used two servos and a sensor. The sensor is an ultrasonic sensor that can trigger the bubble machine when someone approaches. Servo: a servo control arm dipped in bubble water and moved in front of the fan and the fan was triggered to rotate.

Component Parts
inputs: a servo and an ultrasonic sensor
outputs: two servos


When your project is completed, you will then add the following sections:
Timeline
What did you do in each of the past four weeks?

Week 0: Write Proposal
Week 1: drawing
Week 2: coding
Week 3: prototype
Week 4: Present!
Challenges
use one servo to control another servo

Completed Work
#define trigpin 5//set trigpin
#define echopin 6//set echopin
#include <Servo.h>
Servo myservo;// declare servo name type servo
  int duration, distance;//declare variable for unltrasonic sensor
  
void setup() {
  Serial.begin(9600);
  pinMode(trigpin, OUTPUT);
 
  pinMode(echopin, INPUT);
  myservo.attach(9);// attach your servo
myservo.writeMicroseconds(1500);
  // put your setup code here, to run once:
}
void loop() {
 myservo.write(90);// always set servo to 90 to position it to the middle
//ultrasonic code 
 digitalWrite(trigpin,HIGH);
  _delay_ms(500);
  digitalWrite(trigpin, LOW);
  
  duration=pulseIn(echopin,HIGH); 
  distance=(duration/2)/29.1; 
 if(distance <=40)// if ultrasonic sensor detects an obstacle less than 20cm in 90 degree angle.
 {
 myservo.write(0); //servo rotates at full speed to the right
 delay(600);
}
else
{
  myservo.write(90);// else servo stays at 90 degree angle.
  delay(600);
}
  Serial.print("cm"); //print distance unit cm
Serial.println(distance);//distance
 
}
References and links
Tutorials, comments, videos, magazine articles - anything you found that helps you understand your project.
