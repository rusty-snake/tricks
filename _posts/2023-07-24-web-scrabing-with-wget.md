---
layout: post
title: "Web Scrabing with wget"
author: "rusty-snake"
#tags:
---


~~~bash
wget \
	--recursive \
	--adjust-extension \
	--convert-links \
	--page-requisites \
	--tries=3 \
	--wait=5 \
	--random-wait \
	--user-agent='Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0' \
	https://example.com/foo/bar.html
~~~

`--recursive --adjust-extension --convert-links --page-requisites`
: Common base for web scrabing.

`--tries=3 --wait=5 --random-wait`
: Prevent DoS-ing of the server. Do not omit this, a properly protected server will block your IP!

`--user-agent='Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0'`
: Reduce likelyhood of getting blocked by faking a Firefox User-Agent. You can view the UA of your Firefox on `about:support`.

`wget` has many options for web scrabing, best you read the
`Recursive Retrieval Options` and `Recursive Accept/Reject Options` sections
in the [wget manpage](https://www.man7.org/linux/man-pages/man1/wget.1.html)
and <https://www.gnu.org/software/wget/manual/html_node/Recursive-Download.html#Recursive-Download>.
