---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "6 Monthes In"
subtitle: "Or How do I do the Podcast Editing?"
summary: ""
authors: []
tags: ["Podcast Editing", "Otherwhere", "Arcadia, CA"]
categories: []
date: 2020-11-01T11:31:15-07:00
lastmod: 2020-11-01T11:31:15-07:00
featured: false
draft: false
toc: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

I've been editing podcasts for six months now, working on two different pods. My work has been publically lauded by *Cool People On The Internet*. You'd think I'd have something resembling a consistent procedure or methodology. You would be very wrong. No 2 episodes so far have been done exactly the same. But hey. Let's get into it.

{{% toc %}}

## Intent

> Everything left off the cutting room board is needed and essential to  the game. And by listening, you feel that. You feel intelligent design  and not just chaos.  
>
>  --- <cite> Maria Fanning </cite>[^1]

One of my goals when we embarked on this adventure --- beyond trying to survive the apocalypse and everything [*waves hand in expansive manner*] --- was just to make content that I would want to listen to. A big part of that is the editing. I've found that what is probably the most popular Actual Play on the internets --- let's call it Charlie Romeo --- is just something I cannot consume. And I've tried! A few times even.

Charlie Romeo feels a lot like watching a group of friends sitting down to play a TTRPG. There's minimal, if any, editing. You, the consumer, are experiencing what it is like to be at the table. You get all the rule discusson, all the cross-talk and mechanics. You get all the pauses while people roll or plan. And I can understand while others might be into that. You get the atmosphere of playing on top of the playing itself.

For me personally though, I don't need an in-depth discussion of how to play a game. Hearing the players do math doesn't add anything to the experience for me.  So I cut a lot of that out. I shorten pauses, cut out a lot of the table talk, and snip discussions down to what's needed to understand what's going on.

And what you're left with is story, and enough of the mechanics to place it within the context of the game being played. I honestly think it's a lot easier to listen to, and it seems that other people seem to agree with me, and that's really, *really* cool. It's quite a bit of work. More so because we started with me having roughly 0 knowledge of audio editing. Just determination, desire to be awesome, and lots of ADHD hyper focus.

[^1]: Fanning, M. (2020, October 20). *Exploring The Multiverse: Why You Should Listen to Otherwhere*. Cannibal Halfling Gaming. https://cannibalhalflinggaming.com/2020/10/02/exploring-the-multiverse-why-you-should-listen-to-otherwhere/. 



## Tools

### Audio Editor

I've used 3 audio editors so far. [Audacity](https://www.audacityteam.org/), [Reaper](https://www.reaper.fm/index.php), and most recently [Hindenburg Journalist Pro](https://hindenburg.com/products/hindenburg-journalist). And so far, I think Hindy is my favorite, with Reaper as the close second.

Reaper and Hindy are both non-destructive audio editors, meaning that when you make changes in them, the original files aren't changed. If you cut something, but realize cut that "ssss" sound at the end of a word making it sound weird, you can go in and stretch a little handle to get it back like it never left in the first place. Audacity is still a destructive editor. When you save, it overwrites whatever file you're working on. And yeah, you can (and I do anyway), keep a bunch of different versions to make sure you never lose anything. But when you have to recover something, it's always annoying.

Beyond that, everything you can do in Hindy you can do in Reaper. But Reaper took a lot more work to set it up in a way that works well for podcast editing, since it's designed for music. See, Reaper is infinitely customizable. You can change what your workstation looks like, your keybindings, even create a chain of actions and then bind that to a single key. But Hindy is designed for Spoken Word out of the box, and has a bunch of quality of life features that make life easier.

For example, the number one action I do in terms of quantity is to delete a section of all tracks so that everything remains in sync. In reaper, this requires a custom action chain combining 3 other actions,[^2] one of which does not come in stock reaper and needs to be downloaded first.

In Hindenburg, you can do this out of the box in 1 or 2 key-presses. **Ctrl-a** if you don't already have all tracks selected, and then **ctrl-x**.

As for other things that have lead me to make the switch, we have:

* Single knob noise cancelation. Just turn it until you can't hear it!

* Single knob compression. Want to have that radio broadcaster sound? Turn it up to 11.

* Automagical EQ using Voice Profiles. (Though this may be replaced. Remember what I said about me always changing things up?)

* automatic volume leveling as you import files, or with a single key press.

* **Magic Levels** (no, seriously, that's what the feature is called.)

  * Adjustment of volume level *within* a track, not just the track as a whole to try and keep a steady volume even if the recording isn't.
  * lets tracks be aware of each other
    * Ducks one track when it notices that it's echoing another. I record with 2 others in a room, and this is a huge time saver.
    * Fades music up and down when it notices when it's playing while someone is talking.
  * A lot easier to set up fades and ducks even without magic levels. Don't have to mess with "automation" which shows up as... like another track that you have to fiddle with in Reaper.
  * Volume Normalization on export. Did you know that a podcast should probably be at -16 LUFS for stereo, or -19 LUFS for mono? Hindenburg can do that!
    * Don't know what a LUFs from your rights? Lufs are some kind of industry standard for how loud something should be so that you don't have to turn the volume knob between podcasts or worse, episodes within a podcast.

So while I think you can do more with Reaper, I think if I had the choice of starting over with one or the other, I'd just use Hindenburg. There's just so much I had to set up, learn how to use, or find a plugin for that Hindenburg already does. That being said, Hindenburg pro is an investment, and Reaper is only $60 and can still do everything you need.

{{% callout note %}}
If you do want to use Reaper, I highly recommend reading up [Podigy's Podcast Editing guide](https://podigy.co/podcast-editing-guide/). It was more than enough to get started to get good sounding audio. (See first episode of Otherwhere.)
{{% /callout %}}

### Plugins
I've played around with quite a few plugins. Most free, because this was just supposed to be a fun thing I do, and a couple of free trials of premium stuff. And while I one day hope to be able to justify $1200 for the [Izotope RX]( https://www.izotope.com/en/shop/rx-8-advanced.html) series, I have to give it as pass at this moment in time.


For now, I think I am leaning toward the [Accusonus ERA Bundle]( https://accusonus.com/products/audio-repair/era-bundle-standard), which has a bunch of useful one-knob plugins for a much easier to swallow price. Of special intrest to me are the Auto-EQ and the Voice Deepener, which I think makes voices sound a lot better without a lot of work! Especially the Voice Deepener, which claims to make your recorded voice sound more like the voice you hear in your own head. 


## TL;DR
I, at least for the most recent episode, am using Hindenburg Journalist Pro along with the Accusonus ERA bundle, combined with a healthy dose of hyperfocus, attention to detail, and ruthless pair of digital scissors for cutting uneeded content to make Otherwhere the best podcast I can make right now, but one that is always getting better as I learn more.

  

[^2]:“*Item: Select all items in current time selection*”, “*Time selection: Remove contents of time selection (moving later items)*”, and *“SWS: Crossfade adjacent selected items (move edges of adjacent items)”*

