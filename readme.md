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

    HackerNews

     0  Want to Block Common Passwords? Sorry, That is Patented

     1  Solar panels could destroy U.S. utilities, according to U.S. utilities

     2  Show HN: Hospice.io €“ Vagrant configurations generator

     3  Single page apps in depth

     4  Exposed Webcam Viewer

     5  Canada's Guide to patents


So now all I have to do when I see an interesing article on my desktop is:

    $ hn <article_no>

And the article opens in the nearest browser window! Pretty neat!


If I want to see the comments page instead:

    $ hn -c <article_no>

Or if I want to open both the article and the comments:

    $ hn -ca <article_no>