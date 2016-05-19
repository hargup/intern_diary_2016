# Feb 2012

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
    * Chris Pearce questions the possibility of implementing content protection
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

    * Henri Sivonen argues that failing to describe the specs of the
      protection system EME doesn't provide benifits of interoperability and
level playing field for competition. Only lowering the R&D cost for
properietry DRM systems shouldn't be a good enough reason for W3C to work on
EME. [7]

    * Charles Pritchard makes an interesting observation that `<video>` and
      `<audio>` tags are intentionally about arbitary codecs and don't push
vendors for interoperability. He gave an example where trusted computing makes
sense. He also argues that an encrypted stream is no better than a arbitary
codec but  W3C should implement trusted computing anyway to protect the
privacy of people. [8]

    * John Foliot argues that they need to strip way the philosphical
      arguments about EME and think about from a purely technical point of
view and then he justifies EME by saying it what the economy wants. Failing to
realize that "This is what economy wants" is not a technical argument,
neither he justifies that W3C should do what CEOs want them to do.

    *  Carr, Wayne supports the proposal without justification. [10]

    * Henri Sivonen counters John's post by saying that standard setters need
      to make value judgement all the time and arguing "Don't use it if you
don't like it", is an extremly naive solution and doesn't tackle the issue of
lack of level playing field [11]. In the next email says that the lack of
interoperability of `<video>` and `<audio>` shouldn't be taken as role model
also. He countered Pritchard's example about Trusted computing by pointing out
in his example the "Evil Maid" was an adversary but in EME the adversary is
the user, he also says that it'll be laughable to say EME protect's user's
privacy.

    * Bob Lund supports the proposal by saying it is a good first step to
      support problems of content providers and device manufacturers. [13]

    * Tab Atkins points out that the legal difference between encyption and using
      an arbitary codec is that the former is covered by DMCA but the later
isn't. [14]

    * Specifically replying to Henri, Mark Watson argues that EME is not about
      adding DRM to the web but about improving existing plugin based system.
[15]

    * Boris Zbarsky says that EME is bad for the web if it requires new
      browsers to coordinate with companies while commming up. [16]

    * Ian Hickson draws a satire of John's "Don't use it if you don't like it"
      argument about DRM, argues that EME intentionally makes content
inaccessible hence it is unethical [17]. Glenn Adams calls Ian's argument non
sense and says DRM/Content Protection has nothing to do with impaired
users[18].

    * Glenn Adams supports EME on the behalf of Cox Communications and asks
      W3C to remain neutral on the fact that DRM should be used or not. [19]

    * Andreas Kuckartz opposes the proposal if it cannot be implemented by
      Open Source Software. [20]

    * Glenn argues the protecting users should mean protecting the interests
      of content consumers and content producers, and we should not bias
against users who are willing to pay for DRMed content. He points that
EME has to take care of the constrains imposed by licensing terms of content
providers, which might prevent usage of EME with open source implementation [21].

    * Mark Watson says "A Content Decryption Module implementing the
      'clearkey' keysystem can be implemented as Open Source. This serves as
an existence proof, at least.

Whether any given content provider believes any given keysystem
implementation meets their needs is up to them.

We are not proposing to standardize any Content Decryption Module except
clearkey, just as HTML does not mandate any video codec and for similar
reasons. So the specification as proposed can be implemented in Open Source
just as well as the rest of the Media Element." [22]

    * Glenn Adams calls for keeping licensing technical issues separate. [23]

    * Henri Sivonen says a more interesting to ask is if Netflix et al. are
      willing to use open source implementations of CDMs to provide their
content [24].

    * John Vernaleo replies to Glenn saying that he'll like to keep technical
      and legal issue seperate but that might mean keeping OSS out [25] to
which Glenn replies that this is over generalization and not all licenses
block OSS [26], to which John Vernaleo says that the specifics of the
restrictive policies are not important, what he is concerned about is building
a system where OSS cannot participate, he also warns that it is dangerous to
build mechanisms supporting some parties without thinking about their
consequences [27].

    * There was small misunderstanding where Henri says that HTML5 already
      supports cases where user is not treated as an adversary, which Clark
and Glenn found derogatory [28] [29] [30]. To which Henri later clarifies that
Henri probably meant the term "adversary" in the technical context of
cryptography [39]. (Exchanges of Clarke and Tab [42] [43], Andreas supports the
nontechnical usage of term adversary in context of DRM and points out to RMS [45])

    * Boris Zbarsky ... [32]

    *  Incompressible exchange between Charles and Kornel [33] [34]

    * Mark Vickers representing Comcast strongly supported the EME proposal
      claiming that EME will go a long way towards moving most of the
functionality of web to plugins. He compared EME to SSL and said like SSL, EME
will be a vital step enabling commerce and communications through web browser.
[35]

    * Charles argues that EME can help with privacy by ensuring that the
      content consumed by user doesn't get intercepted by third parties, he
mainly talks about browser extensions which be used for interception. He
asks the group to give a full analysis to the proposal so that it can be used
for the benefit of privacy [36].

    * Supporting Ian, Benjamin Hawkes-Lewis posts three weblinks demostrating
      the inverse relation between DRM and accessibility. Though two of these
three weblinks are now broken [37]. To which Glenn Adams responds by saying
that DRM/CP doesn't intentionally discriminates against accessiblity features.
He then points out that HTML5 offer work arounds in case where accessibility
features are missing. [38]

    * Henri says "Even if one accepted the notion that DRM discriminates
      equally against non-accessibility and accessibility features,
discriminating against accessibility features at all deserves special
attention, because traditionally under copyright law, accessibility is
privileged.Typically European countries have copyright acts that put
limitations on copyright (i.e. the copyright holder has less say) that enable
adaptations for accessibility purposes. DRM foils this, which is a recurring
theme in hearings about anti-circumvention legislation.

Suppose the content provider isn't providing a text track and has
applied DRM to the audio track. Suppose that the DRM proprietor places
a contractual requirements (amplified by anti-circumvention
legislation) on implementors that say the unscrambled audio samples
may only be sent to audio output hardware and must not be provided to
other processes. This would prevent the accessibility use of sending
the audio to a speech recognition system for generating captions on
the fly on the client side.
"

He also demands to know why scrambling is not being proposed as a solution.
[40] [41] To which Mark responds that JS is not a secure enough and it might
turn out to be to heavy. [50]

    * David Singer calls it a myth that HTML5 cannot play protected content.
      [44]

    * Mark Vickers argues that EME improves upon many of the accessibility
      issues in plugin systems used to play protected content by providing
standard ways to add accessibility features. [46]
     Mark further asks following questions to David and EME editors. [47]
"""
David Singer:
1. How would the application and user agent communicate the particular
   content-protection scheme? Would it be in the source element type and/or
codecs attributes? Can you give a concrete example?

2. How would the application key server connect to the user-agent key client?

3. Are there any examples deployed, prototyped or proposed for a specific
   content protection system using HTML5 in this manner?

David Dorwin, Adrian Bateman, Mark Watson:
1. Can you provide a functionality comparison of content protection using the
   current specs vs. with your proposal?
"""

    * David's responds to the question [48] and Mark responds by arguing that
      many browsers have entire media pipeline in the browers code and hence it
cannot use the content protection facilities available on the OS, he also
claims that it is not a myth that protected content cannot be run in HTML5
because there isn't a standard way to do it. [49] And then David responds
agains (will do the summarization later) [56].


    * To issue of creating unlevelled field for browser's Mark responds that
      the same situation exists in plugin based enviornments and EME improves
upon that. [50] To which Boris's response was that any new browser with correct
implementation of NPAPI can work with flash so the answer really depends on the
specifics of the Content Decryption Modules. He also questions the assumption
that browser developer will have greater control and more options in case of
EME [51]

    * Mark argues that there are practical difficulties for new browser with
      flash even if they have an implementation of NPAPI according to the
specification, he says CDMs provide more control to browsers because they are
smaller and have much less functionality. [52] According to Boris this is
different because there no legal difficulties, where as implementing a CDM
might lead to trouble with DMCA. [53]

    * Purely technical blabber [54] [55]





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

[9]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0338.html

[10]: http://lists.w3.org/Archives/Public/public-html/2012Feb/0341.html

[11]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0344.html

[12]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0345.html

[13]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0347.html

[14]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0348.html

[15]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0350.html

[16]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0352.html

[17]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0354.html

[18]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0362.html

[19]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0369.html

[20]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0374.html

[21]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0375.html

[22]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0377.html

[23]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0378.html

[24]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0379.html

[25]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0380.html

[26]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0381.html

[27]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0383.html

[28]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0384.html

[29]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0385.html

[30]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0386.html

[31]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0388.html

[32]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0387.html

[33]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0389.html

[34]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0390.html

[35]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0391.html

[36]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0393.html

[37]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0405.html

[38]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0408.html

[39]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0411.html

[40]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0412.html

[41]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0414.html

[42]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0416.html

[43]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0417.html

[44]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0418.html

[45]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0419.html

[46]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0420.html

[47]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0421.html

[48]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0422.html

[49]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0424.html

[50]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0426.html

[51]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0427.html

[52]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0428.html

[53]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0429.html

[54]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0430.html

[55]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0432.html

[56]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0433.html

# Github Notes

* 17th May 2016: Paul Cotton announces that ensuring CDM level
  interoperability is out of scope of the working group's charter [1].

[1]: https://github.com/w3c/encrypted-media/issues/192#issuecomment-219805449


# People

* Adrian Bateman works for Microsoft.

* Ian Hickson: He works for Google and is a part of CSS working group.

* Glenn Adams works for Cox Communications

* Silvia Pfeiffer Works at NICTA

* Chris Pearce works for Mozilla

* Eric Carlson works for Apple.

* Tab Atkins works for Google as a web standard's hacker http://www.xanthir.com

* Mark Watson works for Netflix

* Charles Pritchard works for Jumis

* Henri Sivonen works for Mozilla

* Carr, Wayne works for Intel

* Bob Lund works for Cable Labs

* Boris Zbarsky works for MIT and a quick search suggests he an insider of
  W3C.

* Kornel Lesiński

* Benjamin Hawkes-Lewis(bhawkeslewis@googlemail.com)'s isn't apparent from
  simple web search.

* David Singer works for Multimedia and Software Standards, Apple. He has
  written on identity management and privacy principles in W3C. https://www.w3.org/2011/track-privacy/papers/Apple.pdf https://www.w3.org/2011/identity-ws/papers/idbrowser2011_submission_51.pdf




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
