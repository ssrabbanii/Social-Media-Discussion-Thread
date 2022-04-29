# Social-Media-Discussion-Thread
Developed a simple system in Python to maintain information about users and their posted articles in a social media. 

In this project, a simple system is developed to maintain information about users
and their posted articles in a social media. Based on the information, I could find out some interesting
facts. There are several key functions in this system.

A user needs to first register with the system, by providing the name (first name and last name), a
username, and a password. Auxiliary information like date-of-birth, phone number is optional.
Each user may post a number of articles. Each article contains a title, a textual content and a date when
it is posted.

Users may have friends. Note that friend is a symmetric relation here, i.e. if Y is a friend of X, then
X is also a friend of Y. However, it is not transitive, i.e. if Y is a friend of X and Z is a friend of Y, then
it is not necessarily true that Z is also a friend of X.

Articles may form a thread via quoting part of another article. This is similar to the thread of postings
in BlackBoard Discussion. 

Let us simplify the quoting scenario that each article can quote at most one
article. Of course, an article may not need to quote any article. Note that in reality, social media posts
may include multiple references and that will make the situation much more complicated. An article
without quoting any article is called an anchor. 

An article that quotes another article is called a report,
and the article that got quoted is called a source. For example, it is possible that article A1 is an anchor,
which is a source quoted by article A2. 

Therefore, article A2 is a report for A1. However, A2 can also
serve as a source to be quoted by A3 and A4. So A3 and A4 are reports for A2 as well as A1 (transitive
relationship). 

Another article A5 may also quote A1 as source. The following diagram illustrates the basic
idea with an example involving five articles as explained above posted by 4 users.

To solve this problem, there is a need to perform data abstraction, namely, determine the type of data
to be used and how they are being stored inside the program. In this project, you can see that there are
some important entities, namely, users and articles.I decided on how a user is being
represented inside the Python program and there are many different ways. The particular way I have
chosen to represent my data will form the basis of data abstraction. Some representations are better in
certain contexts or applications, but may be worse in some other.


After designing for the key data structure or representation, I have implemented some functions in
your system to read the data (from keyboard or from files) and store in the memory (i.e. Python variables)
for further processing by additional functions. This is the algorithmic part of the project.

It is interesting in social networks to identify KOL (key opinion leaders) and their relationship, or to
investigate into whether friends tend to quote articles posted by each other, within a social circle. 

To support this kind of investigations, a system is developed to store the data for the users and articles.
Then my system also supports different data access requests to the collected set of data. Note that
in real social network, there is often a need to analyze the content of posts to identify their similarity,
but we are not doing this complex procedure in this project.
