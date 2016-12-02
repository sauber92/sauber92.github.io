---
layout: post
title: '정준영(sauber92)의 블로그입니다'
tags: [hyde]
description: >
  이 블로그는 경희대학교 전자전파공학과, 컴퓨터공학과에 재학 중인 정준영의 블로그입니다.  
---

This major release increases page load speed dramatically. The page now scores roughly 90/100 on [Google's PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fqwtel.com%2Fhydejack%2F) (up from ~50) and has a high score on similar tools.

Most importantly, the critical rendering path is no longer blocked by loading styles or scripts, meaning the site becomes visible faster.

Page load speed matters to Google, but is also *very* apparent to visitors with slow internet connections.

However, as a side effect of these optimizations, the site now has a visible [FOUC](https://en.wikipedia.org/wiki/Flash_of_unstyled_content).
Future versions might address this, but it is the currency in which loading speed is being payed for and can not be fully avoided.

## Major

* HTML, CSS and JS served minified.
* JS downloading starts only after the rest of the page is renderd.
* Critical CSS (above-the-fold) is inlined into the document, the rest is fetched later.

In order to minify the CSS and make it more modular it has been rewritten in SCSS.


## Minor

* Colored focus outline in page color
* Tabindex for tab navigation
* Social media icons easier tappable with finger

## Trivia

Not strictly part of the release, but the images have been blurred to increase text readability and help with loading speed as well (burred images get compressed by JPG much better).

***

[Get *The Fast One* on GitHub](https://github.com/qwtel/hydejack/releases/tag/v5.0.0)
