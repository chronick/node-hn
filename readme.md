# Node HackerNews #
*A command-line HackerNews lister and opener*

This is a simple script for pulling down the HN homepage articles, as well as opening the article links in a browser via the command line. I designed this primarily for use in GeekTool, with the idea being that it would always be on my desktop, and any time an article looks interesting to me I just type ```hn <number>``` and be on my merry way.

To use out of the box:

    $ node app.js [-ca] <article_no>


I did this to make my life easier:

    $ ln -s /path/to/node-hn/app.js ~/bin/hn


Run without arguments:

    $ hn

Produces:

    HN  Scr Cmt
     0  49  38  Taleb: The future will not be cool

     1  119 96  Editorial: "How piracy changed my life"

     2  52  7   Netflix open sources resilience engineering library

     3  15  0   CEOs Don't Come Pre-Made, Authentic Leadership Has To Be Learned

     4  11  1   Who Do Online Advertisers Think You Are?

     5  44  26  A tour of the world in d3.js

     6  79  28  A static website generator in Python

So now all I have to do when I see an interesing article on my desktop is:

    $ hn <article_no>

And the article opens in the nearest browser window! Pretty neat!


If I want to see the comments page instead:

    $ hn -c <article_no>

Or if I want to open both the article and the comments:

    $ hn -ca <article_no>