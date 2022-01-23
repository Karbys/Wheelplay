#include "TimerOne.h"
unsigned int counter=0;
const int Sleep=3;
float rps;
//float carRotation;
void docount()  // counts from the speed sensor
{
  counter++;  // increase +1 the counter valu1
} 

void loop()
{
  float rotation = (counter / (float)8); // จำนวนเม็ดเที่ผ่าน / จำนวนเม็ดทั้งหมด ต่อช่วงเวลา 
  rps = rotation     ; 
  // divide by number of holes in Disc
  Serial.print(rps,DEC);   
  counter=0;  //  reset counter to zero
  Serial.print(","); 
  //carRotation = analogRead(A0);
  //Serial.println(carRotation);
  Serial.println(digitalRead(7));//1=strait, 0=left
//  Timer1.attachInterrupt( timerIsr );  //enable the timer
}

void setup() 
{
  Serial.begin(9600);
  pinMode(3, INPUT);
  //Timer1.initialize(100000); // set timer for 1sec
  attachInterrupt(0, docount, FALLING);  // increase counter when speed sensor pin goes High
 // Timer1.attachInterrupt( timerIsr ); // enable the timer
} 
