_Obfuscation_ [DONE]

    * Charles Pritchard argued that there is no need of EME as `<video>` is codec agnostic and the media can be streamed at arbitary codec which only supported by the media provider. and they can stream the video on a codec which only they support. [5]


    Charles Pritchard argues that obfuscation should be enough for EME's intended pupose as only programmers can grab the content who is the 99.99% of world's population. He says" "consumer" content protection is just a silly cat and mouse game of make-work opportunities for corporate attorneys and 501c structures. It's well-established that content protection does not stop any consumer products from being pirated. Obfuscation works just fine for stopping the average consumer. Everything else is just extra work, unfortunately necessary to keep contracts from getting wet."


    * Tab Atkins pointed out that the legal difference between encryption and using an arbitrary codec is that the former is covered by DMCA but the later isn't. [14]

Henri demands to know why scrambling is not being proposed as a solution.
[40] [41] To which Mark Watson responded that JS is not a secure enough and it might turn out to be to heavy to carry out decryption. [50]


_DRM_ [DONE]

    * Glenn Adams asks W3C to remain neutral on the fact that DRM should be
      used or not. [19]


    * Tab Atkins argued that commercial video can be done without DRM and a example of it are Indie producers on youtube and the comedian Louis CK who make livings without DRM. [4]

 He also argues for the lack
of interoperability. BTW Thinking on DRM free commercial systems, a good way to
earn money can be inserting a ad in the video and more viewing (+ pirating) of
the video just means more ad revenue, the producers only need to have a method
to estimate their viewership to estimate the ad fee. Tab also talked about the
comedian Louis CK who made a million dollar selling videos in DRM-free format.


    * Tab Atkins [2] points out that the sole purpose of EME is DRM, he said
      DRM is "technically impossible and practically useless, imposing
unnecessary costs on legitimate users while doing nothing whatsoever to
actually stop copyright infringement." He is disappointed that his employer,
Google co-edits the proposal.


    * Mark Watson counters the cost to the users because of DRM with the cost
      of fragmentation. [6]


        * The aim of DRM is to act like a speed bump for copyright infriengment
          and in that way it is effective. (Question: Is this speed bump
effective) [3]


        * Millions of $$ of Engineering effort will go waste if they don't
          standarize DRM on the web. [3]


Henri Sivonen argues that failing to describe the specs of the protection
system EME doesn't provide benefits of interoperability and level playing field
for competition. Only lowering the R&D cost for proprietary DRM systems
shouldn't be a good enough reason for W3C to work on EME.


Glenn argues the users of web include both the content producers and the content consumers, protecting users should mean protecting the interests of both, also W3C shouldn't be biased against the users who are willing to pay for protected content.

against users who are willing to pay for DRMed content. He points that
EME has to take care of the constrains imposed by licensing terms of content
providers, which might prevent usage of EME with open source implementation [21].






_John Foliot's rant_


    * John Foliot argues that they need to strip way the philosophical
      arguments about EME and think about from a purely technical point of
view and then he justifies EME by saying it what the economy wants. Failing to
realize that "This is what economy wants" is not a technical argument,
neither he justifies that W3C should do what CEOs want them to do.



    * Henri Sivonen counters John's post by saying that standard setters need
      to make value judgement all the time and arguing "Don't use it if you
don't like it", is an extremely naive solution and doesn't tackle the issue of
lack of level playing field [11].

_Adversary Controversy_

    * There was small misunderstanding where Henri says that HTML5 already
      supports cases where user is not treated as an adversary, which Clark
and Glenn found derogatory [28] [29] [30]. To which Henri later clarifies that
Henri probably meant the term "adversary" in the technical context of
cryptography [39]. (Exchanges of Clarke and Tab [42] [43], Andreas supports the
nontechnical usage of term adversary in context of DRM and points out to RMS [45])

_Comparison with Plugin based system_

* To which Boris's response was that any new browser with correct implementation of NPAPI can work with flash so the answer really depends on the specifics of the Content Decryption Modules. He also questions the assumption that browser developer will have greater control and more options in case of EME [51]


Mark Watson argues that there are practical difficulties for new browser with flash even if they have an implementation of NPAPI according to the specification, he says CDMs provide more control to browsers because they are smaller and have much less functionality. [52]

According to Boris this is
different because there no legal difficulties, where as implementing a CDM
might lead to trouble with DMCA. [53] But Mark feel the situation is no worse
both in legal and technical because CDM's will only be a subset of the current
plugins. [57] EME makes the binary 'blobs' of plugin's smaller with a
well-defined and highly-constrained function and it should be an improvement.
"Making them (blobs) go away altogether might be a bigger improvement by some
measures but by others (range of content available) might be quite negative."
[67]

    * Boris points out and important issue that if W3C don't define the API for
      CDM interaction,  "One of the requirements for browser developers (either
on their own or imposed by the CDM providers) might well be "make it illegal
for any other browser developer to attempt to reverse-engineer the API we're
using"" . He also says that if the discussion is about supporting walled
gardens then it shouldn't happen here at W3C. [68]


_CP in existing HTML5_ [DONE]

    * David Singer calls it a myth that HTML5 cannot play protected content.
      [44]

    * David's responds to the question [48] encrypted video can be played
      through the existing <video> tags where the content file says its
content-ID and is marked as protected, someone who has the DRM to play the
content installed and has brought the keys to play it can watch the video and

Mark Watson responds by arguing that many browsers have entire media pipeline
in the browsers code and hence it cannot use the content protection facilities
available on the OS, he also claims that it is not a myth that protected
content cannot be run in HTML5 because there isn't a standard way to do it.
[49] And then David responds again (will do the summarization later) [56].


    * Earlier Henri had asked if they are OK with revealing unscrambled content to the user only hiding it from the third parties then HTTPS should be enough to which Mark Watson responded that the content providers might wish to hide content when it is stored in servers and that http service with CDNs are cheaper than https and is operationally simpler. [61]

_Need for Trusted Computing_

* Henri Sivonen In the next email says that the lack of interoperability of
  `<video>` and `<audio>` shouldn't be taken as role model also. He countered
Pritchard's example about Trusted computing by pointing out in his example the
"Evil Maid" was an adversary but in EME the adversary is the user, [11]

* Mark Watson responds by arguing that many browsers have entire media pipeline in the browsers code and hence it cannot use the content protection facilities available on the OS, he also claims that it is not a myth that protected content cannot be run in HTML5 because there isn't a standard way to do it.


_Privacy_ [DONE]

* Henry also says that it'll be laughable to say EME protects user's privacy. [11]

* In context of browser extensions Charles once argued that EME can help
  protect privacy of users by ensuring that the content consumed by users
doesn't get intercepted by third parties. He asks the group to give a full
analysis to the proposal so that it can be used for the benefit of privacy
[36].

_Accessebility_ [DONE]

    * Ian Hickson draws a satire of John's "Don't use it if you don't like it" argument about DRM, argues that EME intentionally makes content inaccessible hence it is unethical [17]. Glenn Adams calls Ian's argument non sense and says DRM/Content Protection has nothing to do with impaired users[18].

    * Supporting Ian, Benjamin Hawkes-Lewis posts three weblinks describing various accessibility hurdles that come up due to DRM [37]. To which Glenn Adams said that DRM/CP doesn't intentionally discriminates against accessibility features. He then points out that HTML5 offer workarounds in case where accessibility features are missing. [38]


    * Henri said "Even if one accepted the notion that DRM discriminates equally against non-accessibility and accessibility features, discriminating against accessibility features at all deserves special attention", DRM foils the exceptions provided by copyright law for accessibility purposes, an example can be case where the DRM proprietor places a contractual requirements on implementors prohibiting sending the audio to a speech recognition system for generating captions on the fly on the client side.

[40]

    * Mark Vickers argues that EME improves upon many of the accessibility issues in plugin systems used to play protected content by providing standard ways to add accessibility features. [46]

_CDM Interoperability_ [DONE]


 Main four weaknesses he pointed out were [65]
    * Kornel stated the EME spec does very little to provide easy and interoperable content protection. Specifically it leaves the interaction between CDM and the browser undefined, so each CDM provider will have to cooperate with every single browser vendor it's willing to support, and browser vendors may need to implement proprietary CDM APIs several times.

        2. Very few companies have enough market power to establish a new DRM approved by "Hollywood", so it's quite possible that the current plugin problem will just morph into an identical CDM problem

        3. unified server-side API is much important to enable diversity of protection systems, but it's out of scope of the spec.

    * Mark Watson says "We are not proposing to standardize any Content
      Decryption Module except clearkey, just as HTML does not mandate any
video codec and for similar reasons. So the specification as proposed can be
implemented in Open Source just as well as the rest of the Media Element." [22]

    * Charles Pritchard makes an interesting observation that `<video>` and
      `<audio>` tags are intentionally about arbitary codecs and don't push
vendors for interoperability. He gave an example where trusted computing makes
sense. He also argues that an encrypted stream is no better than a arbitrary
codec but W3C should implement trusted computing anyway to protect the privacy
of people. [8]

    * Kornel ask if there will be standard way for browsers to communicate with
      CDMs [59] to which Mark Watson says "there could be if people would like
there to be. On the other hand there is no such standardized API for plugins or
media codecs." [60] Vickers, Mark supports having a standard API saying it will
be useful [62]. Kornel says without an API the CDM side is all hypothetical
[63] and Glenn say though having it will be a reasonable task but a not a task
for W3C [64].

_Implementation in FOSS browsers_ [DONE]

    * Tab Atkins said that DRM is based on encryption, and all good encryption
      is open-sourced. But it requires the consumer's software to have the
decryption key without giving the consumer the key. This is obviously
impossible in open-source software. [4]

    * Glenn Adams argues that Firefox can use a OS API like mechanism of
      implement EME where they don't have to reveal the source code the
decryption module. [73]

    * Mark Watson argued that EME is not an issue with Firefox from specification point of view because they don't specify the content Decryption Module. [3] Also a Content Decryption Module implementing the 'clearkey' keysystem can be implemented as Open Source. [22]


    * Henri Sivonen says a more interesting to ask is if Netflix et al. are
      willing to use open source implementations of CDMs to provide their
content [24].



_General Support and Opposition to EME proposal_ [DONE]

    * Boris Zbarsky said that EME is bad for the web if it requires new browsers to coordinate with companies while coming up. [16]

    * Andreas Kuckartz opposed the proposal if it cannot be implemented by
      Open Source Software. [20]

    * Ian Hickson called the proposal unethical. [72]

    * Eric Carlson said EME proposal is workable. [69]

    * Carr, Wayne supports the proposal without justification. [10]

    * Bob Lund supports the proposal by saying it is a good first step to
      support problems of content providers and device manufacturers. [13]

    * Mark Vickers, representing Comcast, strongly supported the EME proposal
        claiming that EME will go a long way towards moving most of the
    will be a vital step enabling commerce and communications through web browser. [71]

    * Glenn Adams supports EME on the behalf of Cox Communications [19]





_Unclassified_


    * John C. Vernaleo replies to Glenn saying that he'll like to keep
      technical and legal issue seperate but that might mean keeping OSS out
[25] to which Glenn replies that this is over generalization and not all
licenses block OSS [26], to which John Vernaleo says that the specifics of the
restrictive policies are not important, what he is concerned about is building
a system where OSS cannot participate, he also warns that it is dangerous to
build mechanisms supporting some parties without thinking about their
consequences [27].


    * Kornel stated the EME spec does very little to provide easy and interoperable
      content protection. Main four weaknesses he pointed out were [65]
        1. The spec leaves interaction between CDM and the browser undefined, so  each
        CDM provider will have to cooperate with every single browser vendor it's
        willing to support, and browser vendors may need to implement proprietary CDM
        APIs several times.

        2. Very few companies have enough market power to establish a new DRM approved
        by "Hollywood", so it's quite possible that the current plugin problem will
        just morph into an identical CDM problem

        3. unified server-side API is much important to enable diversity of protection
        systems, but it's out of scope of the spec.

        4. The spec does not help implementors create secure implementations. It needs
        to define chain of trust and how it is established/verified — otherwise
        each CDM/browser/OS combination may have different, variable and unspecified,
        levels of protection.

        Mark Watson agreed with most of Kornel's concerns and said it is the
        first draft and things will be improved upon. [66]



     Vickers, Mark further asked following questions to David and EME editors. [47]
        ```
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
        ```


* Adrian Bateman announced at the public-html mailing list that
  they have been working to provide an API to play encrypted media in HTML 5
[1]. One of the mentioned reason was that many content providers and
application developers have said they can't use `<audio>` and `<video>` because
HTML lacks robust content protection.

    * Glenn Adams objected to linking EME to issue 171 which talked about
      adding ways to pass arbitary parameters to audio and video tags. Glenn
rather proposes to have generic exchange mechanism which are not specifically
related to encrypted content. He criticizes not supporting params.
    * A lot of talk there after is about comparison with `<object>` in a purely
      techinical sense.

    * Chris Pearce questions the possibility of implementing content protection
      in a FOSS browser. [70]

    * Specifically replying to Henri, Mark Watson argues that EME is not about
      adding DRM to the web but about improving existing plugin based system.
[15]


    * Glenn Adams calls for keeping licensing technical issues separate. [23]

    * Boris Zbarsky ... (talks about lack of level playing field)[32]

    * Incompressible exchange between Charles and Kornel [33] [34]

[35]

    * To issue of creating unlevelled field for browser's Mark Watson responds that
      the same situation exists in plugin based enviornments and EME improves
upon that. [50]



    * Purely technical blabber [54] [55] [58] [74]



