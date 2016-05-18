# June 2012

* 21 Feb 2012: Adrian Bateman announced at the public-html mailing list that
  they have been working to provide an API to play encrypted media in HTML 5
[1]. One of the mentioned reason was that many content providers and
application developers have said they can't use `<audio>` and `<video>` because
HTML lacks robust content protection.

    * Ian Hickson called the proposal unethical.
    * Glenn Adams objected to linking EME to issue 171 which talked about
      adding ways to pass arbitary parameters to audio and video tags. Glenn
ratter proposes to have generic exchange mechanism which are not specifically
related to encrypted content. He criticizes not supporting params.
    * A lot of talk there after is about comparison with `<object>` in a purely
      techinical sense.
    * Chris Pearce questions the possiblity of implementing content protection
      in a FOSS browser.
    * Eric Carlson said EME proposal is workable.
    * Tab Atkins [2] points out that the sole purpose of EME is DRM, he said
      DRM is "technically impossible and practically useless, imposing
unnecessary costs on legitimate users while doing nothing whatsoever to
actually stop copyright infringement." He is disappointed that his employer,
Google co-edits the proposal.
    * Glenn Adams argues that Firefox can use a OS API like mechanism of
      implement EME where they don't have to reveal the source code the
decryption module.
    * Mark Watson argues that [3]
        * Millions of $$ of Engineering effort will go waste if they don't
          standarize DRM on the web.
        * EME is not an issue with Firefox from specification point of view
          because they don't specify the content Decryption Module.
        * The aim of DRM is to act like a speed bump for copyright infriengment
          and in that way it is effective. (Question: Is this speed bump
effective)

    * Charles Pritchard argues that obfuscation should be enough for EME's
      intended pupose as only programmers can grab the content who is the
99.99% of world's population. He says" "consumer" content protection is just a
silly cat and mouse game of make-work opportunities for corporate attorneys and
501c structures. It's well-established that content protection does not stop
any consumer products from being pirated. Obfuscation works just fine for
stopping the average consumer. Everything else is just extra work,
unfortunately necessary to keep contracts from getting wet."

    * Tab Atkins [4] made a really good point that commercial video can be done
      without DRM and a example of it are Indie producers on youtube. He also
argues for the lack of interoperability. BTW Thinking on DRM free commercial
systems, a good way to earn money can be inserting a ad in the video and more
viewing (+ pirating) of the video just means more ad revenue, the producers
only need to have a method to estimate their viewership to estimate the ad fee.
    Tab also talked about the comedian Louis CK who made a million dollar
selling videos in DRM-free format.

    * Charles Pritchard argues that there is no need of EME as `<video>` is
      codec agnostic and they can stream the video on a codec which only they
support. [5]

    * Mark Watson counters the cost to the users because of DRM with the cost
      of fragmentation. [6]




* 08 June 2012, Paul Cotton announced the mailing list and said that they'll
  start working on the EME draft.


[1]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0273.html

[2]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0317.html

[3]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0324.html

[4]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0326.html

[5]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0328.html

[6]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0329.html

[7]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0333.html

[8]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0337.html


# People

* Adrian Bateman works for Microsoft.

* Ian Hickson: He works for Google and is a part of CSS working group.

* Glenn works for Skynav

* Silvia Pfeiffer Works at NICTA

* Chris Pearce works for Mozilla

* Eric Carlson works for Apple.

* Tab Atkins works for Google as a web standard's hacker http://www.xanthir.com

* Mark Watson works for Netflix

* Charles Pritchard works for Jumis

* Henri Sivonen works for Mozilla




# Notes from May 2013 discussion

* There have been a lots of internal disagreement about EME, some are found
  here on W3C mailing list. https://www.w3.org/community/restrictedmedia/


* Author's on the list: Julio Cesar Serrano, Andreas Kuckartz(AK)

* Discussion on the Formal Objection by EFF and reply by John Foliot https://lists.w3.org/Archives/Public/public-html-admin/2013May/0146.html
* John F is the principal accessibility strategist, for the last 15 year he has
  worked to make make websites more accessible, prior to that he worked for the
record industry for 15 year.;
    * https://lists.w3.org/Archives/Public/public-html-admin/2013May/0153.html

* His primary objection to the formal objection is that stopping EME won't stop
  DRM in web, it is already a defacto standard and the big companies who are
behind it will use some other business body or standards organization to push
their agenda, btw he also supported the right to control and monetize what
companies have invested in.

* John C. Vernaleo: Opposed to W3C supporting DRM, and does not say that
  removing EME will make DRM go away.

* piranna@gmail.com objects to EME https://lists.w3.org/Archives/Public/public-html-admin/2013May/0154.html
* She is an independent developer from Spain, probably a recent graduate. http://pirannafs.blogspot.in


* Tab Atkins Jr. accuses W3C's EME as double speak on the name of open
  standard; https://lists.w3.org/Archives/Public/public-html-admin/2013May/0155.html

* Tab Atkins works for Google as a web standard's hacker http://www.xanthir.com

* Mark Watson from Netflix makes the comparison that EME doesn't make anything less open than they are today.
https://lists.w3.org/Archives/Public/public-html-admin/2013May/0156.html

* Casey Callaghan argues that EME standard will lead to the fragmentation of
  the web standard https://lists.w3.org/Archives/Public/public-html-admin/2013May/0162.html
    She is a software developer from South Africa, probably independent.

* François REMY argues that it will be worse to have a EME which is supported
  by "all" browsers but is not a standard.
https://lists.w3.org/Archives/Public/public-html-admin/2013May/0164.html
Francois is a participant in the CSS working group and is the cofounder of the
Extensible Web Community Group. He now works for Microsoft, though he didn't at
the time of the posting of the mail.; http://fremycompany.com/


* There are at least three mailing lists on W3C where EME is being discussed,
  public-html-admin@w3.org, public-restrictedmedia@w3.org,
public-html-media@w3.org


Links:

* Status of Formal Objection https://dev.w3.org/html5/status/formal-objection-status.html#EME-1
