---
layout: post
title: Why isn't my markdown going onto a new line.  I want to put text on a new line in markdown without p tags
---

Here's a little tip.

When I was editing the README to the Discourse Advertising Plugin, items would stay on the same line even if I pressed enter for it to go on the next line.  For example:

If I wrote in markdown:
```
Hi Everyone,
I'm adcopywriter on github
```

On rendering it would turn out as:
```
Hi Everyone,I'm adcopywriter on github
```

I tried adding p tags but then that just added a space between the new line.  It looked like this:
```
Hi Everyone,

I'm ad copywriter on github
```

What was the solution?  It was just two spaces after the end of the last one!!!
```
Hi Everyone,  (<-- there are two spaces after "Hi Everyone,"space,space)
I'm ad copywriter on github
```

so... if you need to put text on a new line without a p tag or a space between the lines of text, put in two spaces after the end of the previous line.

Author: Github: Adcopywriter (Vi Nguyen)
