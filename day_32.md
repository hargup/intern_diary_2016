Hi,
Thursday 23 June 2016

So Yesterday I read the details of how video works on web [1], and how does
High Definition Content Protection (HDCP) work [2]. Video is kinda complicated,
the extensions of a video file mp4 and avi, represents container format, who
acts much like zip files. They contain multiple files representing sound, video
and metadata. The video then itself can be encoding using lots of different
techniques/formats known codecs. The dive into HTML5 book explained things very
well from the perspective of the developer who needs to add video to his
website but didn't go into details of how browsers implement video support. I
found [Chromium Design
Documents](https://www.chromium.org/developers/design-documents/video) which
described some of the details but couldn't find anything from Firefox. [Asking
on StackOverflow](stackoverflow.com/questions/37966165/what-are-the-implementation-details-of-video-support-in-firefox)
was of no help either, but it is clear that browsers *can* make use decoding
capabilities of the OS. Anyway today I'm gonna focus on other low hanging
fruits, like WIGI for Indic languages.

[1]: http://diveintohtml5.info/video.html

[2]: https://web.archive.org/web/20080920191718/http://www.digital-cp.com/files/documents/04A897FD-FEF1-0EEE-CDBB649127F79525/HDCP_deciphered_070808.pdf
