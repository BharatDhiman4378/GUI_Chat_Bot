# GUI_Chat_Bot
This is a Python based GUI (Graphical User Interface) chat bot who takes your query and correspondingly respond to the query 
from tkinter import * 
import tkinter as tk
from tkinter import  messagebox
from random import *
from gtts import gTTS
from playsound import playsound
import os
import wikipedia
import webbrowser
import datetime
import time
import pyjokes
#import json
import ecapture as ec
import requests

#!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!this function is use to show data on textfield !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

def show_data():    
    txtname1 = entry1.get()
    txtname2 = bot.get()
    var1 = "YOU : " + str(txtname1)+ "\n"
    var2 = "BOT : " + str(txtname2) +"\n\n"
    text.insert(0.0 , var2 )    
    text.insert(0.0 , var1 )
    
def voice():
    text_name2 = bot.get()
    tts1 = gTTS(text = text_name2, lang = "en", slow = False)
    filename = "voice10.mp3"
    tts1.save(filename)
    playsound(filename)
    #os.remove(filename)
    
#%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%this function is use to clear text %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%     
    
def _clear():
    expression = ""
    user.set("")  

#***************************************this is our coverstation i.e questions and their replies*********************************************
    
ask1      =    ["hi", "hello" ,"Hi","Hii","hii" ,"Hey","hey"]                         
reply1    =    ["Hey", "hello", "Hello too"]

ask2      =    ["how are you" , "how are you?"]
reply2    =    ["i am good" , "i am absolutly fine"]

ask3      =    ["how old are you" , "How Old are You" , "how old are you?" , "How Old are You?"]
reply3    =    ["I am launched in 2021 but i am wise beyond my years. "]

ask4      =    ["what is your name" , "tell me some thing about your self" ,"Tell me some thing about your self" ,"what is your name?"]
reply4    =    ["My self BOT" , "I am BOT " , "My name is BOT "]

ask5      =    ["thankyou" , "Thankyou" , "thank you" ,"Thank You"]
reply5    =    ["Anytime.That's what I am here for!"]

ask6      =    ["What can you do?" , "what can you do for me" , "What can you do" , "What can you do for me?" ,"what can you do" ]
reply6    =    ["I can do anything what you want me to do!"]

ask7      =    ["who created you","who is god for you","who invented you"]
reply7    =    ["I am created by Bharat Dhiman", "I am invented by Bharat Dhiman"]

ask8      =    ["Tell something about me", "Tell Something About Me", "Tell something about me !"]
reply8    =    ["You are smart and you like having fun, plus you ask me great questions. I could not ask for a better BOSS!"]

ask9      =    ["reason for you" , "Reason for you"]
reply9    =    [" i was created as a part of mini project by MR.Bharat" ]

ask10      =    ["what is love?" , "what is love" ,"love" , "opinion about love" , "what is your opinion about love"]
reply10    =    [" Love is a set of emotions and behaviors characterized by intimacy, passion, and commitment." , "Love is a very strong positive feeling towards something or someone." ]

ask11      =    ["flip a coin " , "toss a coin" , "Toss a coin" ,"flip a coin"]
reply11    =    ["it's head" , "it's tail"]

ask12      =    ["roll a dice" , "Roll a dice"]
reply12    =    ["the number on dies is  1 " , " the number on dies is2" ," the number on dice is 3" ," the number on dies is 4", "the number on dies is 5" , "the number on dies is 6"]

error     =    ["sorry, i don't know", "what u said?" ] 


#&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&& this is our main window $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

window1 = tk.Tk()  
window1.minsize(364 ,350)                   
window1.maxsize(364, 350)                    
window1.title("REPLIKA")
window1.configure( bg ="paleturquoise")

scrollbar = Scrollbar(window1)     
scrollbar.pack(side = RIGHT , fill = Y)

user = StringVar()                          
bot  = StringVar()                          
                  
entry1 = Entry(window1, textvariable=user  , width = 45 )
entry1.place(x = 3, y = 325)
    
btn2 = Button(window1, text="Enter", command=lambda:[ main() , show_data() , _clear() , voice()]  , activebackground = "silver" , height = 1 ,width = 6)
btn2.place( x = 290  , y= 322) 

text  = Text(window1 , width = 48, height = 19, wrap = WORD , font = ("arial" , 10 , "bold") , yscrollcommand = scrollbar.set)
text.place(x= 5 , y =1)
scrollbar.config(command = text.yview)

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@this function is used select question from conversation and then reply randomly @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@                            
                                
def main():                             
    question = user.get()                        
    if question in ask1:                      
        bot.set(choice(reply1))
    elif question in ask2:
        bot.set(choice(reply2))
    elif question in ask3:
        bot.set(choice(reply3))
    elif question in ask4:
        bot.set(choice(reply4)) 
    elif question in ask5:
        bot.set(choice(reply5)) 
    elif question in ask6:
        bot.set(choice(reply6)) 
    elif question in ask7:
        bot.set(choice(reply7)) 
    elif question in ask8:
        bot.set(choice(reply8))
    elif question in ask9:
        bot.set(choice(reply9))
    elif question in ask10:
        bot.set(choice(reply10))
    elif question in ask11:
        bot.set(choice(reply11))
    elif question in ask12:
        bot.set(choice(reply12))       
    
    elif 'search youtube' in question :
        question = question.replace("search youtube" , "")
        youtube = "https://www.youtube.com/results?search_query="
        webbrowser.open( youtube + question)
        bot.set("searching your" + question)
        
    elif 'open youtube'in question:
        webbrowser.open("https://www.youtube.com")
        bot.set("opening youtube...")    
    
    elif 'open amazon' in question:
        webbrowser.open("https://www.amazon.in/ref=as_li_ss_tl?ie=UTF8&linkCode=ll2&tag=enin-edge-topsites-curate-ana-21&linkId=fbedcb44d04a4bae8eae32722a2f41c2&language=en_IN")
        bot.set("opening amazon enjoy your shopping...")
    
    elif 'open flipkart' in question:
        webbrowser.open("https://www.flipkart.com")
        bot.set("opening flipkart enjoy your shopping...")    
    
    elif 'open google' in question:
        webbrowser.open("http://google.com")
        bot.set("opening google...")
        
    elif 'who is' in question:
        webbrowser.open("https://www.google.co.in/search?q=who+is+" + question)
        bot.set("opening google...")
    
    elif 'open netflix' in question :
        bot.set("opening netflix...")
        webbrowser.open("http://netflix.com") 
        
    elif 'search amazon ' in question:
        question = question.replace("search amazon"," ")
        search = "https://www.amazon.in/s?k="
        webbrowser.open(search + question)
        bot.set(" your product is ready ! continue your shopping")
        
    elif 'search flipkart' in question:
        question = question.replace("search flipkart"," ")
        search = "https://www.flipkart.com/search?q="
        webbrowser.open(search + question)
        bot.set(" your product is ready ! continue your shopping")
        
    elif 'open chrome' in question :
        bot.set("opening google chrome...")
        webbrowser.open("C:\Program Files\Google\Chrome\Application\chrome.exe")       
    
    elif 'tell me a joke' in question or "jokes" in question or 'tell me joke' in question:
        my_joke = pyjokes.get_joke(language = 'en' , category = "all")
        bot.set(my_joke)
    
    elif 'open gmail' in question:
        webbrowser.open("http://gmail.com")
        bot.set("opening gmail...")
        
    elif 'open instagram' in question:
        webbrowser.open("http://instagram.com")
        bot.set("opening instagram...")    
    
    elif 'open wikipedia' in question:
        webbrowser.open("http://wikipedia.com")
        bot.set("opening wikipedia...")
    
    elif 'search' in question:       
        question = question.replace("search" , " ")
        webbrowser.open(question)
        bot.set("your search is ready...") 
        
    elif 'where is ' in question:
        question = question.replace("where is" , "")
        webbrowser.open("https:/www.google.nl/maps/place/" + question)
        bot.set("finding your place...")
        
    elif 'wikipedia' in question:        
        question = question.replace("wikipedia" , "")       
        result = wikipedia.summary(question, sentences = 3)
        bot.set(result)
    elif 'camera' in question:
        ec.capture(0 ,"Jarvis Camera" , "img.jpg")
        bot.set('hold on...')
    elif 'exit' in question or 'end program'in question or 'end conversation' in question:
        iExit = tk.messagebox.askyesno("LEAVE CONVERSATION" , "Confirm if you want to exit")
        if iExit > 0:
            window1.destroy()
            
    else:
        bot.set(choice(error))
        
window1.mainloop()        
          

