---
layout: post
title:      "First CLI Scraping Project - Plant Manager"
date:       2020-08-10 03:21:06 +0000
permalink:  first_cli_scraping_project_-_plant_manager
---


For my Command Line Interface Project (CLI), we were allowed to build anything, as long as we utilized an API or scraped data from a website. Although consuming an API is said to be easier, I decided to take on the challenge and scrape data from a website.

**What is Scraping?**

Some websites contain a very large amount of important data such as stock prices, sports stats, or in my case, information on how to take care of your houseplants. If you would like to access this information, you would either have to use the same format as the website or copy and paste the information into a new document. This could be a very tedious process. That's where scraping comes into play!
Scraping refers to the extraction of data from a website. This is achieved by parsing the web page's HTML code and pulling ("scraping") the data from the HTML. In order to do so, I closely examined the HTML and identified the exact elements containing the information for the plants' light, water and fertilizer suggestions. This required much precision.
Although scraping is difficult, I understood what it could be helpful to many programmers. Not all information and data is available if one decides to consume an API for their program. There is, however, a good chance that a quick Google search will reveal a large list of the data you're looking for. You can scrape that information and store it in your very own database. 

**Scraping Using Nokogirl and Open-URI**

Scraping using Open-URI came in handy while coding my program. Open-URI is an easy-to-use Ruby Programming module that allows programs to make HTTP requests. 
I also used a Ruby gem called Nokogiri. This gem made HTML parsing so much easier. I was able to treat a large string of HTML code as if it were a sequence of nested objects that I can utilize to excerpt information using provided functions. Nokogiri made the level of meticulousness necessary to extract the information much easier to reap.
