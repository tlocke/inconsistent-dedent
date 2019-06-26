Title: Versioneer
Date: 2014-06-30 13:00
Author: Tony
Slug: versioneer
Status: published

One way to find the version of a Python package is to look at the \_\_version\_\_ attribute. So for pg8000 you should be able to do:  
  
`pg8000.__version__`  
  
Unfortunately you couldn't do that with [pg8000](http://pythonhosted.org/pg8000/), so my task was to find the best way to implement it. The easiest way is to simply add the following line to the  
  
`__init__.py` file:  
<sample>`__version__ = '1.9.10'`</sample>  
<sample>` `</sample>  
but that would have meant having to manually alter the file each time there's a release, and I already have to enter the version number in three places, `setup.py` and `doc/conf.py` and in a Git tag. I had a Google around, and found [Versioneer](https://github.com/warner/python-versioneer). This gets the version from Git, so after versioneering pg8000 the release process is:  
  
<sample>`git tag -a x.y.z -m "Version x.y.z"python setup.py register sdist upload build_sphinx upload_docs`</sample>  
<sample></sample>  
I may have been a bit premature in writing this post, because although it seems to work, I haven't used it in anger yet!
