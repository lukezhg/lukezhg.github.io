---
title: using google web designer to make games
date: 2021-07-30 21:57:53
tags: [google, game, google web designer]
---

[GWD下载页面](https://webdesigner.withgoogle.com/)，这样写道：Create engaging, interactive HTML5-based designs and motion graphics that can run on any device.

这是GWD对自己的定位，而我接触GWD则是因为再寻找一个替代animate动画制作软件。居然真的被我找到了。GWD应该说是一个不错的替代品。第一它是免费的，第二它是谷歌出品的，第三它支持脚本交互。此外，它符合个人的开发思维习惯。

除了用它可以实现基本动画之外，还可以用它开发小游戏，比如：[https://html5advertising.de/2015/09/game-development-with-google-web-designer-ninja-jump-part-i/](https://html5advertising.de/2015/09/game-development-with-google-web-designer-ninja-jump-part-i/)

视频教程：[https://www.youtube.com/watch?v=BPa9Z_t-Wxo](https://www.youtube.com/watch?v=BPa9Z_t-Wxo)

此外，Patrick Voelcker还提供了一个作弊清单如下：

## [](#Google-Web-Designer-API-Cheatsheet "Google Web Designer API Cheatsheet")Google Web Designer API Cheatsheet

### [](#Change-Content： "Change Content：")Change Content：

```
Textfield:
gwd.actions.events.getElementById(textFieldId:String).​textContent​= content:String;

Image:
gwd.actions.events.getElementById(imageId:String).​setAttribute(​"source", imageUrl:String);

Video Player:
gwd.actions.events.getElementById(videoId:String).s​etAttribute(​"sources", videoUrls:String);

YouTube Player:
gwd.actions.gwdYoutube.​setYouTubeId​(ytPlayerId:String, ytId:String, cueOnly:Boolean);

Exit:
gwd.actions.events.getElementById(tapAreaId:String).​setAttribute​("data­exit­url", url:String);

CSS:
gwd.actions.events.s​etInlineStyle(​objectId:String, cssCode:String);
```

### [](#Timeline "Timeline")Timeline

```
gwd.actions.timeline.​play​(objectId:String);
gwd.actions.timeline.​pause​(objectId:String);
gwd.actions.timeline.​togglePlay​(objectId:String); gwd.actions.timeline.​gotoAndPlay​(objectId:String, labelName:String); gwd.actions.timeline.​gotoAndPause​(objectId:String, labelName:String);
```

### [](#Page-Deck "Page Deck")Page Deck

```
gwd.actions.gwdPagedeck.​goToPage(​'gwd­ad', pageId:String, transitionStyle:String, duration:Number, transitionTiming:String, direction:String)
```

### [](#TaP-Aera "TaP Aera")TaP Aera

```
gwd.actions.events.getElementById(tapAreaId:String).​setAttribute(​"data­exit­url", url:String) gwd.actions.gwdIframe.​setUrl​(iframeId:String, url:String)
```

### [](#Google-Ad "Google Ad")Google Ad

```
gwd.actions.gwdDoubleclick.​initAd​('gwd­ad');
gwd.actions.gwdDoubleclick.​goToPage​('gwd­ad', pageId:String, transitionStyle:String, duration:Number,
transitionTiming:String, direction:String); gwd.actions.gwdDoubleclick.​exit​('gwd­ad', exitName:String, url:String, collapse:Boolean, pauseMedia:Boolean);
gwd.actions.gwdDoubleclick.​exitOverride​('gwd­ad', exitName:String, url:String, collapse:Boolean, pauseMedia:Boolean);
gwd.actions.gwdDoubleclick.​incrementCounter​('gwd­ad', counterName:String, isCumulative:Boolean);
gwd.actions.gwdDoubleclick.​startTimer​('gwd­ad', timerName:String);
gwd.actions.gwdDoubleclick.​stopTimer​('gwd­ad', timerName:String);
gwd.actions.gwdDoubleclick.​reportManualClose​('gwd­ad‘);
```

### [](#Swipable-Gallery "Swipable Gallery")Swipable Gallery

```
gwd.actions.gwdSwipegallery.​goToFrame​(galleryId:String, frameNumber:Number, transitionStyle:String);
gwd.actions.gwdSwipegallery.​goForwards​(galleryId:String);
gwd.actions.gwdSwipegallery.​goBackwards​(galleryId:String);
gwd.actions.gwdSwipegallery.​rotateOnce​(galleryId:String, duration:Number, direction:String);
gwd.actions.gwdSwipegallery.​stopRotation​(galleryId:String);
```

### [](#Carousel-Gallery "Carousel Gallery")Carousel Gallery

```
gwd.actions.gwdCarouselgallery.​goToFrame​(galleryId:String, frameNumber:Number, transitionStyle:String);
gwd.actions.gwdCarouselgallery.​goForwards​(galleryId:String);
gwd.actions.gwdCarouselgallery.​goBackwards​(galleryId:String);
gwd.actions.gwdCarouselgallery.​rotateOnce​(galleryId:String, duration:Number, direction:String);
gwd.actions.gwdCarouselgallery.​stopRotation​(galleryId:String);
```

### [](#360°-Gallery "360° Gallery")360° Gallery

```
gwd.actions.gwd360gallery.​goToFrame​(galleryId:String, frameNumber:Number, transitionStyle:String, direction:String);
gwd.actions.gwd360gallery.​goForwards​(galleryId:String);
gwd.actions.gwd360gallery.​goBackwards​(galleryId:String);
gwd.actions.gwd360gallery.​rotateOnce​(galleryId:String, duration:Number, direction:String);
```

### [](#Audio-Player "Audio Player")Audio Player

```
gwd.actions.gwdAudio.​play​(audioPlayerId:String);
gwd.actions.gwdAudio.​pause​(audioPlayerId:String);
gwd.actions.gwdAudio.​mute​(audioPlayerId:String);
gwd.actions.gwdAudio.​replay​(audioPlayerId:String);
gwd.actions.gwdAudio.​seek​(audioPlayerId:String, time:Number);
```

### [](#Video-Player "Video Player")Video Player

```
gwd.actions.gwdVideo.​play​(videoPlayerId:String);
gwd.actions.gwdVideo.​pause​(videoPlayerId:String);
gwd.actions.gwdVideo.​mute​(videoPlayerId:String);
gwd.actions.gwdVideo.​replay​(videoPlayerId:String);
gwd.actions.gwdVideo.​seek​(videoPlayerId:String, time:Number);
```

从整个开发流程上，GWD与早期的Flash是否相似，便于快速上手。只不过有缺憾的是，中文教程几乎没有，需要自己试水。

作为动画制作软件，我最先接触的是Flash，完全是出于兴趣自学的业余爱好者。但是，由于教学的需要，偶尔需要动画制作，于是居然摸索着做了不少动画作品。所以，一旦喜欢上什么，潜力是无限的。
