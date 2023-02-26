# Naziya-Update-code-2
# update version of Naziya personal assisstance code-2

import speech_recognition as sr
import pyttsx3
import pywhatkit
import datetime
import wikipedia
import webbrowser


listener = sr.Recognizer()
engine = pyttsx3.init()
voices = engine.getProperty('voices')
engine.setProperty('voices',voices[1].id)


def talk(text):
   engine.say(text)
   engine.runAndWait()
def take_command():
   try:
        with sr.Microphone() as source:
            print('listening....')
            voice = listener.listen(source)
            command = listener.recognize_google(voice)
            command = command.lower()
            if 'naziya' in command:
                command = command.replace('naziya','')
                print(command)
                
    
   except:
            pass
   return command

def run_naziya():
    command = take_command()
    print(command)

    if 'play' in command:
        song = command.replace('play','')
        talk('playing' + song)       
        print('playing')
        pywhatkit.playonyt(song)
    elif 'time' in command:
     time = datetime.datetime.now().strftime('%I:%M %p')
     print(time)
     talk('current time is' + time)
    elif 'who the heck is' in command:
        person = command.replace('who the heck is','')
        info = wikipedia.summary(person, 1)
        print(info)
        talk(info)
    elif 'date' in command:
        talk('sorry, i have a headache')
    elif 'are you single' in command:
        talk('I am in a relationship with shagufta') 
    elif 'open youtube' in command:
        talk('ok sir iam on the way')
        webbrowser.open("youtube.com")
    elif 'search for' in command:
        about = command.replace('search for','searching for...')
        webbrowser.open("quora.com")
        print(about)
        talk(info)
    else:
        talk('please say  the command again.')  
    

run_naziya()
