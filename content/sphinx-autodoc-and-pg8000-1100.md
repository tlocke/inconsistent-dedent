Title: Sphinx autodoc and pg8000-1.10.0
Date: 2014-08-30 11:16
Author: Tony
Slug: sphinx-autodoc-and-pg8000-1100
Status: published

In pg8000 we've got the problem that docs are duplicated in the code and the documentation pages. We're using Sphinx, so my plan is to use [autodoc](http://sphinx-doc.org/ext/autodoc.html), which will pull docstrings from the Python code into the documentation pages.  
  
Right, I've done that. It worked okay, the only wrinkle was that I had to include the docs for instance variables in the overall class docs.  
  
Btw, I've just released [pg8000-1.10.0](https://pythonhosted.org/pg8000/index.html), which includes the [release notes](https://pythonhosted.org/pg8000/release_notes.html#version-1-10-0-2014-08-30).
