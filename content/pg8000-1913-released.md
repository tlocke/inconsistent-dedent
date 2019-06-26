Title: pg8000-1.9.13 Released
Date: 2014-07-27 04:31
Author: Tony
Slug: pg8000-1913-released
Status: published

I've been doing quite a bit of work on trying to get pg8000 to pass all the SQLAlchemy tests. As well as improving the pg8000 dialect of SQLAlchemy, it's also beneficial for pg8000 itself, because the SQLAlchemy tests are so comprehensive.  
  
Here are the [changes in this new pg8000 release](https://pythonhosted.org/pg8000/release_notes.html#version-1-9-13-2014-07-27):  
  

-   Reverted to using the string `connection is closed`{.docutils .literal} as the message of the exception that’s thrown if a connection is closed. For a few versions we were using a slightly different one with capitalization and punctuation, but we’ve reverted to the original because it’s easier for users of the library to consume.
-   Previously, `tpc_recover()`{.docutils .literal} would start a transaction if one was not already in progress. Now it won’t.

I've also created a [pull request](https://github.com/zzzeek/sqlalchemy/pull/125) for SQLAlchemy that should have it passing nearly all tests.  
  
Next steps are to work on some of the pg8000 bugs / feature request.

</p>

