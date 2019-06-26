Title: Timeout with socket.makefile()
Date: 2015-02-22 10:50
Author: Tony
Slug: timeout-with-socketmakefile
Status: published

The [question was asked](https://groups.google.com/forum/#!topic/pg8000/3BefdOSvg5g), 'without a socket timeout in pg8000, how can we tell if there's been a network failure or similar problem?'.  
  
The reason the socket timeout was removed was this sentence in [the docs](https://docs.python.org/2/library/socket.html#socket.socket.makefile) for socket.makefile():  

> The socket must be in blocking mode (it can not have a timeout).

However in the [Python 3.4 docs](https://docs.python.org/3.4/library/socket.html#socket.socket.makefile) it says:  

> The socket must be in blocking mode; it can have a timeout, but the file object’s internal buffer may end up in a inconsistent state if a timeout occurs.

 So as long as we throw away the file object if a timeout occurs, we're okay to have a timeout under 3.4.

</p>

