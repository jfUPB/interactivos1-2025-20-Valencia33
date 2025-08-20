# Unidad 3


## 🛠 Fase: Apply

no está terminado

```javascript
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
    this.password = ['A','B','C']
    this.key = [];
    this.conteo = 20;
    this.startTime = 0;
    this.state = 'CONFIG'
    this.displayInstruction;
    
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
        if((millis()-this.startTime) > (this.conteo*1000) )
          {
            this.state = "EXPLODED"
          }
      }
      
      if(this.state === "EXPLODED")
        {
          this.displayInstruction = 0
          
          if(key === 'a')
            {
              this.state = 'CONFIG'
            }
        }
  }
  
    display(){
      
      if(this.state == "CONFIG")
      {
        circle(200,200,100)
        textSize(20)
        fill(255,30,30)
        text("CONFIG", 200, 100)
        text(str(this.conteo),200,120)
        
        fill(20,20,50)
        
        if(this.displayInstruction == 0)
          {
            fill(50,20,20)
            circle(200,200,100)
            fill(20,20,50)
          }        
        if(this.displayInstruction == 1)
          {
            fill(200,200,200)
            rect(200,100,330,75,20)
            fill(0,0,0)
            text("El conteo no puede ser mayor a 60", 200,100)
            
            fill(20,20,50)
          }
        if(this.displayInstruction == 2)
          {
            fill(200,200,200)
            rect(200,100,330,75,20)
            fill(0,0,0)
            text("El conteo no puede ser menor a 10", 200,100)
            
            fill(20,20,50)
          }
      }
      
      if(this.state == "ARMED")
        { 
          
          text(str(int(millis()-this.startTime)), 30,30)
          
          if((millis() - this.startTime) % 500 == 0)
            {
              fill(50,20,20)
            }
          if((millis() - this.startTime) % 500 != 0)
            {
              fill(20,20,50)        
            }  
          
          circle(200,200,100)
          
          fill(255,20,20)
          text("ARMED", 200, 100)
          text(str(int(this.conteo-(millis() - this.startTime)/1000)), 200,120)
        }
  }
}

function draw() {
  background(220);
  bomba1.update()
  bomba1.display()  
}

```
