Hi,
Friday 24 June 2016

Yesterday, I created a [Gender Gap visualization for Indic Language
Wikipedias](http://hargup.in/whgi-indic/gender-by-language.html), it took me
more time than I expected. I had to change the template here and there. The
changes chart was not showing up properly because some of the wikipedia had no
change in the number of biographies in the last week, and you know zero is not
a good number for a log scale plot. One language had a negative change, i.e., a
biography was deleted in the previous week. After that work was over, I made a
[pull request to bigbang](https://github.com/sbenthall/bigbang/pull/258)
project, I made a small change to use argparse for argument parsing instead of
system arguments, that also helps in displaying a nice help menu. BTW it looks
like Travis tests have failed, so it looks like I'll have to put more effort
into it.

Today I'll work on OpenSocial and will spend an hour at the end to clean up EME
report.
