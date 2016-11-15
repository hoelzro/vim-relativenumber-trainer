# Vim relative number trainer

A little plugin I wrote to train myself to use relative line numbers.

# Rationale

I had a problem using regular `:set number` in Vim - if I was working on
a large file, all of the line numbers around me would be something like
"2603", "2604", etc.  Since the way I was most accustomed to moving around
the screen was with `gg`/`G`, I would end up typing `2063gg` to get to a
visible line, which is quite a lot to type.

So, with that problem in mind, I turned on `:set relativenumber`...only to
run into a new problem.  This new problem was that my fingers were so
wired into typing `$NUMBER gg`, which meant I would look at the relative number
of "10" for ten lines above the cursor and type `10gg` rather than `10k`, taking
me to the beginning of the file and throwing me off balance.

I wrote this plugin to train my fingers to get used to typing `10k` and such.
It does this by overriding `gg` and `G`.  If I type one of those commands with
a number prefix and that number is likely a relative number (judging from the
lines visible on screen), it cancels the command and admonishes me with a one
second delay.  If it's ambiguous, it assumes that I am looking at the line
above the cursor, since this is what I tend to do.  So typing `2603gg` to get
to another region of the file will work as it normally does, but `10gg` will
likely say "hey, you probably meant to do `10k`".  In the far less
frequent occasion that I actually *want* to go to line 10, I can always do
`:10`.

I should mention that I no longer use this plugin, because it worked and I no longer
need it =)
