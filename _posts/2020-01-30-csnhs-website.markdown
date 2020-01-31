---
layout: single
title: "CSNHS Website"
date: 2020-01-30 10:53:10 -0600
categories: projects
---
Most high school organizations do not have a dedicated website. They typically just used a page on the school's website.
The ones that did usually had one built using a WYSIWUG editor like Wix or Weebly.
As part of the, well, computer science club I felt like I could do better.

You can visit a mostly live version of the website [here](http://clementscs.herokuapp.com/Home). Unfornately, due to host
related issues, the databased functions currently do not work.

### Technologies
After a little research I found that the popular thing to be using was Facebook's *React*. This frontend
tool acted as a way to combine JavaScript and HTML together to make a webpage. For the backend I eventually
settled on the ever popular *Node.JS*. 

An important feature for the website was to allow members to check
their volunteer hours and points. For this, I used a *SQLite* database. Having to host a database in addition to a website
was a tricky prospect for a mostly broke school club. This meant a database that can be kept as a file bundled with the
website would be helpful. The issue would be that in order to update the database, it would have to be downloaded, modified,
and then uploaded again.


### Front End

<img style="float: right; padding-left: 10px;" src="/assets/images/nhs.PNG" width="55%" />

The website's front end of written in *React* and styled using good old CSS.
An intersting problem was that most club members would likely visit the site on their phones.
Phone screens are usually held in potrait orientation, while computers are typically landscape.

Due to the width of some elements, some of the elements would become rather squashed in potrait mode.
To combat this, I added some JavaScript which detected if the device's screen had a greater vertical resolution compared
to the horizontal resolution. If so, I then displayed a small banner on the bottom asking users to rotate their device.

### Back End

<img style="float: right; padding-left: 10px;" src="/assets/images/form.PNG" width="55%" />

In addition to getting information on the club, and it's projects, most members would come to the site
to check if they have enhough volunteer hours and points to stay in good standing. 

Another feature was the "Tech Support" projects, where students and faculty from the school could
visit the site to ask CSNHS members for tech related help.

To do this, I used a *NodeJS* server connected to a *SQLite* databased as my backend. The databased contained
entries for each members points, as well in information from filled out tech support requests.

Unlike other languages JavaScript is not an syncronous language. This means that while other languages such as Java or C will
only execute one line after the other, JS will just go on ahead without waiting. For thing such as web requests this can
lead to problems such as trying to process the return from the server before it has actually arrived.

To combat this, "Callbacks" and "Promises" can be used. A callback is a function passed to another function as a parameter.
The callback will be run after the first finished. A "promise" basically says "I'll send you some data, eventaully...". After the
data from the promise arrives, it can be properly processed and displayed to the user on the page.