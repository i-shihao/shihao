# johan-lieber.github.io

LFX Kernel Mentorship Journey Blog

I have been tinkering with Linux operating system since I bought my first
laptop ever since then I have been spending consistent time initially trying
to understand it .I liked what Linux provided and wanted to understand,
contribute and join its community however never really went into it neither
contributed to it .As I was exploring stuffs related to Linux I came across
LFX mentorship which was hosting a Linux bug fixing program in September.At
first I never thought I would be able to get in as a candidate but despite
that I applied and fortunately i got selected .After the selection we were
initially giving some tasks to complete before December and one the most
difficult task among them were getting five or ten accepted patches to
Linux kernel. I later realized that submitting patches to Linux kernel was
little hard and had to be done early in the program to complete the graduation .

Patch submission Journey

My first patch was in the USB subsystem because I had prior knowledge in this
subsystem I thought it is the perfect place to begin with. I knew there was a
“FIXME” statement in the transport.c file stating that It needed some protocol
translation so with some prior knowledge I had I began to make a proper protocol
translation for it and submitted a patch to its specific maintainers among them
was Greg Kroah-Hartman and Alan stern . My first patch got rejected by many times
probably for seven or eight times because of patch submission errors it got so
worse that Greg said to me that “You are sending patches on top of patches none
of them will work. Please relax take a break and come back in a day or so “.
It is usually good to submit one patch per day or resend versions on the next
day but since i had submitted several patches in a day Greg seemed so annoyed
but i liked that he was annoyed.

After some review and feedback on the patch i eventually got rejected and Alan
stern said that it is unnecessary but even if it got rejected it was such an
important patch for me since it required understanding of USB subsystem and
file related to like usb.c , protocol.c and transport.c however I also learned
some valuable lessons along with the rejection some important lesson were like
how to submit a good patch . I also learned how to submit a good patch by reading
documentations in the Linux tree under /Documentation/process which were good
help in regard to patch submission.

Chanding old Apis

With the rejection of first patch I quickly began searching of new ways to find
bugs in hope for fixing them and submitting a patch and during this groping I
came across this website which had many “TODO” lists to do and one of them was
API changes . There were many old functions that need to be replaced with newer
functions and I began to replace old deprecated APIs with new APIs and send
patches to each subsystem maintainers and without much resend this time several
patches were accepted and with this my first patch got accepted into the Linux
Kernel .Although it was minute changes but eventually got accepted by maintainers.

The website's wiki has not been updated since 2017 so the bugs listed there were
already been fixed or no new api changes were listed on it so I needed to move on
and search new resources to find bugs and in this regard i found this website
which is such a good resource related to Linux. It also helped me a lot not only
in searching for bugs but to understand functions ,subsystem , files and rest .It
also lists those old deprecated apis too which needs replacement and among them
that needed replacement was in the showfs functions that used bare snprintf()
functions which could to be replaced with sysfs_emit(). I replaced those showfs
functions that used snprintf() with sysfs_emit() and submitted a patch and
fortunately it got accpeted but one thing i needed to remember that only in the
new implementation sysfs_emit() was asked to replace not in the old showfs

Syzbot

Fixing apis changes were not hard .It did not required much care and work so the
urge was there to do something more difficult .One of the best websites that
lists bugs to Linux kernel was Syzbot .It always have a open section which lists
bugs that are found in the Linux subsystem and most of them needs fixing .It is
usually good to begin with beginner friendly bugs like “KASAN” bugs which are
easy in terms of understanding kernel bugs which are usually hard .These type
of bugs might have its reproducers with them but it depends .Most of the open
bugs listed on syzbot do not have any reproducers with them so after fixing
some apis changes I moved to syzbot bugs and began to understand and carefully
reproduced them but not all reproducers work sometimes in my case I tested two
syzbot bugs and both of them failed to reproduce the same crash. This meant
that even if syzbot bug has a reproducers it does not mean that It will
definitely reproduce the same crash again along with the same configurations.
In such cases it is better to make the reproducers by ourselves or leave the
bugs as it is.

Another thing is before we try to make a fix we need to understand its scope
and carefully do the fix because fixing it might break somethings else .
Although I attempted to fix two of syzbot bugs however both of them failed to
reproduce the same crash on system I tried but due to short on time I left it
because I had to make several patches to mainline Linux I could not spent more
time on syzbot since it needs careful observation .If I stayed I would not be
able to make even five patches so I needed to make a choice here . Below is
picture of syzbot interface.

staging drivers

/drivers/staging subsystem is such good place for beginners I wish I knew it
earlier. driver/staging area is a place where there is a lot of need for fixes
improvements and changes .When I heard about it I quickly went to explore it
and as expected there were many directories listed there .In most of the
directories there were “TODO” files. These files were indicating that the
driver needed fixes and improvements and in hope of someone do it they were
listed there and they were good for beginners to get their hands dirty.
I explored many directories there and saw many to do lists however because
I was short on time I also eventually left this directory for later exploration
however this was such a good place to begin with since it is where most fixes
are needed.

Tools and scripts

Besides syzbot and /drivers/staging subsystem I also utilized many static
analysis tools including Coccinelle, smatch and checkpatch.pl, to find
bugs in the Linux kernel source tree. These tools were helpful in both
understanding and finding bugs however not all bugs found by coccinelle
and smatch were bugs but rather a false positive and most of the bugs
found by them required significant investigation .Checkpatch.pl was more
straight forward in terms of finding coding style and compliance issues.
Here are some commands I used mostly during the mentorship

      make coccicheck MODE=report M=drive
      r
     smatch -p=kernel --file-output drivers/usb/core/*.c

     find . -name "*.c" -exec \

      ~/linux-source/linux-git/scripts/checkpatch.pl --strict -f {} \;


Refelection on my Mentors

Although I have not attended much meetings but those meetings which I attended
where incredibly productive helpful and enjoying as well . One of the most
valuable lessons I got from this mentorship was to see how Shauh khan and David
hunter were doing their job with such enthusiasm . She poured such energy into
this program that she used to answer our questions one by one it did not matter
to her whether it was silly questions or not she would take good amount of time
for each candidate’s questions and thoroughly investigate about it and then she
would give talks on that question and would give detailed suggestions and in
between David would remind us what we were missing he would tell us all those
minute details that we eventually miss also he was very helpful .Both of them
used to answer our questions with good details .It was amazing to see both of
them working it was such that both of them emphasized on every minute detail
and left nothing undone . They did their job beautifully.

Summary

At last this mentorship has been very helpful to me since I was new to open source
not only it helped me submitting patches to Linux but also taught me some valuable
lessons that I think I would not learned somewhere else . I submitted at least six
patches to Linux during this program and many are under review since I learned
submitting patches during this program I think I will go on submitting patches in
the future as well because it is such and amazing ecosystem to work with . I am
grateful for this mentorship that such good mentors have taught us and guided us
on the way towards open source . Thanks to Shuah khan and David hunter .

This file is hosted on Github pages and can be visited using this link
            https://i-shihao.github.io/shihao/
