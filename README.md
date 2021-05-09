int led = D7;

void setup()
{
    pinMode(led, OUTPUT);
    Particle.subscribe("Deakin_RIOT_SIT210_Photon_Buddy",Buddy );
}

void loop()
{
    Particle.publish("Deakin_RIOT_SIT210_Photon_Buddy", "wave");
    delay(2000);
    Particle.publish("Deakin_RIOT_SIT210_Photon_Buddy", "pat");
    delay(3000);
    
}
void Buddy(const char *event, const char *data)
{
    if(strcmp(data, "wave") == 0)
    {
        //flash led 3 times while receiving "wave"
        Particle.publish(String::format(event));
        digitalWrite(led, HIGH); 
        delay(1500);
        digitalWrite(led, LOW);
        delay(1500);
        digitalWrite(led, HIGH);
        delay(1500);
        digitalWrite(led, LOW);
        delay(1500);
        digitalWrite(led, HIGH);
        delay(1500);
        digitalWrite(led, LOW);
        delay(3000);
        
    }
    else if (strcmp(data, "pat") == 0)
    {
        Particle.publish(String::format(event));
        digitalWrite(led, HIGH);
        delay(700);
        digitalWrite(led, LOW);
        delay(700);
        digitalWrite(led, HIGH);
        delay(700);
        digitalWrite(led, LOW);
        delay(2000);
        
    }
    
}
