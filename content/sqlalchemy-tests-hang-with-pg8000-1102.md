Title: SQLAlchemy tests hang with pg8000 1.10.2
Date: 2015-04-15 12:56
Author: Tony
Slug: sqlalchemy-tests-hang-with-pg8000-1102
Status: published

Before doing a new release of pg8000 I generally run the full suite of SQLAlchemy tests (as well as pg8000's own test suite). This time with pg8000 1.10.2 I found that the tests hung at:  

    test/dialect/test_oracle.py::CompatFlagsTest::test_ora8_flags PASSED

  
doing CTRL-C let the tests carry on, not missing out any. Since pg8000 passed its own tests, I went ahead and released it anyway. Publish and be damned! Not a good attitude.  
  
So here I am at the [Bristol Hack Night](http://www.meetup.com/CodeHub-Bristol/events/220774326/), and determined to fix this bug. I reached out to the SQLAlchemy mailing list, and got [some pointers](https://groups.google.com/forum/#!searchin/sqlalchemy/pg8000/sqlalchemy/JxVovTmw7m4/4dr3AynbP54J) from the ever helpful and hugely talented Mike Bayer.  
  
I've made no progress. Even printing stuff out to stderr made the bug go away. What will I do?  
  
Skip forward many days...  
  
I'm now at the [Meanbee Hack Night](http://www.meetup.com/Meanbee-Hack-Nights/events/221569943/) in Bath. After the lack of progress last time, I've got some new leads. The aforementioned Mike Bayer made a [second post](https://groups.google.com/forum/#!topic/sqlalchemy/TFJGXR0jKPo) saying:  

> 44a9820b4e02f65b3884fa2c016efc has a fix which adds explicit cleanup to a few connection objects that are checked out and not closed, leading to the pool.\_refs collection to not be empty when that particular test starts.

So I'll `fetch` that and see how the tests run...  
  
Everything runs okay now, so case closed.

</p>

