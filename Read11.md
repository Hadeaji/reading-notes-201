# Assorted Topics

## controlling Sizes

you can easily control the size of an image in CSS using the `height` and `width`
And to organize the site you have to specify a the same size for the small, medium and large photo's like
and Grouping them into classes

## Alignning Images
Using `float: left;` and `float: right;` you can easily align it properly.
Adding some margin to let a space between img and text

How can you center them?

By default images are inline and if you want to center them use you have to make their display at block level
and set the margins to auto this will center the image and make the text under it

## Background

1: background-color
2: background-image
3: background-repeat
4: background-attachment
5: background-position
you should consider this order when using some of them to work properly

## Background Image

You can also use `background-image: url("ImageDirectotyHere");` to place an image for the background of and 
HTML element

Background Repeat:

The background image is repeated both Ways by default

`repeat-x` The image is repeated horizontally only
`repeat-y` The image is repeated vertically only.
`no-repeat` The image is only shown once.

background attachment:

You can make the fixed backgroung image stay fixed or move when scrolling the page.
By using those values for it

`fixed`
The background image stays in the same position

`scroll`
The background image moves up and down as the user scrolls up and down the page.

Background position:
used to specify where in the browser window the background image should be placed when the 
backgroung image in not being repeated

using percentage after the command like 

`background-position: 50% 50%;`

The first represents the horizontal position and the second represents the vertical

and if you only typed one value the other one will default to center

You can also use multi background images like in the example

 `background:`
 `url(example-1.jpg)`
 `top left no-repeat,`
 `url(example-2.jpg)`
 `bottom left no-repeat,`
 `url(example-3.jpg)`
 `centre top repeat-x;`

You can add several properties to an element when trasiform from
one for the default stat and one when hovered and one when activeted or clicked on.

using `:hover`
and `:active`

> this is called an image spirit

## background gradient

how to make gradient background color 

![ex](Read11-1.jpg)


Contrast Of The Background Image

![ex](Read11-2.jpg)


## Search Engine Optimization (SEO)

>Search engine optimization (or SEO) is the practice of trying to help your site appear nearer
>the top of search engine results when people look for the topics that your website covers.

the  is idea of working out which terms people are likely to enter into a search engine to find your site and then using these terms in the right places on your site to increase the chances that search engines will show a link to your site in their results

There are two Techniques for this to workout

On-Page Techniques
ther are seven key places:

1. Page Title
2. URL / Web Address
3. Headings
4. Text
5. Link Text
6. Image Alt Text
7. Page Descriptions

Off-page Techniques

How to Identify Those Keywords:

1. Brainstorm
List down the words that someone might type into Google to find your site.

2. Organize
Group the keywords into separate lists for the different sections or categories of your website

3. Research
There are several tools that let you enter your keywords and then they will suggest additional keywords you might like to consider, such as:

adwords.google.co.uk/select/KeywordToolExternal

4. Compare
It is very unlikely that your site will appear at the top of the search results for every keyword.

5. Refine
Now you need to pick which keywords you will focus on. These should always be the ones that are most relevant to each section of your site.

6. Map
Now that you have a refined list of keywords, you know which have the most competition, and which ones are most relevant, it is time to start picking which keywords you will use for each page.


## Analytics: Learning about your Visitors

- Signing Up
The Google Analytics service relies on you signing up for an account at:
www.google.com/analytics
The site will give you a piece of tracking code which you need to put on every page of your site

- How it Works
Every time someone loads a page of your site, the tracking code sends data to the Google servers where it is stored.
Google then provides a webbased interface that allows you to see how visitors use your site.

- The Tracking Code
A tracking code is provided by Google Analytics for each website you are tracking. It should appear just before the closing </head> tag.
The code does not alter the appearance of your web pages

#### How Many People Are Coming to Your Site?

![ex](Read11-3.jpg)

It also tells you What Are Your Visitors Looking At the most from your pages and whish is being the lowest so you will cosider improving it

it will also tell you Where Are Your Visitors Coming From 


## In order to put your site on the web you will need a domain name and web hosting.

Your domain name is your web address (e.g. google.com or bbc. co.uk) 
And you will need to upload it to a web server. Web servers are special computers

### FTP & Third Party Tools

To transfer your code and images from your computer to your hosting company, you use something known as File Transfer Protocol.
They allow you to transfer files across the Internet from your computer to the web server hosting your site