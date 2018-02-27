# Feb 2012

* 21 Feb 2012:

Mark Watson "I'm just trying to make it easy for customers to watch TV shows
and movies online, legally, on as many devices and in as convenient a way as
possible. It's often argued that this is where other content industries went
wrong: by not doing this. HTML can help with that." [75]

* Robert "But in practice, HTML <video> relies on the availability of standard
  codecs and containers whose behavior is documented/standardized (albeit
patent-encumbered in many cases). Likewise, it is important to somewhere
specify the Content Decryption Modules." [76]

* Charles Pitchard "I've been addressing obfuscation, given the licensing
  arrangement that the recording industry has given to both audio feeds and
lyrics, and theorizing about how that would look with video. It does fall under
the user is trusted case, but it's got that little quirk where the average user
is unable to manipulate the stream." [77]

* Kornel
"""
I think performance issue can be avoided in two ways:

1. Use JavaScript only to generate key for stream encrypted using a
standard cipher. Instead of decrypting many MB of the stream, JS would
only need to decrypt 32 bytes holding the key.

2. Provide JavaScript with access to natively-implemented helper functions
for typical tasks in cryptography (SIMD for XORs and shifts of arrays,
operations on polynomials, standard hashes, etc.). JavaScript only acting
as a "glue" between many native functions may have orders of magnitude
lower overhead.


Although to be honest I don't see the point of tying to do content
protection in JS. Such well-specified interoperable environment will be
ineffective for user-is-adversary use case. For secure transport we have
HTTPS already.

The remaining case — secure storage with untrusted parties — should rather
have a simple, native solution. Special UI for giving browser decryption
password in a way that makes it clear that password doesn't go to a remote
site is important, and JS can't do that by design.

""" [78]

* Encrypting content stored on untrusted CDNs [79] [80] [81] [82] [83] [84] [88]

* Mark Watson "Yes, I understand this does not make any sense to you. But it does to others. It's a pre-requisite for services like Netflix to use HTML5 instead of plugins. This list is not the place to argue the ethics of that. W3C needs to decide whether to work on making that a possibility, or whether HTML5 is simply not going to be a suitable technology for our segment of the industry, which would be a shame." [84] On this Charles said "$20k of work on WebKit would get you what you want. And you don't even have to spend it-- looks like there's enough industry support that someone else will." [85]

* Mark "Please remember that there are many more implementations of the web platform than the desktop browsers: we are especially concerned with TVs, Set Top Boxes, Blu-ray players and other CE devices. There is a real danger that a variety of standards bodies around the world define their own modifications to HTML for these features. Such fragmentation is in no-ones interest and so we would very much prefer to see W3C addressing this." [86]

* Clarke """
Indeed, Mark's point is the crux of the issue. There are several
participants in the Web & TV IG and in this group who have content
protection requirements and many of them have spoken up. These
participants hope to use HTML5 because they believe it can provide a
better solution than what is currently available. I am hopeful that we can
work together to find a solution that both meets the requirements of those
who need (at least currently) content protection to provide their service
and those who are charged with the stewardship of HTML.
""" [87]

* Implementation outside W3C [91]


Henri:

CDMs are qualitatively different from codecs, because:

 1) So far, the list of CDMs isn't down to a very small known number (3 in the case of codecs at the moment, though H.265 or Daala could increase the number)

 2) In addition to being encumbered by patents, CDMs could be encumbered by trade secrets. (If there aren't secret algorithms, there might be secrets keys that an implementation needs to incorporate in order to be compatible.)

 3) In addition to being encumbered by patents, it seems (IANAL, though) that being compatible with a CDM without permission might run afoul with anti-circumvention laws.

As for plug-ins, there's one that's still a big deal: Flash Player. If a new platform doesn't support Flash, people notice. If a new platform doesn't support Java or Silverlight or whatever long-tail plug-in, that's pretty much OK as far as market acceptance goes. Plug-ins other than Flash matter for competitiveness only relative to other browsers on an OS that already has other browsers that support Java, Silverlight, etc.


## Henri's Proposal

This feature adds a decryption layer to the browser's HTTP stack and an API for initializing decryption keys from a different origin. Also, the Same Origin Policy is extended to block obvious access to decrypted data from JavaScript.

The browser maintains a key storage that holds tuple of key, sha1(key), origin of key, list of authorized origins and time to live. There's a JavaScript API navigator.addKey(keyUrl, arrayOfAuthorizedOrigins, timeToLiveSeconds, doneCallback). keyUrl is a URL of the same origin as the caller of the API. The payload retrieved from the URL is key material to be added to the key storage. arrayOfAuthorizedOrigins is an array of origins serialized as strings that are authorized to serve content to be decrypted using the key. (This is a privacy mechinism against other origins probing the key store in case an untrusted CDN has leaked key hashes. More on hashes later.) timeToLiveSeconds is the number of seconds after which the browser purges this keystore entry. doneCallback is a JavaScript function that the browser calls after it has retrieved and processed keyUrl. Upon success, a single argument true is passed. Upon failure, a single argument false is passed. (Note: The key material is not exposed to JS.) The browser generates an id for the key by hashing the key material with SHA-1. Origin of key is set to the origin of the caller of the API which has to be the same as the origin of keyUrl.

When an HTTP response includes the response header Content-Encoding: AES256, the processing happens as follows (if any step fails, treat as like other HTTP errors):

The HTTP implementation gets the value of another response header called Key-SHA1 and base64-decodes it. Then, the browser's key storage is searched for a key whose sha1(key) entry matches this value and whose list of authorized origins containst the origin of the HTTP response and decrypts the response payload using AES256 using the located key as the decryption key. The decrypted payload is exposed to the other parts of the browser as having origin E(origin of key).


Origins of the type E(Origin) have the following properties:

 * A resource of origin E(Origin) can be included as embedded content (<img>, <video>, <audio>) in (and only in) a document whose origin is Origin.

 * For the purpose of JavaScript access to the data of the resource (be it raw bytes or pixel data), E(Origin) is considered to be different-origin with every origin including the origin(s) representing the authority of browser extensions.

 * Browsers disable the "Save As..." context menu for embedded content whose origin is of the form E(Origin)

When the layer above the HTTP layer request the HTTP stack to perform a range request on a Content-Encoding: AES256 resource, the HTTP stack must extend the range such that the range consists of full AES256 blocks in both directions. (The lack of block chaining is deliberate so that seeking is possible.)

Mark's response:

If the keys are available to the browser code, then this probably wouldn't work for most of our content, since a browser could be trivially modified to release the keys.

If the keys are not exposed to the browser code (i.e. if the mechanism above were implemented within something like the CDM we propose and this met our security requirements) then another issue is that you (presumably) rely on standard HTTP authentication to authenticate the user.

Presently we use our own application protocol within which we have our own authentication mechanisms. We provided details of this in the discussion on the proposed web cryptography working group [1] . This avoids the need to stand up front-end servers for each different key delivery protocol (of which your proposal would be just one).

This is one reason why we propose to proxy the key delivery messages through the Javascript layer.


Performing the decryption at the HTTP layer has the following problems:
- HTTP servers have to support the additional headers, which means CDN changes are necessary. Even trivial CDN changes take time to roll out across the world and CDNs generally want some compensation. Anything which restricts our choice of CDNs increases our costs and reduces user quality of experience (due to reduced diversity). So there's value to us if the solution works with existing HTTP services.
- existing standard encryption mechanisms (for example common encryption for mp4 files) cannot be used, meaning that existing files would have to be re-encrypted and also that separate copies of the media would be needed for browsers based on this system and devices following the existing standards. Requiring separate copies has both storage costs and cache efficiency costs (which impact quality of experience).

It's possible the second point could be addressed by making the HTTP stack file-format-aware, so that it could apply the appropriate kind of decryption. But that seems architecturally problematic.


I'm not an expert on these kind of browser security issues, but the above sounds quite neat to me. It could also be considered as a way to handle the output of CDMs in our proposal, for the case where this output (in whatever form) goes back to the browser code.


https://lists.w3.org/Archives/Public/public-html/2012Mar/0015.html



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

[57]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0434.html

[58]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0435.html

[59]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0436.html

[60]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0437.html

[61]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0438.html

[62]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0439.html

[63]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0440.html

[64]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0442.html

[65]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0444.html

[66]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0449.html

[67]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0446.html

[68]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0448.html

[69]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0314.html

[70]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0303.html

[71]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0391.html

[72]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0274.html

[73]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0322.html

[74]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0451.html

[75]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0459.html

[76]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0458.html

[77]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0476.html

[78]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0484.html

[79]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0487.html

[80]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0488.html

[81]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0489.html

[82]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0491.html

[83]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0492.html

[84]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0493.html

[85]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0494.html

[86]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0495.html

[87]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0496.html

[88]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0497.html

[88]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0498.html

[88]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0499.html

[89]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0500.html

[90]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0501.html

[91]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0502.html

[92]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0503.html

[93]: https://lists.w3.org/Archives/Public/public-html/2012Feb/0504.html


# Github Notes

* 17th May 2016: Paul Cotton announces that ensuring CDM level
  interoperability is out of scope of the working group's charter [a].

[a]: https://github.com/w3c/encrypted-media/issues/192#issuecomment-219805449


# People

* Glenn Adams works for Cox Communications
* Bob Lund works for Cable Labs
* Mark Watson works for Netflix
* Mark Vickers works for Comcast.
* Adrian Bateman works for Microsoft.
* Clark Stevens works for CableLabs


* Eric Carlson works for Apple.
* Carr, Wayne works for Intel
* Leonard Rosenthol works for Adobe
* David Dowin works for Google


* Chris Pearce works for Mozilla
* Henri Sivonen works for Mozilla
* Robert O'Callahan used to work with Mozilla till March 2016, he was rr
  (record and replay) developer.
* David Baron works for Mozilla
* Boris Zbarsky works for Mozilla and a quick search suggests he an insider of
  W3C.


* Silvia Pfeiffer Works at NICTA

* Tab Atkins works for Google as a web standard's hacker http://www.xanthir.com
* Ian Hickson: He works for Google and is a part of CSS working group.
* John C. Vernaleo worked at Conformal System at the time of discussion and
  security and open source firm. http://www.netpurgatory.com/web_stuff/media/cv_jcvernaleo.pdf
* Andreas Kuckartz is a german software developer.
(ping.de is the internet provider)
* Charles Pritchard works for Jumis, which is a web applications and services
  provider

* Kornel Lesiński works at Financial Times

* Benjamin Hawkes-Lewis(bhawkeslewis@googlemail.com)'s isn't apparent from
  simple web search.

* David Singer works for Multimedia and Software Standards, Apple. He has
  written on identity management and privacy principles in W3C. https://www.w3.org/2011/track-privacy/papers/Apple.pdf https://www.w3.org/2011/identity-ws/papers/idbrowser2011_submission_51.pdf

* Smylers is a programmer from Leeds, UK





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

* John C. Vernaleo: Opposed to W3C supporting DRM.

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
