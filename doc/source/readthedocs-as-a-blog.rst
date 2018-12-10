Readthedocs.org as a blog
=========================

Why I've never had a blog
-------------------------

I've always wanted to have blog.

The biggest problem is that I hate most "blogging" platforms.  WYSIWYG editors 
irritate me.  Blogging on the "web" isn't always that convenient. 

So, no blog. 

As a side note, I am a developer and one of my biggest weakness is documentation of the 
software I write.  For reasons similar to why I hate most blogging platforms,  I find most documentation 
platforms kludgy and annoying.  I hate Wiki's,  largely because they are easy to forget about and 
don't get updated.  Being a "reader" of a Wiki is okay.  Being the "writer" of a Wiki is a pain.

Not documenting software isn't an option.  Without documentation,  people can't learn about
your work.  In my opinion, developers who don't document or comment in code are doomed to failure.
While documentation is a "burden",  it is a key part of making any software complete and 
successful.

It is still a pain in the ass. 

Concepts behind Sphinx/Readthedocs.org
--------------------------------------

I've noticed a trend of projects using the `Sphinx Python Documentation Generator <http://www.sphinx-doc.org>`_.  I decided to give it a try. 

The general concept is to keep your software documentation close to the source code.  That is,  make
documentation part of the development cycle.  With Sphinx,  you use a very simple and easy to learn
mark up language to create your documentation.  You can then "build" (quite literally) your documentation.
When you "compile" your documentation, the mark up language is converted to HTML, PDF, etc.  
Using different "themes" allows you to quickly create visually appealing and useful documentation. 
Since the documentation is inside your source code tree,  you are more likely to update it.  

Another bonus of Sphinx is that is makes documentation fun, or at the very least, bearable.

How does `readthedocs.org <https://readthedocs.org>`_ fit into this?  

`Readthedocs.org <https://readthedocs.org`_ provides hosting for your documentation.  For example,  the
`Suricata IDS <https://suricata.readthedocs.org>`_ uses Readthedocs.org.  I've started moving all my
documentation for `Sagan <https://sagan.readthedocs.org>`_ and `Meer <https://meer.readthedocs.org>`_
to Readthedocs.org (Note: my documentation is far from complete and is still a work in progress!). 
However,  Readthedocs.org is more than just a hosting place for documentation.  It a great and 
easy (ie - automatic) way for publishing documentation as well. 

Here's what I mean.

I keep most of my source code for projects on `Github <https://github.com>`_.  For example, Sagan (https://github.com/beave/sagan) and Meer (https://github.com/beave/meer).  The documentation for both these
projects are in the https://github.com/beave/sagan/tree/master/doc/source and 
https://github.com/beave/meer/tree/master/doc/source directories. 

When I updated my documentation for either project and 'push' it to Github.com,  Readthedocs.org
automatically "see's" the update and automatically "builds" ("make html") and hosts my documentation.
This makes creating, publishing and hosting all very simple.  Readthedocs.org has tied several
great concepts together.

The Readthedocs team have a great "getting started" video at https://docs.readthedocs.io/en/latest/intro/getting-started-with-sphinx.html.

Building a Sphinx/Readthedocs Blog
----------------------------------

Here's how I built out my "blog" platform.

First,  I registered a domain.  While "beaves-blog.redthedocs.org" is okay, I wanted something a 
bit more personal.  With that in mind,  I registered "beave.io".  The idea is to redirect traffic
from the "beave.io" to my "beaves-blog.readthedocs.org". 

Apache
~~~~~~

Setting up Apache to handle "beave.io" redirects to "beaves-blog.readthedocs.org." was pretty simple to 
accomplish.  After getting Apache setup,  i created a ``.htaccess`` file in my web root for
"beave.io".

::

   # This will redirect all "beave.io" requests to my "beaves-blog.readthedocs.io".
   Redirect 301 / https://beaves-blog.readthedocs.io/


I also installed a `LetsEncrypt <https://letsencrypt.org/>`_ certificate.  Because, why not.  More
information about how to use LetsEncrypt and ``certbot``,  see: https://certbot.eff.org/lets-encrypt/debianstretch-apache.html

Github
~~~~~~

I then made a new Github repo at https://github.com/beave/beave.  This site will only contain blog
postings like the one your are reading now.  I then cloned the repo and made a "doc" directory.  
I then installed on my local system the tools I would need to use Sphinx. 

::

   sudo apt-get install python-dev build-essential python-setuptools
   sudo easy_install sphinx
   sudo pip install sphinx_rtd_theme
   sphinx-quickstart


The "sphinx-quickstart" will setup your "documentation" environment. 

Readthedocs
~~~~~~~~~~~

Once I have my templates created for my "blog",  I then "pushed" it to Github.com. 

I then pivoted to `Readthedocs.org <https://readthedocs.org>`_ and logged in.  I added a 
new repo in Readthedocs.org that points to https://github.com/beave/beave.  I told Readthedocs.org
to "import" and build documentation that repo. 

From here on, when I "push" a new blog entry up to https://github.com/beave/beave,  Readthedocs.org 
will clone my repo, build the "documentation" (blog) and publish it.

Putting it all together
~~~~~~~~~~~~~~~~~~~~~~~

If I want to make a new blog entry,  this is what I do:

::

   git clone git@github.com:beave/sagan # You could also use https://github.com/beave/beave
   cd beave/doc/source
   vi index.rst        # Add my new blog entry to the index.rst
   vi newblowentry.rst # Edit my new blog entry.
   git commit -a      
   git push

If I want to see what the blog will look like before a commit/push,  in the "doc" directory
you can type this:

::

   make html

That's it! I can now edit and publish blog entries from any where using the tools I enjoy!

Final Thoughts
~~~~~~~~~~~~~~

There are some limitations. For example,  there is no "comment" area.  Since I've gone down this
road of Readthedocs.org as a blogging platform,  I might as well use Github.com "issues".  If you
would like to leave a comment about this or any other blog entry,  simple submit a issue at
https://github.com/beave/beave/issues


