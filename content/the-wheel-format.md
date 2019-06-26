Title: The Wheel Format
Date: 2014-09-15 12:00
Author: Tony
Slug: the-wheel-format
Status: published

Actually, the [False Lead](http://inconsistent-dedent.tlocke.org.uk/2014/09/a-false-lead.html) kind of led to something in the end. When pg8000 established a connection, messages end in either a READY\_FOR\_QUERY or a ERROR\_RESPONSE, whereas in the query phase, messages only ever end with a READY\_FOR\_QUERY. So I've separated out the two bits of code, and each is simpler than the combined one. Hopefully, this will help in tracking down the long-standing bugs (or even solve them!).  
  
In other news, there's been a request that pg8000 be packaged in the [.whl](http://legacy.python.org/dev/peps/pep-0427/) format on the cheese shop. I did a bit of reading, and it seems like a really good idea. So that's my next task...
