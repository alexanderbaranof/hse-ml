# Collaboration I

## Communications channels

### E-mail

Exercise: Write a simple RFC561-compliant e-mail.

```
From: alexanderbaranof@gmail.com 
To: alexanderbaranof@gmail.com
Date: 19 JUN 2021 2016-MSK 
Subject: Exercise
Hi!
```

Exercise: Send yourself an e-mail with non-ASCII characters. (E.g., "привет!") Download the raw message and open with a text editor. What are the contents? How is the message encoded, and where is the encoding specified? (Sometimes you need to select "view message source" or "view original message" to do this.)

I send text "Привет" and message look like this:
```
0J/RgNC40LLQtdGCDQo=
--0000000000000c096b05c5219d79

Content-Type: text/html; charset="UTF-8"
Content-Transfer-Encoding: base64se64
```
Exercise: How are attachments handled? Refer to the Wikipedia article on MIME; send yourself an e-mail with a (very small!) attachment, and download the raw e-mail message and open with a text editor. What are the contents? Show and explain each MIME part. Can you recover the attachment from the raw message?

```
MIME-Version: 1.0 - info about MIME formatting
Date: Sat, 19 Jun 2021 20:21:30 +0300
Message-ID: <CAG_Akt+PbDYwMn+PadoD+T511dE=742kNmEquj6-agshWzS=uQ@mail.gmail.com>
Subject: 
From: Alexander Baranov <alexanderbaranof@gmail.com>
To: alexanderbaranof@gmail.com
Content-Type: multipart/mixed; boundary="000000000000d4a56305c521ab7f"

--000000000000d4a56305c521ab7f
Content-Type: multipart/alternative; boundary="000000000000d4a56005c521ab7d"

--000000000000d4a56005c521ab7d
Content-Type: text/plain; charset="UTF-8" - 



--000000000000d4a56005c521ab7d
Content-Type: text/html; charset="UTF-8"

<div dir="ltr"><br></div>

--000000000000d4a56005c521ab7d--
--000000000000d4a56305c521ab7f
Content-Type: application/octet-stream; name=testfile - File type
Content-Disposition: attachment; filename=testfile
Content-Transfer-Encoding: base64
X-Attachment-Id: f_kq412l8z0
Content-ID: <f_kq412l8z0>


--000000000000d4a56305c521ab7f--
```

Yes, if necessary, we can restore the sent file because it is stored in the text of the message


### IRC

Exercise: Install an IRC client, log in to freenode.net, join #apertium and write a message "begiak: tell nlhowell hi". It will instruct the bot managing #apertium to forward me the message next time it sees me.

```
* Now talking on #apertium
<alexbarhse> begiak: tell nlhowell hi
```

Exercise: Find a piece of software that you use which has an IRC channel for support. Ask a question there about the software. Include your conversation, and a brief description of your experiences.

I use Pidgin client and connect to #pidgin suuport via https://web.libera.chat/#pidgin . It's simple. 

### Matrix

Exercise: together with a friend, try out the Riot.im web client. How does it compare to IRC? To Telegram?

My feeling is that it's something between Telegram and IRC.  Interesting description of the protocol used. 

## Quality control

### Bug reports

Exercise: Both Python and the Linux kernel have considered in the past moving from bugzilla- and e-mail-based systems to forges. Read both articles, and summarise the advantages and disadvantages of forge-based systems and e-mail, and the results of each.

The advantage of the forge system is that it is easier for people to start using it. Most of the time they are clearer and more understandable than email. However, such systems are not suitable for large projects and very often prevent people from debugging code locally or discussing it conveniently.

Mail, on the other hand, seems to be a simple system because it has been in use for a very long time and can be integrated relatively easily. However, it is difficult for newcomers to understand all the features of such a patch acceptance system from the beginning. Also, project managers can't conveniently control the work on an active project.

### Continuous integration

Exercise: Suppose your project is not software. What kinds of quality control tests might you implement? Give examples for written articles, web sites, musical compositions, and graphics.

For text data, it is easy to implement word error checking. You can also control some turns of speech. And for the final validation you can use an editor.

For web sites, it's worth using customer reviews, as well as tracking the business performance of the site. If they change for the worse, it means that there are some mistakes.

For music tracks, it is important that the volume of all tracks is set to the same level. I think this can be done automatically. Also the editor can tinker with the finished songs.

But for charts, visualization is important, and there is no way to automate the process. That's why there is a need for validation by an expert

### Documentation

Exercise: install and run pandoc. (The dependencies are hefty.)

```
pandoc 2.11.4
Compiled with pandoc-types 1.22, texmath 0.12.1, skylighting 0.10.2,
citeproc 0.3.0.5, ipynb 0.1.0.1
User data directory: /Users/alexanderbaranof/.local/share/pandoc or /Users/alexanderbaranof/.pandoc
Copyright (C) 2006-2021 John MacFarlane. Web:  https://pandoc.org
This is free software; see the source for copying conditions. There is no
warranty, not even for merchantability or fitness for a particular purpose.
```

Use ctrl+D comand for generate output
```
pandoc --mathml
$x^2 = y^2+z^2$
<p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>x</mi><mn>2</mn></msup><mo>=</mo><msup><mi>y</mi><mn>2</mn></msup><mo>+</mo><msup><mi>z</mi><mn>2</mn></msup></mrow><annotation encoding="application/x-tex">x^2=y^2+z^2</annotation></semantics></math></p>
```