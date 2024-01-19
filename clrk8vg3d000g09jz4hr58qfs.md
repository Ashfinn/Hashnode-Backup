---
title: "Making a Movie Recommendation App with Python and Beautiful Soup"
seoTitle: "Making a Movie Recommendation App with Python and Beautiful Soup"
seoDescription: "Create a personalized movie picker! Learn Python web scraping to turn your Letterboxd watchlist into a fun movie randomizer.🎥🐍"
datePublished: Fri Jan 19 2024 06:13:16 GMT+0000 (Coordinated Universal Time)
cuid: clrk8vg3d000g09jz4hr58qfs
slug: making-a-movie-recommendation-app-with-python-and-beautiful-soup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704825095915/097da173-f5c9-4197-8f84-73d996ec464d.jpeg
tags: python, html5, web-scraping, beautifulsoup, movies, letterboxd

---

## What is Web Scraping?

Let's say you want a list of 100 top-rated doctors in your area. You can just search online and write them down 1 by 1. Even if you find a website containing all 100 of them in one place. They might have extra unnecessary info that you can't just `ctrl+C`, `ctrl+V`. It would take a long time. What if you could just use the website link and download all the names of the doctors at once?

Web scraping allows you to do just that. A web scraper is just like an assistant whom you can give a task like: "Hey, go through all the names on the website and find out how many of them are doctors."

Your assistant doesn't read every single item from top to bottom. Instead, it quickly scans the content, picks out the sentences or paragraphs about doctors, and brings them back to you. That's web scraping in action.

> In short, web scraping is a method of collecting data. It makes it easier to collect and store massive amounts of data in a short amount of time which would otherwise take a lot of time and will be incredibly tedious.

### How I Used Python to Scrape and Randomize My Letterboxd Watchlist

I love watching movies, and I use **Letterboxd** to keep track of the films I want to watch. However, sometimes I have trouble deciding what to watch next because my watchlist is too long. I wanted to find a way to make my movie selection more fun, so I decided to write a Python script that scrapes my watchlist and prints a random movie title from it. This way, I can get a surprise recommendation every time I run the code.

In this blog post, I will show you how I did it, and what kind of movies I got from my randomizer. *To follow this blog, you must have a fundamental understanding of HTML.*

### Python: Your Versatile Web Scraping Companion

Python is a champion for web scraping. It offers a powerful yet beginner-friendly toolkit. Let's go over all the basic tools we will use for web scraping. *Don't worry if you don't know what the library does. You will learn them along the way. Let's just build something.*

1. **Python:** Obviously!
    
2. **Requests:** This library acts as your web browser, sending requests to websites and fetching their content. You can learn more about the library here -&gt; [Requests](https://ashfin.hashnode.dev/unveiling-the-power-of-requests-a-python-library-for-http)
    
3. **Beautiful Soup:** This library transforms messy HTML code into a structured format. Making data extraction extremely easy.
    
4. **Random:** A module that lets us generate random numbers and choices.
    

## The Plan

The plan for this project is quite simple and short. It consists of three main parts:

* **Importing the libraries**
    
* **Scraping the watchlist**
    
* **Printing a random movie title**
    

Let’s look at each part in detail.

### Importing the Libraries

The first part of the code is importing the libraries that we need:

```python
import requests
from bs4 import BeautifulSoup
import random
```

* We use the `import` statement to import the modules and libraries into our program.
    
* We also use the `from` keyword to import specific functions or classes (*it's okay if you don't know what classes are*).
    

### Scraping the Watchlist

The second part of the code is scraping a user's watchlist on Letterboxd. For this example, I will use my watchlist, but you can replace the URL with any user’s watchlist that you want to scrape.

* We start by creating an empty list called `data` that will store the movie titles.
    
    ```python
    data = []
    ```
    
* Then, we use a `while` loop to iterate over the web pages of the watchlist.
    
    ```python
    data = []
    while True:
    ```
    
* We use the `requests.get()` function to send a **GET** request to the URL and get the HTML content of the page. Then we store it in a variable called response.
    
* We use the `BeautifulSoup()` function to create a soup object that represents the HTML document as a nested data structure. *(It structures the HTML doc for normal humans to understand)*
    
    ```python
    data = []
    while True:
        response = requests.get('https://letterboxd.com/ashfin/watchlist/')
        soup = BeautifulSoup(response.text, 'html.parser')
    ```
    
* Next, we have to go to our website and find our desired elements.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705592351037/1ddf279d-38c9-4740-b4dd-dd0ee8a3c5ac.png align="center")
    
    We right-click on the page and select Inspect Element. This allows us to inspect the HTML file
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705592438423/bffeab43-d191-4e76-8d5c-38d91d2c7b56.png align="center")
    
    *Remember that this might be different for different browsers.*
    
* We click on the Select Element button and try to find the movie's title.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705592496674/000a53fe-335c-4627-a383-c18f26b9d057.png align="center")
    
    The titles might not be as easily accessible on some sites so you would have to do some digging. In our case, we can find the title from the `alt` attribute of the movie images.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705592752622/584c1a6f-afac-43ff-a53a-e2cf14b42d55.png align="center")
    
* We use the `soup.select()` method to find all the elements that match the CSS selector `li.poster-container`. Since the image attribute is inside the `li.poster-container` attribute.
    
* This selector returns a list of items containing the movie posters and titles.
    
* We use a `for` loop to iterate over this list, and for each element, we find the `img` tag inside it.
    
    ```python
    for e in soup.select('li.poster-container'):
        img = e.find('img')
    ```
    
* We use the `has_attr()` method to check if the `img` tag has an `alt` attribute, which contains the movie title. If it does, we use the `append()` method to add the title to the `data` list.
    
    ```python
    for e in soup.select('li.poster-container'):
        img = e.find('img')
        if img and img.has_attr('alt'):
            data.append(img['alt'])
    ```
    

### Printing a Random Movie Title

The third and final part of the code is printing a random movie title from the `data` list.

* We use the `random.randint()` function to generate a random integer between 0 and the length of the list. We use this integer as the index to access a random element from the list.
    
    ```python
    num = random.randint(0, len(data))
    ```
    
* We use the `print()` function to display the movie title on the screen.
    
    ```python
    num = random.randint(0, len(data))
    print(data[num])
    ```
    
* We also use the `input()` function to ask the user if they want to exit the program or continue. If the user types 1, the program breaks out of the loop and ends. Otherwise, the program repeats the process and prints another random movie title.
    
    Here's what the final code looks like -&gt;
    

```python
import requests
from bs4 import BeautifulSoup
import random

data = []
while True:

    response = requests.get('https://letterboxd.com/ashfin/watchlist/')
    soup = BeautifulSoup(response.text, 'html.parser')

    for e in soup.select('li.poster-container'):
        img = e.find('img')
        if img and img.has_attr('alt'):
            data.append(img['alt'])

    num = random.randint(0, len(data))
    print(data[num])
    exit_value = input("type 1 to exit:   ")
    if exit_value == '1':
        break
```

### The Results

Now that we have written the code, let’s see what kind of movies we get from our randomizer. Here are some examples of the output:

```python
Parasite
type 1 to exit:
```

```python
The Shawshank Redemption
type 1 to exit:  1
```

As you can see, the randomizer gives us a variety of movies from different genres, years, and countries. Some of them are classics, some of them are recent hits, and some of them are hidden gems. They all reflect my taste and preferences, as they are from my watchlist. This is a fun and easy way to discover and enjoy new movies.

## Conclusion

I hope you enjoyed this project and learned something new from it. If you want to try it yourself, you can find the source code here -&gt; [Letterboxd-Lifesaver](https://github.com/Ashfinn/Letterboxd-Lifesaver). You can also modify the code to scrape other websites or to add more features or functionality. Just be careful and check if the website allows web scraping or not. Feel free to share your feedback or suggestions in the comments below.

Happy coding and happy watching! 🎬