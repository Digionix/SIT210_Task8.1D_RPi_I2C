
```
#include <Wire.h>

#define ADDRESS 0x05

int number = 0;
int input = 0;
int led = D6;


void setup() 
{
pinMode(led, OUTPUT);

Wire.begin(ADDRESS);

Wire.onReceive(GetData);

Wire.onRequest(SendData);


}

void loop() {

}


// Functions


void GetData(int ByteCount)
{
    
    while ( Wire.available() )
    {
        for (int i = 0; i < ByteCount; i++)
        {
            input = Wire.read();
            number = int(input);
        }
        
        if (number == 1)
        {
            digitalWrite(led, HIGH);
        }
        
        else if (number == 2)
        {
            digitalWrite(led, LOW);
        }
    }
}


void SendData()
{
    Wire.write(number);
    
}
```
