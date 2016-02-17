---
title: Compare Date with PERL
tags:
  - English
  - PERL
  - example
  - 英语练习
id: 237
categories:
  - Uncategorized
date: 2008-01-28 17:19:22
---

(This is one of my English Diary, just for exercise.)
I haven't touch PERL for a long time, feel so tired to debug script error on page with "Internal Server Error", that's the reason I don't like it. But the reason I still use it is because [CPAN](http://search.cpan.org/), it's a huge library for PERL Archive. You can easily find any function you can imagine. Here's a example to Compare Date.
[code lang="per"]
#!/usr/bin/perl
print "Content-type: text/htmlnn";

# you need three packages: Date::Parse, Time::Local, Time::Zone;
# http://search.cpan.org/perldoc?Date::Parse
# http://search.cpan.org/perldoc?Time::Local
# http://search.cpan.org/perldoc?Time::Zone
use Date::Parse;
my $secs = str2time("2008-02-14");
my $now=time();
# check we got something useful back
unless (defined $secs){
die "Can't parse '$time' as a time or daten";
}
print "End as:n", "'$secs' (".gmtime($secs).")
n";
print "Now as:n", "'$now' (".gmtime($now).")
n";
if($now &gt;= $secs){
print "It's time to go now.";
}else{
print "Don't worry, still have time.";
}

[/code]