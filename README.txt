

SMS (and CBS) will likely live for another several decades.
The "competition" is either split (and not built into the
telecom systems, they are via separate apps) or dead in the
water (the supposed replacement is simply not available, and
thereby not used).

But SMS (and CBS) has not had a proper update for decades, and is
in a rather deplorable state; hardly updated since the 1990-ies
(apart from some failed 'national language alphabets').

So I have made a number of updates that together can make SMS
viable for another at least a few decades. Would be a pity to
leave it in a deplorable state for the rest of its likely lifetime.

The changes are to the "alphabets" 3GPP standard. Other are left
unchanged (other than deprecating the styling specified in the
SMS standard) in this proposal (And drafts for sections 4 and 5
should probably not be continued; editorial not worth the effort.)

1. To improve the 7-bit alphabets: deprecate the ill-designed existing
   non-default alphabets, add well-designed "national" language alphabets,
   indeed more of them than there was. Recommend 0x10 for human-visible
   SMS messages in all Latin-script European languages, deprecate the
   default 7-bit for human visible messages (SMS and CBS). "Telecom
   internal" messages ('special' SMS (like phone configuration from
   operator), USSD (like *#-codes from phone), and more) (normally not
   visible for human readers) should still use the default 7-bit alphabet.
   These 7-bit alphabets can also be the basis (conversion specified
   in the proposal) for 8-bit alphabets. One should also allow for UTF-8,
   which is popular in most (all?) 'competing' messaging systems.
   Note though, that while these '8-bit alphabets' would be specified
   for 3GPP messaging systems, they may be usable also for other
   messaging systems, though they are all *incompatible* with XML, HTML,
   and text file storage.
      Having these "alphabets" allow for shorter (and hence cheaper) messages
   counting in bytes, and counting in number of submessages for a message,
   not forcing UCS2 (UTF-16) encoding for lots of messages. SMS still has
   a cost per submessages for many operators; so it may be up to half as
   many submessages per message for long messages (less to no difference
   for really short messages, though). The additional 7-bit (8-bit) alphabets
   cannot be used for CBS since CBS does not have any "National Language
   Identifier" in the protocol. (I think the same might go for USSD.)

2. "UCS2": a) Refer instead to UTF-16 (commonly used), which is an extenstion
   of UCS2 (a predecessor of UTF-16, limited to BMP, not in common use now).
   b) Add mappings (mainly to REPLACEMENT CHARACTER) for characters that
   are unsuitable for use in SMS (or CBS) messages. Such as HT (map to SP),
   most "control" characters, private use characters, bidi controls and more.

3. There is a mechanism specified for SMS for (limited) styling of text.
   However, that mechanism is 1) ill-defined, and 2) implemented by no-one.
   Replace that with a mechanism that is well-tested over decades and
   suits SMS/CBS well (no XML or HTML like markup, nor 'markdown', all of
   which are highly unsuitable for SMS/CBS). This exact mechanism is used
   in about all terminal emulators. Also Teletext used (it's mostly obsolete)
   a similar mechanism. So nothing new-fangled and untested, it is well tried
   and tested since long, and is well compatible with SMS. (No, jumping letters,
   though (cmp. iMessage...).) This should be accomanied by deprecating the
   (totally unimplemented) styling specified in the SMS standard.

4. Add a simple table formatting method (again using a method compatible with
   SMS/CBS). No fancy tables, simplest possible. I think that would be quite
   useful in some SMS messages, for instance for itemized prices, and other
   (short) lists that stand out from the running text.

5. The Unicode line breaking algorithm (finding break points) is a bit flawed
   as it is. Correction to the most egregious errors are included in this
   proposal. In the "medium term" these corrections should be incorporated
   in the Unicode line breaking algorithm.

6. Also the Unicode bidi algorithm (mainly for the Arabic and Hebrew scripts)
   has some shortcomings. Unicode has a few nestable bidi control characters
   that can be used to 'correct' the situation. However, they are 1) very hard
   to use, so 2) next to no-one uses them, and 3) they can be used to cause
   great confusion, even security issues. Therefore, they must not be used
   in SMS or CBS messages; they are mapped away in the UCS mapping. Instead,
   the Unicode bidi algorithm is modified so that a) these controls are not
   needed, and b) the outcome reordering is as good as one can get it and it
   is not confusing nor just bonkers. In the "long term" these corrections
   should be incorporated in the Unicode bidi algorithm (except that bidi controls
   would still be available, despite security issues that exclude them from SMS).

This is "just" character encoding (and text presentation) improvements.
It does not add functionality like end-to-end encryption, file transfer,
or image/video transfer, ... So in that regard it is quite conservative,
but still valuable for the next few decades of SMS (and CBS) use.

