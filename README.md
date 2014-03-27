tarea-1
=======
//secuancia de encendido de led 



#define pinBoton_1 11
#define pinBoton_2 10

#define pinLed_rojo 13
#define pinLed_verde 12

boolean rutinaOn=false;
unsigned long time_1;
unsigned long deltaT;
int ciclo;

void setup(){
  pinMode(pinBoton_1,INPUT);
  pinMode(pinBoton_2,INPUT);
  pinMode(pinLed_rojo,OUTPUT);
  pinMode(pinLed_verde,OUTPUT);

}
void loop(){
  if(digitalRead(pinBoton_1)==HIGH && !rutinaOn){
    rutinaOn=true;
    time_1=millis(); //tiempo de partida 
    digitalWrite(pinLed_rojo,HIGH);
  }
  if(rutinaOn)
  deltaT=millis()-time_1;
  Serial.print("tiempo:");
  Serial.println(deltaT);
  if(deltaT>3000 && digitalRead(pinBoton_2)==HIGH && deltaT<10000)
  {
    digitalWrite(pinLed_rojo,HIGH);
    falsodelay(500);
    digitalWrite(pinLed_rojo,LOW);
    falsodelay(500);
  }
  if(deltaT>3000 && digitalRead(pinBoton_2)==LOW && deltaT<10000 )
  {
    digitalWrite(pinLed_rojo,HIGH);
  }
  if(deltaT>2000 && deltaT<7000)
  {
    digitalWrite(pinLed_verde,HIGH);
  }
  else
  {
    digitalWrite(pinLed_verde,LOW);
  }
  if(deltaT>=10000){
    digitalWrite(pinLed_rojo,LOW);
    rutinaOn=false;
  }

}
void falsodelay(int tiempo)

{
  unsigned long tiemporeal=millis();//variable local falsodelay
  unsigned long tiempobase=tiemporeal;//variable local falsodelay
   
      for(;tiemporeal-tiempobase <= tiempo ; tiemporeal=millis())
 
          {
             //Un delay falso de "tiempo" milisegundos 
          } 
  
}





