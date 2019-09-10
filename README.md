# Learning-Python
#Packing for Dictionaries 

def print_teacher(**kwargs):
    #kwargs stands for key word arguments 
    #when packing for tuples only use one * and use key word args 
    for key, value in kwargs.items():
        print(f'{key}: {value}')
    
    
print_teacher(name='Ashley', job='Instructor', topic='Python')

#Object oriented Python 
    #Object/Classes have attributes to describe them like nouns have adjectives, nouns use verbs for actons where classes use methods for special abilities 
    #An instance is 
class Thief:
    sneaky = True
    
#creating a class, code challenge 1 obejct oriented Python

class Student():
    name = "Sam"
    
me = Student() #creating this me = Student() is an example of an instance 
print(me.name) #this is printing out that specific instance with the attribute name attached to it

#Methods: Methods are functions that belong to a class
#Methods in classes are the actions that the instances of your class can do 
#When methods are used their used by an instance not by the actual class
#Because of this methods always take at least one parameter, which represent the instance that is using the method, by defult that parameter is call "self"

class Thief:
    sneaky = True
    
    def pickpocket("self"):
        print("Called by {}".format(self))
        return bool(random.randint(0,1))
    
#Below is a tricky situation that should be noted with regard to methods 
kenneth = Thief()
kenneth.pickpocket()
#this will return either True or False
#but Thief.pickpocket() will return an error message
#when using the direct class with the method you must pass an arguement
Thief.pickpocket(kenneth) #This will achieve the desired True or False result
#since we called the METHOD directly from the CLASS we had to provide INSTANCE that it would be used by 
#METHODS can only be used by INSTANCES

    

    
#Code Challenge #2 object oriengted Python
class Student:
    name = "Sam"
    
    def praise(self):
        return "You're doing a great job, {}".format(self.name)
        #In your praise method you will want to use the instance with name: self.name
        
    def reassurance(self):
        return "Chin up, {}. You'll get it next time!".format(self.name)

    def feedback(self, grade): 
        if grade > 50: #since grade is a parameter of the method, does no need to be refered to using self
            return self.praise() #since praise and reassurance belong to the object the must be returned using self
        else:
            return self.reassurance() 
        
#Methods with multiple parameters

import random 
    
class Thief:
    sneaky = True
    
    def __init__(self, name, sneaky=True, **kwargs):
        self.name = name
        self.sneaky = sneaky
        
        for key, value in kwargs.items():
            setattr(self, key, value)
        
    def pickpocket(self):
        if self.sneaky:
            return bool(random.randint(0,1))
        return False
    
#Code Challenge 3 methods with multiple parameters 

class Student:
    name = "Your Name"
    
    #Sometimes I have other attributes I need to store on a Student instance, though. 
    #Can you use **kwargs and setattr to add attributes for any other key/value pairs I want to send to the instance when I create it?
    def __init__(self, name, **kwargs):
        self.name = name
        for attribute, value in kwargs.items():
            setattr(self, attribute, value)
    
    def praise(self):
        return "You inspire me, {}".format(self.name)
    
    def reassurance(self):
        return "Chin up, {}. You'll get it next time!".format(self.name)
    
    def feedback(self, grade):
        if grade > 50:
            return self.praise()
        return self.reassurance()
    

#OOP Basics quiz

# What method do we override to change what happens when a class instance is created?
    #__init__
#An instance is a new copy of a class
    #True
#Use del to delete an instance

## Masterclass OOP
    
class RaceCar:
    
    def __init__(self, color, fuel_remaining, **kwargs): 
        self.laps = 0 #setting this attribute within the method so that it is not defined universally but just for this instance
        self.color = color #example setting objects as instances 
        self.fuel_remaining = fuel_remaining #example of setting objects as instances 
        
        for key, value in kwargs.items():
            setattr(self, key, value)
            
    def run_lap(self, length):
        self.fuel_remaining = self.fuel_remaining -(length*0.125)
        self.laps += 1 
    
    
