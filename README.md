# MAX31865 Library

* http://www.github.com/NimaLTD   
* https://www.instagram.com/github.nimaltd/   
* https://www.youtube.com/channel/UCUhY7qY1klJm1d2kulr9ckw   

This is the MAX31856 STM32 HAL Library  
Based on https://github.com/adafruit/Adafruit_MAX31865      

Installing Library:
* Select "General peripheral Initalizion as a pair of '.c/.h' file per peripheral" on project settings.   
* Enable SPI and set clock below 2MHz,MSB,CPOL LOW,CPHA 2 Edge.   
* Enable a gpio as Output for CS Pin.  
* Include Header and source into your project.   
* Config "Max31865Conf.h".   
* Call Max31865_Init( .. .. .. ).   
```
#include "Max31865.h"
Max31865_t  pt100;
bool        pt100isOK;
float       pt100Temp;
int main()
{
  Max31865_init(&pt100,&hspi3,SENSOR_CS1_GPIO_Port,SENSOR_CS1_Pin,4,50);
  while(1)
  {
    float t;
    pt100isOK = Max31865_readTempC(&pt100,&t);
    pt100Temp = Max31865_Filter(t,pt100Temp,0.1);   //  << For Smoothing data  
    HAL_Delay(1000);
  }
}
```






