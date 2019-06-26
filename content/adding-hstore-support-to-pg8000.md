Title: Adding hstore support to pg8000
Date: 2014-08-03 07:42
Author: Tony
Slug: adding-hstore-support-to-pg8000
Status: published

In the pg8000-1.9.14 release the changes were:  

-   Make `executemany()` set `rowcount`. Previously, `executemany()` would always set `rowcount` to -1. Now we set it to a meaningful value if possible. If any of the statements have a -1 `rowcount` then then the `rowcount` for the `executemany()` is -1, otherwise the `executemany()rowcount` is the sum of the rowcounts of the individual statements.
-   Support for password authentication. pg8000 didn’t support plain text authentication, now it does.

Now I think we can continue on our campaign to get pg8000 passing all of the SQLAlchemy tests. I thought we'd actually got there, but [Mike Bayer pointed out](https://github.com/zzzeek/sqlalchemy/pull/88#issuecomment-44669582) that I was running the default version of PostgreSQL which doesn't have the HSTORE and JSON types, and tests for these were failing. I'm running Ubuntu, so I wonder how to enable these types?  
Hold on, first let's do a test for HSTORE that fails:  

> `val = '"a"=>"1"'self.cursor.execute("SELECT cast(%s as hstore)", (val,))retval = self.cursor.fetchall()self.assertEqual(retval[0][0], val)`

Right, now we're getting the error 'HSTORE does not exist'. Good, that's what we expect. From [the docs](https://help.ubuntu.com/community/PostgreSQL) it looks like we just do:  

> `sudo apt-get install postgresql-contrib`

and we have to enable the extension:  

> `CREATE EXTENSION hstore; `

And it works! Also, our test doesn't fail, so pg8000 supported HSTORE all along. Let's run the SQLAlchemy tests and see what happens. Well, everything seems to work, so all good! I think we can mark the issue in GitHub as closed and that's the end of the story.

</p>

