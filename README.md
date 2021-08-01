# ultrasonic-sensor-
an ultrasonic that sense a customer to move 6 servo motor
# elements of the circuit 
- 220ohm resistor
- ultrasonic resistor
- led light 
# picture of the circuit
![‏‏لقطة الشاشة (4)](https://user-images.githubusercontent.com/86115930/127778034-10fee0ed-321e-47ff-838a-4b1b4dc62b9b.png)
# circuit figure 
https://www.tinkercad.com/things/kxTNkci0oXq-powerful-juttuli-waasa/editel
# code
```
#include <IRremote.h>

// C++ code
//
#define echoPin 5 //attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 7 //attach pin D3 Arduino to pin Echo of HC-SR04

//define variables 
long duration;
int distance;
int startTime;
int currentTime;

void setup(){
pinMode(trigPin, OUTPUT);
pinMode(11,OUTPUT);
pinMode(echoPin,INPUT);
Serial.begin(9600);
}


void loop(){
  while(getDistance() > 25)  
  {
     startTime = millis();
  }
  while(getDistance()<25){      
  	 currentTime= millis();
  
  	if (currentTime -startTime > 3000)
  		{  
  		digitalWrite(11,HIGH);	
    	delay(2000);
    	digitalWrite(11,HIGH);
    	break;   
 	}
  }
} 
int getDistance(){
  // clear the trigpin condition 
  digitalWrite(trigPin,LOW);
  delayMicroseconds(2);
  //sets the trigpin HIGH (ACTIVE) for 10 microsecond
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin, LOW);
  //reads the echo pin , return the sound wave travel in microsecond
  duration = pulseIn(echoPin,HIGH);
  //calculation distance
  distance = duration * 0.34/2; 
  //diplay the distance on the serial monitor
  return distance;
}
```



