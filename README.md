# someone-like-youuuuuu-code
A catalogue of some bad programming decisions.

## inspired by a tweet, and loathing bad code that I was forcing myself to write.

https://twitter.com/bendhalpern/status/1091535397543464960
<center>
  
<blockquote class="twitter-tweet" data-lang="en"><p lang="und" dir="ltr">{ ❤️ } <a href="https://t.co/95skyKfxyk">pic.twitter.com/95skyKfxyk</a></p>&mdash; Ben Halpern 🤗 (@bendhalpern) <a href="https://twitter.com/bendhalpern/status/1091535397543464960?ref_src=twsrc%5Etfw">February 2, 2019</a></blockquote>

![someone_like_you](https://user-images.githubusercontent.com/11463275/53697901-17847b80-3da4-11e9-8053-5a227bd71714.gif)

</center>

1) deeply nesting functions on a backend service as shown in the gif above.

![screen shot 2019-03-03 at 11 13 02 am](https://user-images.githubusercontent.com/11463275/53698021-5d8e0f00-3da5-11e9-8620-a2c349537e7b.png)

2) nesting an entire css library into an scss class ... to override styling of material UI;
<br/>Instead of using withStyles as suggested by the documentation.

3) launch agent is a process that runs when the computer turns back on or wakes from sleep.
<br/>Change the background of a computer to be a screensaver 
<br/>restarting with reboot wake from sleep or after the process it was spawning is quit/killed.
