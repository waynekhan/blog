---
title: Embedding Flash in HTML, versus iframe
date: 2009-03-18T04:02:16+00:00
---

I recently received a request to build a new CakePHP app. The interface consists of a container 800 by 250 pixels width, with practically no chrome (company name, copyright info) whatsoever. It's shows calendar entries for a given period, and users can click to view entry details (in a [Thickbox](http://www.codylindley.com/Javascript/257/thickbox-one-box-to-rule-them-all)).

I thought the design was rather simplistic, and gave it no further thought. The project was completed in about 2 days, and I spent an additional 1.5 days making minor changes.

Today I realized that simple design was because it was intended to replace a Flash-based calendar on the client's homepage. I did a test with iframe, but it doesn't work well, because the Thickbox (with entry details) is contained within the iframe.

Note to self: Clarify intended deployment method before giving price information. No hard feelings of course, since they might not understand that embedding Flash is not the same as iframe. Now it's likely I'll need to spend more time doing it right; i.e., template-ize their HTML, and then put in the (micro) website that I completed earlier.
