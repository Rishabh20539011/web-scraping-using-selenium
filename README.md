## web-scraping-using-selenium
### Scraping Data from a dynamic website-[GRABCAD](https://grabcad.com/library) under various categories using Selenium

**INTRODUCTION:**

Grabcad is a platform where we can upload or download CAD models to show up our work and get a chance to win exciting prizes too. Basically GRABCAD evolved as a community of engineers and currently there 52 lakh registered users and 31 lakh open source models available on the website . This vast [free cad model library](https://grabcad.com/library) is very helpful for students and learning professionals who wants to be a part of CAD related jobs or research for learning different designing softwares such as [Solidworks](https://grabcad.com/library?page=1&time=all_time&sort=popular&softwares=solidworks),  [Catia](https://grabcad.com/library?page=1&time=all_time&sort=popular&softwares=catia),  [Autocad](https://grabcad.com/library?page=1&time=all_time&sort=popular&softwares=autocad),  [pro-E](https://grabcad.com/library?page=1&time=all_time&sort=popular&softwares=pro-slash-engineer-wildfire) etc. 
It brings together all the tools engineers need to manage and share CAD files into one platform.

**OBJECTIVE:**

As a Data Science Engineer we aims to get the all time most downloaded design models by parsing the information from this website in to a form of tabular data under different categories of knowledge domain such as [Machine Design](https://grabcad.com/library?page=1&time=all_time&sort=popular&categories=machine-design),  [3D printing](https://grabcad.com/library?page=1&time=all_time&sort=popular&categories=3d-printing),  [Aerospace](https://grabcad.com/library?page=1&time=all_time&sort=popular&categories=aerospace),  [Electrical](https://grabcad.com/library?page=1&time=all_time&sort=popular&categories=electrical)  so that we can further get to know the interests among the community, difficulty level faced to design the models and ofcourse to distribute the prizes for the most popular ones. 

(In this notebook we will limit our objective to scrape the data for each category separately to limit the dataset , We can also combine the data for different categories and further analysis and testing on that complete data can be done on a similar path)

**The overall steps I'll follow are:**

1. Understanding the structure of [grabcad](https://grabcad.com/library)website
2. Install and Import required libraries
3. Download the page and extract the urls from [grabcad's all time most downloaded library page](https://grabcad.com/library?page=1&time=all_time&sort=most_downloaded) using <code>selenium.webdriver</code> and <code>kora.selenium</code>  under different cageories (Total 33 gategories are there on the page) 
4. Extract model links( 100 per page) from each url extracted above under the required categories among those 33 mentioned above 
5. Download each model link and parse the data out of it in 4 categories i.e  Names, Downloads, Likes, Comments 
6. Combine extracted data into a dictionary from each category.
7. Compiling all details into a <code>Pandas</code> dataframe and creating a CSV file

**By the end of the project, is expected to create a csv file with the following information under machine design category:**
```
name,downloads, likes, comments
Stepper Motor Nema 17, 41925, 575, 78
MQ-1 Predator UAV, 31373, 802, 144
CNC 3-axis, 30116, 994, 175
Planetary Gearbox, 29050, 900, 189


```
**NOTE:**

1. Grabcad is a dynamic website using javascript therefore we can not extract the webpage HTML from <code>beautiful soup</code> here, Therefore use of <code>selenium</code> is preffered for these kind of websites. But yes we can use <code>beautiful soup</code> after getting the webpage HTML from the webdriver in some websites. 

2. If you want to code on you local computer install <code>Selenium</code> and one of the webdriver depends on your browser to extract the page, But if you are coding on cloud based services such as google colab then you need to install <code>kora Selenium</code> but remember this <code>kora Selenium</code> will not work on binder and others so be aware.

