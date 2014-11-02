Robot-Tricks
============
#Diya Banerjee CS 1301-A3
#gt id: 903080103
#dbanerjee@gatech.edu
#"I worked on the homework assignment individually, and referred only to this semesters course materials

from Myro import *
from time import *

#Tricks: triangle(), alarm(), walk(), fetch()

def triangle():#Robot will draw a triangle on the ground

    forward(1,2)
    turnLeft(1,.75)
    forward(1,2)
    turnLeft(1,1)
    forward(1,2)
    

def alarm():#Robot will spin while beeping 
    for time in timer(5):
        rotate(1)
        beep(1,870,600)
     
    stop()
    for time in timer(5):
        rotate(-1)
        beep(1,970,700)
    stop() 
    
def walk():#Robot will slowly walk for 2 seconds
    for num in range(2):
        motors(1,.65)
        wait(.7)
        stop()
        motors(.65,1)
        wait(.7)
        stop()
        

def fetch():#Robot will go to nearest wall and come back to you
    x=True
    start=time()
    while x==True:
        
        forward(1)
        center=getObstacle("center")
            
        if center>6100:
            stop()
            end=time()
            
        
            backward(1)
            turnRight(1,1.35)
            times=end-start
            x=False
        
    forward(1,times)
    
def song():#lion sleeps tonight, kinda...im not good with music
    beep(.5,600)
    beep(.5,700)
    beep(.3,750)
    beep(.3,750)
    
    wait(.2)
    beep(.5,750)
    beep(.3,800)
    beep(.3,800)
    beep(.3,750)
    beep(.3,750)
    wait(.2)
    
    beep(.5,700)
    beep(.5,820)
    beep(.5,820)
    beep(.5,750)
    beep(.2,800)
    beep(2,800,600)
    
def beep1():#Piano tune
    beep(.2,650)
    beep(.2,600)
    beep(.2,650)
    beep(.2,600)
    beep(.2,650)
    beep(.2,600)
    beep(.2,550)
    beep(.3,600)
    beep(.3,650)
    
def beep2():#Sad tune
    beep(1,500)
    beep(1,450)
    beep(1,400)
def beep3():#Happy scale
     beep(.3,700)
     beep(.3,750)
     beep(.3,800)
     beep(.3,850)
     beep(.3,900)
     beep(.3,950)
     beep(.3,1000)
     beep(.3,1050)

def morningRoutine(num):
    if num<1:
    
        return
    elif num==1:
        triangle()
    elif num==2:
        triangle()
        wait(1)
        alarm()
    elif num==3:
        walk()
        wait(1)
        triangle()
        wait(1)
        alarm()
        
    elif num==4:
        fetch()#Test with robot facing a wall
        wait(1)
        turnRight(1,1.3)
        wait(1)
        walk()
        wait(1)
        triangle()
        wait(1)
        alarm()
    else:
        fetch()#Test with robot facing a wall, if possible have surrounding be open
        wait(1)
        turnRight(1,1.3)
        wait(1)
        walk()
        wait(1)
        triangle()
        wait(1)
        alarm()
        wait(1)
        song()
    
        
    
    
def greetMenu():
    x=int(input("Which option would you like? \n0.Exit\n1.Tiny Treats\n2.Ok Treats\n3.Jumbo Treats"))
    if x==0:
        print("Bye, bye! Have a good day!")
    elif x==1:
        beep2()
        walk()#walk for 2 seconds
        wait(1)
        rotate(1)#Spin angrily 
        wait(3)
        stop()
        
        
    elif x==2:
        triangle()
        beep1()
        wait(1)
        alarm()
    elif x==3:
        fetch()#Test with robot facing a wall
        wait(1)
        turnRight(1,1.3)
        walk()
        beep3()
       
        
    elif x>=4:
        print("I'm sorry, I cannot accept that.")
        greetMenu()
