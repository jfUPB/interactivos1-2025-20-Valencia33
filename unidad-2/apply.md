# Unidad 2


## 🛠 Fase: Apply

🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 04 🐟 

```py
from microbit import *
import utime
import music

STATE_INIT = 0
STATE_CONFIG = 1
STATE_ARMED = 2
STATE_EXPLODE = 3

conteo = 20000;
start_time = 0;
resta =0;
current_state = STATE_INIT

while True:
    # pseudoestado STATE_INIT
    if current_state == STATE_INIT:
        display.show(Image.ASLEEP)
        current_state = STATE_CONFIG
        
    elif current_state == STATE_CONFIG:
        
        display.scroll(int(conteo/1000),delay=50)

        if conteo > 60000:
            display.show(Image.NO)
            conteo = 60000
        elif conteo < 10000:
            display.show(Image.NO)
            conteo = 10000
        
        if button_a.was_pressed():
            # Acciones para el evento
            conteo+=1000
            display.scroll(int(conteo/1000),delay=50)

        if button_b.was_pressed():
            # Acciones para el evento
            conteo-=1000
            display.scroll(int(conteo/1000),delay=50)
            
        elif accelerometer.was_gesture('shake'):
            current_state = STATE_ARMED
            start_time = utime.ticks_ms()     
            

    elif current_state == STATE_ARMED:
            resta = utime.ticks_ms()-start_time
            display.scroll(int((conteo-resta)/1000),delay=50)
            if(utime.ticks_diff(utime.ticks_ms(),start_time)>conteo):
                current_state = STATE_EXPLODE
                display.show(Image.SKULL)
                music.play(music.FUNERAL)  
    
    elif current_state == STATE_EXPLODE:
        if pin_logo.is_touched():
            current_state = STATE_CONFIG
            conteo = 20000
```

<img width="1251" height="1376" alt="PRACTICA 5" src="https://github.com/user-attachments/assets/bc46ab21-4f69-4fcb-b677-34f803c2aab8" />
