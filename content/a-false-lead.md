Title: A False Lead
Date: 2014-09-06 09:32
Author: Tony
Slug: a-false-lead
Status: published

There are a couple of bugs with pg8000 that I've been unable to reproduce, after trying quite hard for some time. The other day I had a flash of inspiration that it could be caused by not closing the connection when there's a timeout on reading a response from the server. Let's see if I can create a test that fails.  
  
Ah no, that can't be it. If this type of socket has had a timeout, then an exception is raised if you try to read from it again.
