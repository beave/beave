Your "Threat Intel" is over rated.
==================================

... and here is why...


What is "Threat Intel"
~~~~~~~~~~~~~~~~~~~~~~

Before we begin, let's define what I'm referring to as ``Threat Intel``.  In this arcticle,  I am
strictly referring to the use of ``Indicators of Compromise`` (IoC) lists.  This includes the use
of ``bad`` or ``known`` threat actor TCP/IP addresses,  file hashes,  file names,  e-mail addresses, 
domain names, etc.  The attacker in question in this article would be semi-advanced and possibly
targetting your network.

Okay, It isn't useless
~~~~~~~~~~~~~~~~~~~~~~

When I say, "Threat Intel is over rated",  I do not mean that it is useless.  I am 
repeatedly asked about Threat Intelligence and how we use it.  I get asked in such a way that people
expect it to bring "magic sauce" to their securty program.  The general concept is that the more 
"intelligence" (data) one has, the better.  This isn't the case. 

First off,  Threat Intel's usefulness is better applied backward facing and not forward facing.  That
is,  Threat Intel is good to finding historical events that have happened in your network.  In many 
cases,  when you try to apply it to future events, you come up empty handed because the attacker has
already changed there techniques. 

Attackers know about "Threat Intel"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Do you know why?  `Because attackers use "Threat Intelligence" too!`.  This shouldn't be astonishing. 
What is astonishing to me is that many security minded folks don't seem to relize this.  How do we
know this?  Because attackers have told us.  Case and point,  "Hacking Team Hack" 
(https://pastebin.com/0SNSvyjJ).

::

   "I didn't want to make the police's work any easier by relating my hack of
   Hacking Team with other hacks I've done or with names I use in my day-to-day
   work as a blackhat hacker. So, I used new servers and domain names, registered
   with new emails, and payed for with new bitcoin addresses."


From an attackers point of view,  "Threat Intel" can be just as useful to them as it is to your team.
You might look at Threat Intel as a "what to look for" list.  The attacker might look at it as a 
"what they might be looking for and to avoid doing" list.

An attacker might use pervious undisclosed or new launch sources,  modificaiton of attack binaries 
to modify file hashes) to avoid your threat intel.  It is pretty simple and easy to stay ahead of 
"Threat Intel". 

So when is Threat Intel useful?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As I stated before,  the usefulness is in post success or attempted  attack discovery.  Using this 
data can show if you have been successfully or unsuccessfully compromised in the past from any 
individual threat. 

This is a good thing and mining for such data within your organization is a smart thing to do.  
However,  it doesn't much help you forward because it is likely the attacker has already changed 
there tactics, methods and proceedures. 

Should you apply that data forward facing?  Sure,  you might get lucky.  You might also introduce
many false positives.  Anyone who has worked in Threat Intel has seen shared hosting providers listed,
public NTP servers and DNS server listed which can cause headaches.

Which brings me to another point.

Consider your sources
~~~~~~~~~~~~~~~~~~~~~

The general thougth is "put every source into a big pot and stir it up!".   That is,  the 
more sources you have for Threat Intel,  the better.   We use to have a term about this when I 
was younger about beer:

:::

   "It's about quantity not quality." 

That gererally sums up what I believe many people feel.  As I've gotten older,  my views on 
Threat Intel (and Beer) have flipped.

:::

   It's about quality not quantity."

More != Better.  In fact,  it can cause you more headaches.  Here is a simple example; how old
is the data?  If the TCP/IP address listed is several years old,  then it's likely not being used
in active attacks.  If it is being used,  `when was the last time it was used`.  Your Threat Intel
should be able to supply this information to your tools.  This way you can make queries like, "Show
me Threat Intel hits with a last seen data of 6 months or earlier".  This is functinality we have
built into ``Bluedot`` and `Sagan <https://sagan.io>`_. 

We use to use a major Threat Intelligence provider.  A lookup of an IP address might tell us that
it was associated with a known botnet.  This raise the following questions:

   1. What sort of "botnet"?
   2. When was it discovered?
   3. When was it last seen?
   4. Are there any notes or references around this type of bot? 

We asked the provider about supplying this type of data.  We where told that wouldn't be possible.

Verify and understand the feeds you are pulling from.  More is not better.  In face,  there has been
discussions about attackers "poisoning the data well" of Threat Intel simply to throw off security
teams.

Verify your data.  Even if it comes from a reputable souce,  mistakes can be made.  For example, 
we use ``FBI Flash reports`` as part of our data collection.  We have seen incomplete MD5 sums in
flash reports.  We have seen feeds mistakingly put IP addresses like 8.8.8.8 as IOCs. 

Don't just consume, validate before consumption.

WHen to play it forward
~~~~~~~~~~~~~~~~~~~~~~~

So if Threat Intel is really good on historical data but not as good forward facing, what do you do?
As stated, applying publically disclosed Threat Intel will have limited use but you might get lucky.
If you have the ability,  adding internally generated data to your Threat Intel sources can be a good
thing.  If you've seen some cleaver attacks,  collecting the IOCs and adding them into your back end
(MISP, etc) is a great thing to do.  

Another good source is "Honeypots" located within your network.  Placement from the inside (to catch
insider threats/lateral movement attempts) and external.  Typcally,  external Honeypots lead to a lot 
of data that isn't terribly useful.  However,  if done right and placed within your network,  you might
catch recon attampts from a more advanced attacker.   This is cheap 




Not your primary path
~~~~~~~~~~~~~~~~~~~~~

Threat Intel is only a tool or another part of the puzzle.  Threat Intel shouldn't be dependant on by
itself as a primary indicator.  When coupled together with other indicators,  it can add confidence to
the event.  

