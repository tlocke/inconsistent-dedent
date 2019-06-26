Title: Prang
Date: 2015-09-10 10:24
Author: Tony
Slug: prang
Status: published

Having got [Odio](http://pythonhosted.org/odio/) to a reasonable state, the next step is to incorporate a [RELAX NG](https://en.wikipedia.org/wiki/RELAX_NG) validator into it, to make sure the output of Odio is always a valid [ODF](https://en.wikipedia.org/wiki/OpenDocument) document. I couldn't find a Python RELAX NG validator, so I've embarked on [Prang](https://github.com/tlocke/prang).  
  
Armed with the RELAX NG [specification](https://www.oasis-open.org/committees/relax-ng/spec-20011203.html), [tutorial](http://relaxng.org/tutorial-20011203.html) and [suggested algorithm](http://www.thaiopensource.com/relaxng/derivative.html), I'm tackling this daunting task. Actually, dear reader, I'm finding it tough going. I haven't given up though...
