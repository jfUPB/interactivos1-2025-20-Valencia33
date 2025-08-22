# Unidad 3


## 🛠 Fase: Apply

🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 06 🐟

__p5.js__

```js
function setup() {
  createCanvas(400, 400);
  frameRate(30)
  textAlign(CENTER)
  textFont('Comic Sans MS');
  rectMode(CENTER)
  bomba1 = new Bomb()
}

class Bomb {
  constructor()
  {
    this.password = ['A','B','A']
    this.keyArray = [];
    this.keyindex = 0;
    this.passIsOk = 0
    
    this.conteo = 20;
    this.startTime = 0;
    this.explosionTime = 3000;
    
    this.state = 'CONFIG'
    this.displayInstruction = -1;
    
  }
  
    update(){      
     if(this.state === 'CONFIG')
     {     
      if(key === "a")
        {
          key = ""
          this.conteo += 1;
          this.displayInstruction = 0;
        }
      if(key === "b")
        {
          key = ""
          this.conteo -= 1;
          this.displayInstruction = 0;
        }
       if(key === "s")
         {
           key = ""
           this.state = "ARMED"
           this.startTime = millis()
         }
       
       if(this.conteo > 60)
         {
           this.conteo = 60;
           this.displayInstruction = 1;
         }
       
       if(this.conteo < 10)
         {
           this.conteo = 10;
           this.displayInstruction = 2;
         }
    }
      
      if(this.state === 'ARMED'){    
            if(key === 'a')
              {
                key = ''
                this.keyArray[this.keyindex] = 'A'
                this.keyindex++
              }
            
            if(key === 'b')
              {
                key = ''
                this.keyArray[this.keyindex] = 'B'
                this.keyindex++
              }
        
        text(str(this.keyArray[0] ),30,30)
        text(str(this.keyArray[1] ),30,60)
        text(str(this.keyArray[2] ),30,90)
        text(str(this.keyindex),30,120)
        text(str(this.passIsOk),30,150)
        
         this.passIsOk = false
        
        if(this.keyindex == this.password.length)
          {
            
            for(let i = 0; i < this.password.length; i++)
              {
                if(this.keyArray[i] == this.password[i])
                  {
                    this.passIsOk = true
                  }
              }
          }
        
        if(this.passIsOk)
          {
            this.state = "CONFIG"
            this.conteo = 20
            this.keyindex = 0
            this.passIsOK = false
            
            for(let i = 0; i<this.keyArray.length; i++)
              {
                this.keyArray[i] = " "
              }
            
          }

        if((millis()-this.startTime) > (this.conteo*1000) )
          {
            this.state = "EXPLODED"
            this.startTime = millis()
          }
      }
      
      if(this.state === "EXPLODED")
        {
          
          if((millis() - this.startTime) > this.explosionTime)
            {
              this.displayInstruction = 1
            }
          else
            {
              this.displayInstruction = 0
            }
          
          if(key === 'a')
            {
              key = ""
              this.state = 'CONFIG'
              this.conteo = 20
            }
        }
  }
  
    display(){   
      
        noStroke()
        fill(200,200,200)
        ellipse(200,250,150,40)
      
      if(this.state == "CONFIG")
      {
        fill(20,20,50)
        circle(200,200,100)
        textSize(20)
        fill(30,30,30)
        text("CONFIG", 200, 100)
        text(str(this.conteo),200,120)
        fill(150,150,150)
        text("Presiona 's' para activar la bomba", 170,385)
             
        if(this.displayInstruction == 1)
          {
            fill(200,100,100)
            rect(200,100,330,75,20)
            fill(0,0,0)
            text("El conteo no puede ser mayor a 60", 200,100)
            
            fill(20,20,50)
          }
        if(this.displayInstruction == 2)
          {
            fill(200,100,100)
            rect(200,100,330,75,20) 
            fill(0,0,0)
            text("El conteo no puede ser menor a 10", 200,100)
            
            fill(20,20,50)
          }
      }
      
      if(this.state == "ARMED")
        { 
          
          fill(20,20,50)
          
          if((millis() - this.colorInterval) > 500)
            {
              fill(50,20,20) //solucionar que cambie de color cada 500ms
            }
          
          circle(200,200,100)
          
          fill(255,20,20)
          text("ARMED", 200, 100)
          text(str(int(this.conteo-(millis() - this.startTime)/1000)), 200,120)
        }
      
      if(this.state == "EXPLODED")
        {
          if(this.displayInstruction == 0)
            {
              fill(200,200,20)
              ellipse(200,200,random(1,3)*((millis()-this.startTime)/10),random(1,3)*(millis()/10))
              fill(200,150,20)
              ellipse(200,200,random(1,3)*((millis()-this.startTime)/20),random(1,3)*(millis()/20))
              fill(200,70,20)
              ellipse(200,200,random(1,3)*((millis()-this.startTime)/30),random(1,3)*(millis()/30))
            }
          if(this.displayInstruction == 1)
            {
              fill(20,20,20,millis()/10)
              square(200,200,400)
              fill(255,255,255)
              text("Presione 'a' para reiniciar",200,200)
            }
        }
  }
}

function draw() {
  background(220);
  bomba1.update()
  bomba1.display()  
}
```

🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 07 🐟

p5js con micro bit

Profe no tenía el microbit entonces ni idea si quedó bueno. :(

```js
let port;
let connectBtn;

function setup() {
  createCanvas(400, 400);
  frameRate(30)
  textAlign(CENTER)
  textFont('Comic Sans MS');
  rectMode(CENTER)
  
      port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  
  bomba1 = new Bomb()
}

class Bomb {
  constructor()
  {
    this.password = ['A','B','A']
    this.keyArray = [];
    this.keyindex = 0;
    this.passIsOk = 0
    
    this.conteo = 20;
    this.startTime = 0;
    this.explosionTime = 3000;
    
    this.state = 'CONFIG'
    this.displayInstruction = -1;
    
  }
  
  
    serial(){
      
        if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A'){
            key = "a"
        }
        else if(dataRx == 'B'){
            key = "b"
        }
        else if(dataRx == 'S'){
            key = "s"
        }
    }

    if (!port.opened()) {
        connectBtn.html('Connect to micro:bit');
    }
    else {
        connectBtn.html('Disconnect');
    }
    }
  
    update(){      
     if(this.state === 'CONFIG')
     {     
      if(key === "a")
        {
          key = ""
          this.conteo += 1;
          this.displayInstruction = 0;
        }
      if(key === "b")
        {
          key = ""
          this.conteo -= 1;
          this.displayInstruction = 0;
        }
       if(key === "s")
         {
           key = ""
           this.state = "ARMED"
           this.startTime = millis()
         }
       
       if(this.conteo > 60)
         {
           this.conteo = 60;
           this.displayInstruction = 1;
         }
       
       if(this.conteo < 10)
         {
           this.conteo = 10;
           this.displayInstruction = 2;
         }
    }
      
      if(this.state === 'ARMED'){    
            if(key === 'a')
              {
                key = ''
                this.keyArray[this.keyindex] = 'A'
                this.keyindex++
              }
            
            if(key === 'b')
              {
                key = ''
                this.keyArray[this.keyindex] = 'B'
                this.keyindex++
              }
        
        text(str(this.keyArray[0] ),30,30)
        text(str(this.keyArray[1] ),30,60)
        text(str(this.keyArray[2] ),30,90)
        text(str(this.keyindex),30,120)
        text(str(this.passIsOk),30,150)

         this.passIsOk = false
        
        if(this.keyindex == this.password.length)
          {
            
            for(let i = 0; i < this.password.length; i++)
              {
                if(this.keyArray[i] == this.password[i])
                  {
                    this.passIsOk = true
                  }
              }
          }
        
        if(this.passIsOk)
          {
            this.state = "CONFIG"
            this.conteo = 20
            this.keyindex = 0
            this.passIsOK = false
            
            for(let i = 0; i<this.keyArray.length; i++)
              {
                this.keyArray[i] = " "
              }
            
          }

        if((millis()-this.startTime) > (this.conteo*1000) )
          {
            this.state = "EXPLODED"
            this.startTime = millis()
          }
      }
      
      if(this.state === "EXPLODED")
        {
          
          if((millis() - this.startTime) > this.explosionTime)
            {
              this.displayInstruction = 1
            }
          else
            {
              this.displayInstruction = 0
            }
          
          if(key === 'a')
            {
              key = ""
              this.state = 'CONFIG'
              this.conteo = 20
            }
        }
  }
  
    display(){   
      
        noStroke()
        fill(200,200,200)
        ellipse(200,250,150,40)
      
      if(this.state == "CONFIG")
      {
        fill(20,20,50)
        circle(200,200,100)
        textSize(20)
        fill(30,30,30)
        text("CONFIG", 200, 100)
        text(str(this.conteo),200,120)
        fill(150,150,150)
        text("Presiona 's' para activar la bomba", 170,385)
             
        if(this.displayInstruction == 1)
          {
            fill(200,100,100)
            rect(200,100,330,75,20)
            fill(0,0,0)
            text("El conteo no puede ser mayor a 60", 200,100)
            
            fill(20,20,50)
          }
        if(this.displayInstruction == 2)
          {
            fill(200,100,100)
            rect(200,100,330,75,20) 
            fill(0,0,0)
            text("El conteo no puede ser menor a 10", 200,100)
            
            fill(20,20,50)
          }
      }
      
      if(this.state == "ARMED")
        { 
          
          fill(20,20,50)
          
          if((millis() - this.colorInterval) > 500)
            {
              fill(50,20,20) //solucionar que cambie de color cada 500ms
            }
          
          circle(200,200,100)
          
          fill(255,20,20)
          text("ARMED", 200, 100)
          text(str(int(this.conteo-(millis() - this.startTime)/1000)), 200,120)
        }
      
      if(this.state == "EXPLODED")
        {
          if(this.displayInstruction == 0)
            {
              fill(200,200,20)
              ellipse(200,200,random(1,3)*((millis()-this.startTime)/10),random(1,3)*(millis()/10))
              fill(200,150,20)
              ellipse(200,200,random(1,3)*((millis()-this.startTime)/20),random(1,3)*(millis()/20))
              fill(200,70,20)
              ellipse(200,200,random(1,3)*((millis()-this.startTime)/30),random(1,3)*(millis()/30))
            }
          if(this.displayInstruction == 1)
            {
              fill(20,20,20,millis()/10)
              square(200,200,400)
              fill(255,255,255)
              text("Presione 'a' para reiniciar",200,200)
            }
        }
  }
}

function draw() {
  background(220);
  bomba1.serial()
  bomba1.update()
  bomba1.display()  
}

function connectBtnClick() {
    if (!port.opened()) {
        port.open('MicroPython', 115200);
    } else {
        port.close();
    }
}
```

```py
from microbit import *

uart.init(baudrate=115200)

while True:
    if button_a.is_pressed():
        uart.write('A')
    if button_b.is_pressed():
        uart.write('B')
    if accelerometer.was_gesture('shake'):
        uart.write('S')

```


