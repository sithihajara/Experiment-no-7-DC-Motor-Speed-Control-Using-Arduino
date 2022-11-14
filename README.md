# Experiment-no-7-DC-Motor-Speed-Control-Using-Arduino
### AIM : To control the speed and the direction of a DC motor using L293D driver ic( H- bridge)

### Components Required:
•	Arduino UNO board
•	L293D driver
•	12V DC motor
•	10K ohm potentiometer
•	Pushbutton
•	12V source
•	Breadboard
•	Jumper wires
### THEORY 
The L293D quadruple half-H drivers chip allows us to drive 2 motors in both directions, with two PWM outputs from the Arduino we can easily control the speed as well as the direction of rotation of one DC motor. (PWM: Pulse Width Modulation).
Arduino DC motor control circuit:
Project circuit schematic diagram is the one below.

![image](https://user-images.githubusercontent.com/36288975/167763051-b230c183-afc5-46f2-ba95-0f95e10dd6c9.png)
FIGURE-01 H BRIDGE CIRUCIT INTERFACE 
 
The speed of the DC motor (both directions) is controlled with the 10k potentiometer which is connected to analog channel 0 (A0) and the direction of rotation is controlled with the push button which is connected to pin 8 of the Arduino UNO board. If the button is pressed the motor will change its direction directly.
The L293D driver has 2 VCCs: VCC1 is +5V and VCC2 is +12V (same as motor nominal voltage). Pins IN1 and IN2 are the control pins where:
![image](https://user-images.githubusercontent.com/36288975/167763120-1421c2c5-8381-49eb-b376-03f6e1113b7a.png)
TABLE-01 EXITATION TABLE FOR H BRIDGE 

As shown in the circuit diagram we need only 3 Arduino terminal pins, pin 8 is for the push button which toggles the motor direction of rotation. Pins 9 and 10 are PWM signal outputs, at any time there is only 1 active PWM, this allows us to control the direction as well as the speed by varying the duty cycle of the PWM signal. The active PWM pin decides the motor direction of rotation (one at a time, the other output is logic 0).

## PRGORAM 
###PROGRAM TO MAKE DC MOTOR ROTATE
```
const int motorpin1 = 5;
const int motorpin2 = 6;

void setup()
{
  pinMode(motorpin1, OUTPUT);
  pinMode(motorpin2, OUTPUT);
}

void loop()
{
  digitalWrite(motorpin1, HIGH);
  delay(2000);
  digitalWrite(motorpin2, LOW);
  delay(2000);
}
```
##PROGRAM TO CONTROL DC MOTOR ROTATION
```
#define motorIn1 5
#define motorIn2 6

void setup()
{
  pinMode(motorIn1,OUTPUT);
  pinMode(motorIn2,OUTPUT);
}
void loop()
{
  clockwise(0);
  delay(3000);
  counterclockwise(50);
  delay(3000);
}
void counterclockwise(int speed)
{
  analogWrite(motorIn1,speed);
  analogWrite(motorIn2,0);
}

void clockwise(int speed)
{
  
  analogWrite(motorIn1,0);
  analogWrite(motorIn2,speed);
}
```
### CIRCUIT DIAGRAM
![198868191-ba5cfb66-4a9b-4e8c-bdf6-e99989a160a4](https://user-images.githubusercontent.com/94219582/201653798-4e19bc35-5020-4f14-bcee-da25091b1f87.png)
### OUTPUT
### GRAPH AND TABULATION
### CLOCKWISE
![198868197-cd2ce5bb-1641-4ceb-b18c-a3e3970cd642](https://user-images.githubusercontent.com/94219582/201654104-093436cf-4b84-4687-aeaa-145d74f1099e.png)
![198868197-cd2ce5bb-1641-4ceb-b18c-a3e3970cd642](https://user-images.githubusercontent.com/94219582/201654135-7b96890d-26be-4d34-94ba-796d3e5731e9.png)
### COUNTER CLOCKWISE
![198868218-a52b4338-015a-4e4c-8d50-f85d6d81a2bf](https://user-images.githubusercontent.com/94219582/201654270-ff4a9aaa-d9d1-4884-a20f-9c538b3acbdb.png)
![198868218-a52b4338-015a-4e4c-8d50-f85d6d81a2bf](https://user-images.githubusercontent.com/94219582/201654331-20744da5-6582-4328-b96a-d3a1b67bac3b.png)
### RESULTS AND DISCUSSION
Thus, the speed and the direction of a DC motor using L293D driver ic( H- bridge) is controlled.
