#!/usr/bin/env node

/********************
 * Node-HackerNews
 *
 * A simple CLI app that reads in HackerNews's frontpage and colorizes it
 *
 * by Nick Donohue
 * forked from https://github.com/kamranayub/node-reddit. Thanks!
 * License: WTFPL (http://sam.zoy.org/wtfpl/)
 * Attribution is cool but not required
 ********************/

var cli     = require('cli'), 
    http    = require('http'),
    request = require('request'),
    colors  = require('colors'),
    string  = require('string'),
    openurl = require('openurl')

cli.setUsage(
  'node-hn.js [OPTIONS] [ARTICLE_NO]\n\n' +
  '  Run with no arguments to show the homepage\'s list of articles.\n'+
  '  ARTICLE_NO is one of the numbers corresponding to\n'+
  '    the article on the list.'
);

var options = cli.parse({
      comments: ['c','open comments URL for article instead'],
      article:  ['a','when -c is applied, open both comments and article'],
});

var requestURL = 'http://api.ihackernews.com/page',
    commentsURL = 'http://news.ycombinator.com/item?id=';

var getNews = function(callback) {
  request(requestURL, function (err, res, body) {
    if (!err && res.statusCode === 200) {
      var hn = JSON.parse(body),
          stories = hn.items; 
      stories.forEach(callback);
    }
  }); 
}

var limit = 27 //arbitrary limit for my screen. modify to taste.

cli.main(function (args, options) {

  if (args[0]) {
    if (string(args[0]).isNumeric()) {
      getNews(function(story,index) {
        if (parseInt(args[0]) === index) {
          if (options.comments) {
            openurl.open(commentsURL + story.item_id);
            if (options.article) {
              openurl.open(story.url);
            }
          }
          else {
            openurl.open(story.url);
          }
        }
      });
    }
    else {
      console.log(help);
    }
  }

  else {
    console.log("HackerNews".yellow)
    getNews(function(story,index) {
      if (index > limit) return;
      var row = "",
        title = story.title.length > 100
              ? story.title.substr(0, 100) + "..." 
              : story.title;

      row += ((index < 10? " ":"") + index.toString()).green;
      row += "\t" + title;
      row += "\n";

      console.log(row);
    });
  }
});
