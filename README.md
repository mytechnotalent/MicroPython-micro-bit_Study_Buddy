![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/MicroPython-micro-bit%20Study%20Buddy.png?raw=true)

# MicroPython-micro-bit
# Study Buddy
The micro:bit Study Buddy is a micro:bit Electronic Educational Engagement Tool designed to help students learn a new classroom subject with the assistance of a micro:bit TED (Talking Educational Database) and a micro:bit TEQ (Talking Educational Quiz).

## Mission Statement
Over the next 10 years we are going to see a fundamental transformation of technology in a way never before seen in history.  

Future careers will look very different than they do today to which literally every opportunity will include the usage of a microcontroller in combination with an automation engine and the skills necessary to adapt to this new paradigm.

With this landscape directly over the horizon we need to empower our Educators, the single more important group of leaders in the twenty-first century, with the tools necessary to inspire and engage the next generation of makers in an exciting new way.

Today is born the concept of a micro:bit Electronic Educational Engagement Tool to connect with students in a very emotional and inspiring way which will help solidify classroom subject curriculum in a significantly enhanced time frame in addition to preparing these future leaders with the software engineering fundamentals necessary to compete in tomorrow's economy.

The micro:bit Electronic Educational Engagement Tool is comprised of a micro:bit TED (Talking Educational Database) and a micro:bit TEQ (Talking Educational Quiz) to enhance Educators world-wide with the curriculum integration to take their students to the next level.

## Project Hypothetical
YOU are a History and Biology Educator and are about to teach your students the 50 state capitals of the US in your history curriculum in addition to parts of a cell in your biology curriculum.  YOU now have a grant and with that grant a micro:bit V2 for each student and YOU get to take advantage of the micro:bit EEET (Electronic Educational Engagement Tool) to integrate into your curriculum!

YOU follow the steps below and very easily see how YOU can integrate this technology in a way NEVER done in history!  YOU will be able to BRING TO LIFE a micro:bit TED (Talking Educational Database) or talking chat bot that can help the student learn the 50 state capitals and the parts of a cell as it makes facial animations and literally TALKS to the student!

The student will then be able to work with the micro:bit TED on their own to help strengthen their curriculum concept development and then take the micro:bit TEQ to help them prepare for the subject exam or test.  They can engage the TED and TEQ on demand which will build their confidence and comfort level of the subject matter in a revolutionary new way!

We are going to utilize the micro:bit Python V2 web editor to design our project with detailed steps to help any educator regardless of their background or comfort level to implement this feature.

## Schematic
![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/schematic.png?raw=true)

## Parts
[micro:bit](COMING NOVEMBER 2020)

## STEP 1: Navigate To The FREE micro:bit Python Web Editor
[micro:bit Python Web Editor](https://python.microbit.org/v/beta)<br><br>
![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/STEP%201.png?raw=true)

## STEP 2: Plug micro:bit V2 Into Computer
***PLUG IN USB CABLE TO COMPUTER AND DEVICE***

## STEP 3: Click CONNECT
![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/STEP%203.png?raw=true)

## STEP 4: Click "BBC micro:bit CMSIS-DAP" & CONNECT
![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/STEP%204.png?raw=true)

## STEP 5: Highlight Sample Code - Select All
![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/STEP%205.png?raw=true)

## STEP 6: Click Backspace On Keyboard To Delete Sample Code
![image](https://github.com/mytechnotalent/MicroPython-micro-bit_Study_Buddy/blob/main/STEP%206.png?raw=true)

## STEP 7: Copy Study Buddy Python Code Template Into Python Web Editor
```python
import gc
import time

from microbit import display, Image
from speech import say


def generic_bot(question):
    """Bot function

    Parameters
    ----------
    question : str
        Question to parse for trigger words

    Returns
    -------
    None
    """
    # Our Python dictionary which is a database
    # and here is where we can type in new key/value
    # pairs or in our case trigger word or words and
    # then a response
    db = {
            'your name': 'My name is Mr. George.',
            'food': 'I like pizza.',
         }


    # Init LED happy image 
    display.show(Image.HAPPY)

    # This is an advanced topic as well however this little function
    # cleans out the unnecessary global objects or variables on what
    # we call the heap area in memory
    gc.collect()
    
    # Init response object
    response = ''
    
    # We want to make sure that our dictionary database can 
    # find all values even if you use a capital letter
    # so we convert everything to lowercase 
    question = question.lower()
    
    # If you type something other than an empty string that means 
    # question has a value so the rest of the code will continue
    # on
    if question:
        # This is a bit complicated do not worry about this for now
        # all this is doing is looking through our dictionary database
        # and seeing if our input value has the word or words which
        # match an entry in the dictionary database and if it does
        # put the value in the _response object
        response = [val for key, val in db.items() if key in question]
        
        gc.collect()
        
        # If our bot got a response from us then make sure
        # we trigger the speaking or suprised image so our bot
        # can open its mouth to talk and then have our bot
        # talk to us in our REPL and by hearing it speak as well
        # and if the user types in a trigger work that is not 
        # recognized then provide a custom default response
        if response:
            display.show(Image.SURPRISED)
            print('BOT: {0}'.format(response[0]))
            say(str(response[0]))
            display.show(Image.HAPPY)
        else:
            display.show(Image.SURPRISED)
            print('BOT: That is not a state or state capital I am familiar with.')
            say('That is not a state or state capital I am familiar with.')
            display.show(Image.HAPPY)
```
