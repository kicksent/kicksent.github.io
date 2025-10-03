---
layout: posts
title: What I learned from scraping dating profiles
---

# What I learned:

1. Most users don't put a lot of effort into their profiles
1. Unexpected loopholes to dating sites
1. Scraping male profiles is harder than scraping female profiles
1. Takeaways from scraping
1. People are overly direct about their desires on dating sites even if what they are saying is taboo

In August of 2021, from Friday to Sunday, I scraped 11,700 profiles from the internet. I wanted to see how difficult it would be to get a database of profiles created for comparison for a new app idea I had. There were several hurdles that make scraping difficult, but for the most part, it's pretty simple.

Using python, I used a headless browser to load pages, scrape data, enter it into mongodb, and close the pages. I set my macbook to perform this task over and over while I improved the script's speed and wrote down my thoughts for my app that I wanted to create.

However, this blog post isn't about the app I was trying to create. It's the things I learned in the process of scraping profiles that I find the most interesting.

## 1. Most users don't put a lot of effort into their profiles

There's a lot of variety out there in the world of online dating. It's cool to be able to compare what people of the same sex are saying to try and garner attention and attract partners. Many people have similar profiles that say things like "love hiking" or a joke that they likely copied from reddit or a google search. After reading about 100 of them, it becomes obvious which profiles stand out, and which don't. Putting a small effort into a profile is easily recognized and can help the user to stand out in a sea of the same fish.

## 2. Unexpected loopholes to dating sites

One of the dating sites I scraped used the id of the user from the database in the url for that user's profile. When I scraped the profile, I used this id from the url to store the profiles in my database since it was guaranteed to be unique. I also stored things like username, profile info, and description. But this had an unexpected benefit that I had not foreseen.
This site sends alerts to the user of profiles that liked their profile. However, for free members, they are unable to see who it was. Instead, they only see the profile name of the user and a grayed out profile picture to entice them to pay for the premium services. Luckily, I had the usernames and profile ids in my database. All I had to do to verify that the user really liked my profile was to look for that username in my database, and paste their profile url into my browser and like them back. (For what it's worth, the site was verified not to be lying about users that liked the profile. Many smaller dating sites have been accused of sending fake likes to get payment from users for premium services.)

## 3. Scraping male profiles is harder than scraping female profiles

When I first discovered this, I was a bit annoyed. I had written my scraper and it had been running for two days without issue. However, at some point it just stopped. I failed to realize that I would need a different scraper to scrape male profiles. This may not be obvious to users but it's harder to browse many male profiles than it is to browse for female profiles. There are likely a number of reasons for why sites do this. My main theory is that males spend more on the site, and spend more money trying to perfect their profile descriptions, and so companies try to protect that data for themselves. Profile data is a big market. Users want to be able to purchase help to boost their profiles, get higher swipe/like rates, and be able to select their mates. It's so influential it begs the question of who should be in control of this kind of data and if it's even okay for dating companies to look at the data they've collected for analysis. This data is quite personal and has a big impact on users' lives.

## 4. Women get a lot more messages(especially if they are attractive)

When scraping male profiles, I used a picture of a woman generated from a GAN(a type of neural network that creates pictures). The woman was a brunette with nice facial features on a simple background. It was quite interesting to see how many offers for money, success, freedom, adventure, etc. was prompted from successful men on the site within a day of creating this account. Some men promised extravagant vacations, others offered rides in their corvettes, and a great number offered an endless sex extravaganza lasting multiple days.

## 5. People are overly direct about their desires on dating sites even if what they are saying is taboo

Examples are:

- "White men only!"
- "Don't even message me if you..." can/can't do X or Y or Z.
- "If you live far away then be prepared to drive a lot"
- "Let's stay home and fuck"

## 6. Takeaways from scraping

Scraping sites can be a fun pass-time. You never know what you might learn about an industry from scraping some data. Just don't go publishing this data online. Dating profile data is private and often companies don't want people to be scraping it for the purposes of sharing it out or exposing people on the sites.
