---
layout: post
title: My Ruby CLI Gem
date: 2013-05-06 
---

**Overview:**

As a part of [Learn Verified](https://learn.co/){:target="_blank"}, I have just completed my first command line interface Ruby gem! This project involved gathering data from a website and then displaying select information back to the user. I thought about a number of different websites I could scrape for this project, but I picked the one that immediately stood out. Since I’m a huge fan of TED talks and wanted a quick way to see some of the most popular talks today, I’ve decided to scrape the [Ted Talks](https://www.ted.com/talks){:target="_blank"} website. The basic requirements for the project were as follows: 

1.	Package as a gem
2.	Provide a CLI on gem installation.
3.	CLI must provide data from an external source, whether scraped or via a public API.
4.	Data provided must go at least a level deep, generally by showing the user a list of available data and then being able to drill into a specific item.

When the user runs the gem, a list of categories (e.g. science, business, technology, design) are displayed. The user then chooses a category, and a list of the top 10 TED talks in that category is shown. Additionally, the user can also enter a search term and a list of the top TED talks relating to that search term will display. The user then selects a talk, and can see more detailed information about that specific talk. Here’s a visual of the command line interface:
Main menu:

List of categories:

![Categories screenshot](/img/categories.jpg)

List of talks:

![talks screenshot](/img/talks.jpg)

Talk description:

![description screenshot](/img/description.jpg)

While making this ruby gem, I created three separate classes—a TedTalks::CLI class, TedTalks::Talk, and TedTalks::Info class. The purpose of the CLI class was to list the different categories and talks and allow the user to choose from the options on the command line. The basic flow of the class is defined within the call method:

![CLI method screenshot](/img/cli.jpg)

One of the most interesting parts of this project was getting information from the ted.com website. In the TedTalks::Talk and TedTalks::Info classes, I use the Nokogiri ruby gem to scrape relevant information. This includes attributes such as title, author, date and rating of a talk, which I gathered from the general talks page, using the chrome developer tools to figure out what the correct elements are. Things like description, time, date, and views were for an individual talk, gathered from the individual talk webpage. A code snippet is included below: 

![scraping method screenshot](/img/scrape.jpg)


Once I had scraped the information from the Ted talks website, all that was left was to display this information back to the user, displayed below as an example: 

![list_talks method screenshot](/img/list_talks.jpg)

**Challenges:**

This is a brief overview of how the gem gathers information from the website and displays it back to the user on the command line. I did encounter some challenges along the way, such as ensuring my code was efficient, and that I didn’t repeat the same line of code too many times, as I had just learned about DRY (don’t repeat yourself). For example, I initially had twice the number of if statements as I do here—one for every category and its number, but then I decided that it would be easier to store them in a hash and iterate over them. I use the hash to get the word that corresponds to the user input. This way I wasn’t repeating the same line of code too many times.

![hash method screenshot](/img/hash.jpg)


I had initially also placed the functionality of scraping both the list of ted talks and the individual talk info into just one class, but then later decided that it may be more efficient to place both of these into separate classes, with each class just doing one thing. This way, I found it much easier to separately keep track of both of these websites. 

At the end, I had three different classes and a working Ruby gem! In the next few days, I will go through a code review and improve upon what I have.   
