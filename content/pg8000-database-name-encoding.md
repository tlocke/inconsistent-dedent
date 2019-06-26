Title: pg8000: database name encoding
Date: 2015-01-17 05:23
Author: Tony
Slug: pg8000-database-name-encoding
Status: published

We had a bit of a bootstrapping problem with [pg8000](https://github.com/mfenniak/pg8000), where the first message of the protocol contains the database name. The database name could be in one of a number of character sets eg. Unicode or EUC-JP. The problem is that when pg8000 sends the first message, it doesn't know the encoding, and so can't encode the database name correctly!  
  
The answer, I found from [an email](http://www.postgresql.org/message-id/1330344173.7111.23.camel@vanquo.pezone.net) is:  

> In the connection request, you effectively need to specify the user name (and database name) as bytes in the encoding that you created them in.I don't think this is documented in an obvious way.

So the user of pg8000 has to provide the database name as bytes, and then this is passed directly to the server.  
  
As a convenience for users, pg8000 detects if the database name is provided as a unicode type, and if it is it encodes it as utf8.  
  
The process of getting to this happy solution was a roundabout to-ing and fro-ing between me and [Mathieu Fenniak](https://github.com/mfenniak), and I don't think either of us would have got there on our own (or it would have taken a lot longer). So a fruitful collaboration!  
  
I'm now continuing work on porting [Imprimatur](https://github.com/tlocke/imprimatur) to Python...

</p>

