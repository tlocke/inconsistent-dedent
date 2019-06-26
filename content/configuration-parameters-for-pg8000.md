Title: Configuration Parameters For pg8000
Date: 2014-08-20 07:40
Author: Tony
Slug: configuration-parameters-for-pg8000
Status: published

I've been getting various requests for [pg8000](http://pythonhosted.org//pg8000/) to use the same [environment variables as the PostgreSQL client applications](http://www.postgresql.org/docs/9.3/static/libpq-envars.html). At first sight this seems like a good idea, because it provides standardization in that pg8000 would work straight away with the environment variables that you've already got set up for the PostgreSQL client applications.  
  
However, pg8000 is a library and so different considerations apply. As a library can be used in all sorts of scenarios, I think it's better for the application to decide how it gets its configuration values. If PostgreSQL environment variables make sense for the application, then that application should implement that. The job of pg8000 is to merely take the parameters of the connect function. Anything more would add to the complexity of pg8000 which we're always trying to avoid.  
  
So, I'm minded to turn down the requests for adding different configuration methods.
