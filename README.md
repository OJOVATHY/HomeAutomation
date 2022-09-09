# HomeAutomation
The main objective of this project is to build a smart home device which can be used to control home appliances via Internet. This establishes Internet connection to the systems and all the home appliances can in turn be connected and controlled by Internet.


#include <ThingSpeak.h>
#include <ESP8266WiFi.h>
int pin1=D1;
int pin2=D2;
int pin3=D3;
int pin4=D4;
WiFiClient client;
unsigned long counterChannelNumber = "";
const char * myCounterReadAPIKey = "";
const int FieldNumber1 =  1;
const int FieldNumber2 =  2;
const int FieldNumber3 =  3;
const int FieldNumber4 =  4;

void setup()
{ pinMode(D1,OUTPUT);
pinMode(D2,OUTPUT);
pinMode(D3,OUTPUT);
pinMode(D4,OUTPUT);
Serial.begin(115200);
Serial.println();
WiFi.begin("Wifi Name", "Wifi password");  Serial.print("Connecting");
![image](https://user-images.githubusercontent.com/91971716/189369463-7daa5e27-2cf8-4078-a69c-addaf796107e.png)
while (WiFi.status() != WL_CONNECTED)
{
delay(500);ss
Serial.print(".");
Serial.println();
Serial.print("Connected, IP address: ");
}
Serial.println(WiFi.localIP());
ThingSpeak.begin(client);
}
void loop()
{
int a =  ThingSpeak.readLongField(counterChannelNumber, FieldNumber1, myCounterReadAPIKey);
int b =  ThingSpeak.readLongField(counterChannelNumber, FieldNumber2, myCounterReadAPIKey);
int c =  ThingSpeak.readLongField(counterChannelNumber, FieldNumber3, myCounterReadAPIKey);
int d =  ThingSpeak.readLongField(counterChannelNumber, FieldNumber4, myCounterReadAPIKey);
Serial.println(a);
Serial.println(b);
Serial.println(c);
Serial.println(d);
digitalWrite(D1,a);
digitalWrite(D2,b);
digitalWrite(D3,c);
digitalWrite(D4,d);
}

