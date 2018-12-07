Readthedocs.org as a blog
=========================

Why I've never had a blog
-------------------------

I've always wanted to do a blog. Mostly for my sake.

The biggest problem is that I hate most traditional "blogging" platforms.  WYSIWYG editors 
irritate me.  Blogging on the "web" isn't always that convenient. 

So,  no blog. 

As a side note, I am a developer and my biggest weakness is documentation of the software I write.  
For similar reasons I hate most blogging platforms,  I find most documentation platforms kludgy 
and annoying.  I hate Wiki's,  largely because it is easy to forget about them and hence they don't 
get updated.  While reading a Wiki is fine,  the interfaces are not what I desire.  

Not documenting software isn't an option.  Without documentation,  people can't learn about
your work.  In my opinion, developers who don't document or comment in code are doomed to failure.
While documentation is a "burden", it's also a keep to software being complete and successful

It is also a high pain in the ass. 

Concepts behind Sphinx/Readthedocs.org
--------------------------------------

I've noticed a trend of projects using the Sphinx `Python Documentation Generator <http://www.sphinx-doc.org>`_.  I decided to give it a try. 

The general concept is to keep your software documentation close to the source code.  That is,  make
documentation part of the development process.  With Sphinx,  you use a very simple and easy to learn
mark up language to create documentation.  You can then "build" (quite literally) your documentation.
The mark up language is converted to HTML, PDF, etc.  Using different "themes" allows you to quickly
create very nice documentation.   Since the documentation isn't outside your source tree,  you are 
more likely to update your documentation.  Traditionally,  once you updated your source code, you would
have to pivot to a Wiki or some other web resource.  That is a pain. 

Another bonus of Sphinx is that is makes documentation fun.  At the very least, bearable.

How does `readthedocs.org <https://readthedocs.org>`_ fit into this?  

`Readthedocs.org <https://readthedocs.org`_ provides a hosting for your documentation.  For example,  the
`Suricata IDS <https://suricata.readthedocs.org>`_ uses Readthedocs.org.  I've started moving all my
documentation for `Sagan <https://sagan.readthedocs.org>`_ and `Meer <https://meer.readthedocs.org>`_
to Readthedocs.org (Note: my documentation is far from complete and is still a work in progress!). 
However,  Readthedocs.org is more than just a hosting place for documentation.  It a great and 
easy (ie - automatic) way for publishing documentation as well. 

I keep most of my source code for projects on `Github <https://github.com>`_.  For example, Sagan (https://github.com/beave/sagan) and Meer (https://github.com/beave/meer).  The documentation for both these
projects are in the https://github.com/beave/sagan/tree/master/doc/source and 
https://github.com/beave/meer/tree/master/doc/source directories. 

When I updated my documentation for either project and 'push' it to Github.com,  Readthedocs.org
automatically "see's" the update and automatically "builds" ("make html") and hosts my documentation.
This makes creating, publishing and hosting all within your source code incredibly easy and powerful!
It is several really great concepts tied together. 

Building a Sphinx/Readthedocs Blog
----------------------------------


First off,  I registered a domain.  While "beaves-blog.redthedocs.org" is okay, I wanted something a 
little more personal.  With that in mind,  I registered "beave.io".  The idea is to redirect traffic
to the "beave.io" site to my "beaves-blog.readthedocs.org". 

Apache
~~~~~~

This was pretty simple to accomplish.  I setup Apache to host "beave.io" and in the web sites 
root,  i placed the following .htaccess file.:

::

   # This will redirect all "beave.io" requests to my "beaves-blog.readthedocs.io".
   Redirect 301 / https://beaves-blog.readthedocs.io/


I also installed a `LetsEncrypt <https://letsencrypt.org/>`_ certificate.  Because, why not. 

Github
~~~~~~

I then made a new Github repo at https://github.com/beave/beave.  This site will only contain blog
posts like the one your are reading.  I then cloned it and made a "doc" directory.  I then installed
on my local system the tools I would need to use Sphinx. 

::

   sudo pip install sphinx_rtd_theme
   sudo apt-get install python-dev build-essential python-setuptools
   sudo easy_install sphinx
   sphinx-quickstart


The "sphinx-quickstart" will setup your "documentation" environment. 

Readthedocs
~~~~~~~~~~~

Once I have my templates created for my "blog",  I then "pushed" it to Github.com. 

I then pivot to `Readthedocs.org <https://readthedocs.org>`_ and login.  I then added a 
new repo in Readthedocs that points to https://github.com/beave/beave.  I told Readthedocs
to "import" and build this page out.   

From here on out,  I only have to do a few commands to push up a new blog any time I want. 


Putting it all together
~~~~~~~~~~~~~~~~~~~~~~~

If I want to make a new blog entry,  this is what I do:

::

   git clone git@github.com:beave/sagan # You could use https://github.com/beave/beave
   cd beave/doc/source
   vi index.rst        # Add my new blog entry to the index.rst
   vi newblowentry.rst # Edit my new blog entry.
   git commit -a      
   git push

If I want to see what the blog will look like before a commit/push,  in the "doc" directory
you can do:

::

   make html

That's it! I can now edit and publish blog entries from any where using the tools I enjoy!

Final Thoughts
~~~~~~~~~~~~~~

There are some limitations.  For example,  there is no "comment" area.  Since I've gone down this
road of Readthedocs.org as a blogging platform,  I might as well use Github.com "issues".  If you
would like to leave a comment about this or any other blog entry,  simple submit a issue at
https://github.com/beave/beave/issues

