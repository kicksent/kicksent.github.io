---
layout: posts
title: How I learned to type properly after 15 years of habit
---

# Touch Typing 
  

For those of you who do not know. Earlier this year I decided to relearn how to type. For years I had lazily never learned how to type in a way which utilized all of my fingers. I began this journey in 2019 a few weeks before the new year. Here is what I did to achieve my goal: 
  

**[Typing Club](https://www.typingclub.com/)**

  

This site has nice clicky sound effect when typing for correct and incorrect keys. In addition, it had the progression built into it that I was looking for to retrain my brain how to type from scratch. It also has some nice motivational content that helps you to use correct form, keep with your training, and learn about typing without looking at your keyboard. They refer to this as touch typing. The site asks for payment but you can continue on for a very long time and I was never forced to pay for the lessons before moving on to a new site. I highly recommend this as a starting place for new typists.

### Early training:

For the first week, I was unemployed and I typed everyday for 3+ hours. This may sound like a lot but honestly it was a great way to get a lot of learning done. I really wanted to retrain my brain to type using this new style and I didn't want to revert back to my old ways. I was desperate to get my typing speeds up so that I could rely on my typing skills for all of my typing demands.

  
  

### Goal and reward:

Type 40 wpm consistently and I will reward myself with a [Ducky One 2 Mini RGB 60%](https://mechanicalkeyboards.com/shop/index.php?l=product_detail&p=4322). Gosh this keyboard was so pretty, and it even had a special exclusive YOTD spacebar(I ended up getting YOTP but oh well). 

  
  

### The yield:

  

After my first two weeks, I could type all a-z keys without looking and was able to occasionally burst up to 40WPM. Thus, I ordered my new Ducky keyboard and eagerly awaited its arrival.

  

### Onward!

  

For those of you who have used [typing club](https://www.typingclub.com/). There is a progression where they add keys and you advance through levels, short minigames, and single handed typing sessions. Each time you complete one of these, you advance one level up. However, there is a threshold for WPM and accuracy which must be met for you to continue on. I was able to get to about level 400 before I found myself having to retype lessons to get the requirement met. I would this repetitive and tedious so I reset my score to ~ level 200 and started back at it again.

  

The next time I reached level 400 I was breezing through the levels reaching speeds over 55 WPM and sometimes 65 in short bursts. But it was time to move on. The lessons are quite narrow and once I reached this point I wanted to move on to something new.

  

**[TypeRacer!](https://play.typeracer.com/)**

  

Typeracer is the king of online typing. I still type on this site everyday as of 9/19/2019(9 months after the beginning of my typing journey). It has a lightweight feel and is constantly full of users. There are also some nice keybinds for playing without using a mouse. Here are the ones I use the most:

  

**ctrl + alt + O**: Starts a practice session

**ctrl + alt + J**: Go back to the main screen unless in an active match

**ctrl + alt + I**: Starts a race against players online

  

### Today:

Today I type between 65 and 85 words per minute depending on the text. Although I am now employed full time, I type every day on [TypeRacer](https://play.typeracer.com/) for 30-60 minutes. I find time for this when burned out from coding or when I just want to warm up my brain in the morning when I am feeling tired. I still need to remain diligent about using the proper form. Interestingly enough, I am faster at touch typing now but if I am tired or stressed I sometimes forget to type properly and will revert to my old way of typing. When I notice this, I make a mental note and switch over to touch typing again. It's an easier fix now because it's much easier to type properly now.

  
  
  

### What about code?

If anyone is interested, I did write a small script to help log times and text from the site using python. It's pretty simple but I have been using it to store some typing data so I can track my progress over the years. It does require some copy and pasting but it works for now.

```

#Typeracer progress script for tracking my mental energy, exhaustion, and progress over the next few years

from datetime import datetime

import os

import argparse

  

#parse

parser = argparse.ArgumentParser(description='Log typeracer.com WPM and time of day.')

parser.add_argument('WPM', metavar='wpm', type=int, help='integer words per minute')

parser.add_argument('text', metavar="text", type=str, help='the text typed surrounded by ""')

args = parser.parse_args()

  

submission_time = str(datetime.now().strftime('%Y-%m-%d %H:%M:%S'))

  

#log

log_file = "typeracer_log.txt"

log_text = ("{} \t {} \t {} \n".format(args.WPM, args.text.strip("\n"), submission_time))

  

#write contents to file

file = open("typeracer_log.txt", 'a')

file.write(log_text)

file.close()

  

print("Success!")

  

```