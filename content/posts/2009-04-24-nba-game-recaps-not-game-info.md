---
title: NBA game recaps, not game info!
date: 2009-04-24T08:08:19+00:00
---

With reference to [this](http://t-a-w.blogspot.com/2009/03/use-greasemonkey-to-vote-for-hotter.html) post, I decided to write my first Greasemonkey script.

I don't subscribe to cable TV, so I get my sports news fix mostly by reading. Now that the NBA playoffs are in progress, I use NBA.com on a daily basis to read recaps like [this one](http://www.nba.com/games/20090423/LALUTA/recap.html). I'm upset enough that the Lakers -- one of the eight teams I'm rooting for -- lost, without having to right-click "Game Scoreboard", copy the link, and replace "gameinfo.html" with "recap.html" -- which is what I'm most interested in, since I didn't watch the match.

This is a pain, and since I can't control NBA.com, I wrote a quick Greasemonkey userscript to do it automatically for me. This uses the excellent [jQuery](http://jquery.com/), and is just 3 lines:

```javascript
jQuery("span.gamelinks a").each(function() {
    var $this = $(this);
    $this.attr("href", $this.attr("href").replace(/gameinfo/, "recap"));
});
```