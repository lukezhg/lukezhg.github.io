---
layout: post
title: "Firefox extension FireGesture Scripts"
date: 2013-08-26 18:23
comments: true
categories: "技术技巧"
tags: [en, firefox, extension]
---
I found the firefox extension Firegesture is very useful. You can self-define the function of your gestures.  

The following are my scripts:  
1.  Sina Weibo(DUDU)  
<code>
	var sel = 'http://v.t.sina.com.cn/share/share.php?title='+encodeURIComponent(document.title)+'&url='+encodeURIComponent(window.content.location.href)+'&source=bookmark';
	gBrowser.loadOneTab(sel, {
		inBackground: true,
		relatedToCurrent: true
	});
</code>
2. iciba(RLR)  
<code>
	var word = getBrowserSelection();
	if (!word)
		return;
	var sel = 'http://www.iciba.com/'+encodeURIComponent(word);
	gBrowser.loadOneTab(sel, {
		inBackground: true,
		relatedToCurrent: true
	});
</code>
3.  Copy the title and url  
<pre><code>
const AS_HTML = false;

function htmlEscape(s) {
  s = s.replace(/&/g, "&amp;");
  s = s.replace(/>/g, "&gt;");
  s = s.replace(/</g, "&lt;");
  s = s.replace(/"/g, "&quot;");
  return s;
}
var url = window.content.location.href;
var title = window.content.document.title;
var txt = AS_HTML ? 
  '<a href="' + htmlEscape(url) + '">' + htmlEscape(title) + '</a>' : 
  title + "\n" + url;
var clipboard = Cc["@mozilla.org/widget/clipboardhelper;1"]
                .getService(Ci.nsIClipboardHelper);
clipboard.copyString(txt);
</code></pre>