Title: pg8000-1.9.11 Released
Date: 2014-07-20 04:12
Author: Tony
Slug: pg8000-1911-released
Status: published

[pg8000-1.9.11](https://pythonhosted.org/pg8000/) has been released. The changes are:  

-   <div class="first">

    Add support for two-phase commit DBAPI extension. Thanks to Mariano Reingart’s TPC code on the Google Code version:

    </div>

    <https://code.google.com/p/pg8000/source/detail?r=c8609701b348b1812c418e2c7>  
   on which the code for this commit is based.  
-   <div class="first">

    Deprecate `copy_from()`{.docutils .literal} and `copy_to()`{.docutils .literal} The methods `copy_from()`{.docutils .literal} and `copy_to()`{.docutils .literal} of the `Cursor`{.docutils .literal} object are deprecated because it’s simpler and more flexible to use the `execute()`{.docutils .literal} method with a `fileobj`{.docutils .literal} parameter.

    </div>

-   <div class="first">

    Fixed bug in reporting unsupported authentication codes. Thanks to <https://github.com/hackgnar> for reporting this and providing the fix.

    </div>

-   <div class="first">

    Have a default for the `user`{.docutils .literal} paramater of the `connect()`{.docutils .literal} function. If the `user`{.docutils .literal} parameter of the `connect()`{.docutils .literal} function isn’t provided, look first for the `PGUSER`{.docutils .literal} then the `USER`{.docutils .literal} environment variables. Thanks to Alex Gaynor <https://github.com/alex> for this suggestion.

    </div>

-   <div class="first">

    Before PostgreSQL 8.2, `COPY`{.docutils .literal} didn’t give row count. Until PostgreSQL 8.2 (which includes Amazon Redshift which forked at 8.0) the `COPY`{.docutils .literal} command didn’t return a row count, but pg8000 thought it did. That’s fixed now.

    </div>

</p>

