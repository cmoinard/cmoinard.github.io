---
layout: post
title: Music theory in F# - Introduction
date: 2022-12-11 12:00:00
description: Music theory in F# - Introduction
tags: F# MusicTheory
---

This is the introduction of the music theory in F# series:
- Introduction
- Step 1: [Random note](/2022/12/11/fsharp-music-theory-01-random-note)
- Step 2: [The Major scale](/2022/12/11/fsharp-music-theory-02-major-scale)
- Step 3: [Chords of the Major scale](/2022/12/11/fsharp-music-theory-03-chords)

This serie is part of the [F# Advent 2022](https://sergeytihon.com/2022/10/28/f-advent-calendar-in-english-2022/).

## Backstory

I LOVE playing music. I started the guitar when I was 10, I learned by myself with guitar tablatures. I did the same when I started the piano 6 years ago. But another passion came through: Music theory.

I love to understand how a song is made, why these chords sound good. I watched tons of videos on Youtube, especially my two favorites:
- [Jake Lizzio](https://www.youtube.com/@SignalsMusicStudio)
- [Adam Neely](https://www.youtube.com/@AdamNeely)

It helped me to understand what I play, which are almost only covers. I do not compose music. I don't like it and the little things I composed were not as good as I want.

One day, I had an idea. What if I create a script to generate a music scale to help me write something. For instance, the script can say: "D# phrygian" and it will force me to compose something in this scale. So I wrote a script with F#. It didn't help me compose music AT ALL because I really enjoyed writing this script and I couldn't stop adding features.

## Prerequisites

No need to know F#, this serie is beginner oriented.

If it's your first time with F#, welcome! F# is a functional-first and strongly typed language on dotnet. Be careful, the indentation is important, like Python. The order of declarations too, everything you use should be declared before.

If you want to test the F# code in these articles, you will need to:
- Install [dotnet](https://dotnet.microsoft.com/en-us/download)
- Install VsCode with the Ionide-Fsharp extension

Once they are installed, set the language in VsCode as F#, then you can select code and press `Alt+Enter` to send the selection into the F# Interactive (FSI).

You can also execute a script by opening a terminal and execute:
```
dotnet fsi MyScript.fsx
```

I will dive a bit into music theory, but you don't have to know it. I hope you will understand how music can be made. I recommand to install a piano app on your phone to have a better idea of what I will explain.

If you already know music theory, you will see horrible things. Keep in mind that the mistakes are intentional to simplify the explanations, but I will fix them later.

Next step: [Random note](/2022/12/11/fsharp-music-theory-01-random-note)


## Update 2022-12-13

I started writing this article weeks ago, I was really excited for my first contribution of the F# advent, I thought this subject was specific enough to be original.

But just a week ago, [Michal Nebes](https://mastodon.social/@emneb) published a blog article on the [same exact subject](https://blog.emneb.dev/posts/02-generating-chord-progressions-in-fsharp.html) 😅

His article is really great and he goes further by creating sounds, exactly what I was searching for since months!

If you already read his article, I hope you'll enjoy mine as well 🙏