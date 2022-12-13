---
layout: post
title: Music theory in F# - Random note
date: 2022-12-11 12:00:00
description: Music theory in F# - Random note
tags: F# MusicTheory
---

# First step: Random note

This is the first part of the music theory in F# series:
- [Introduction](/2022/12/11/fsharp-music-theory-00-introduction)
- Step 1: Random note
- Step 2: [The Major scale](/2022/12/11/fsharp-music-theory-02-major-scale)
- Step 3: [Chords of the Major scale](/2022/12/11/fsharp-music-theory-03-chords)

## Theory

There are 12 notes in occidental music theory, 7 natural and 5 altered:
```
Natural: C, D, E, F, G, A, B
Altered: C#, D#, F#, G#, A#
```
Each notes are separated by a semitone. If you look at a piano board, the white keys are the natural notes and the black keys the altered:

![Piano keyboard with the name of the notes](/assets/images/fsharp-music-theory/KeyboardWithNotes.jpg)

A sharp (`#`) means that the base note is a semitone higher, so `A#` is a semitone higher than `A`.

A flat (`b`) means that the base note is a semitone lower, so `Bb` is a semitone lower than `B`.

`A#` and `Bb` are enharmonic, it means that they produce the same sound.

If you add 12 semitones to a note, upwards or downwards, the note will be the same from the start but with a higher or lower pitch. They are called octaves.

![Piano with all the C marked as octaves](/assets/images/fsharp-music-theory/Octaves.jpg)

## Code

Like I said before, some notes produce the same sound, so for the sake of simplicity, I will represent only sharp notes and not flat ones for now.

```fsharp
type Note =
    | C | CSharp
    | D | DSharp
    | E
    | F | FSharp
    | G | GSharp
    | A | ASharp
    | B

module Note =
    let all = [
        C; CSharp
        D; DSharp
        E
        F; FSharp
        G; GSharp
        A; ASharp
        B
    ]
```

The type `Note` is a union type which mean 
> It's either `A` or `ASharp` or `B` or ...

The `Note` module lists all the functions and values related to the concept of `Note`. `all` is the list of all possible `Note`.

Now, I want to choose a random note:

```fsharp
open System

let random = Random()
let randomIndex = random.Next(0, Note.all.Length)
let randomNote = Note.all.[randomIndex]
```

`randomNote` is the note at a random index between 0 and 11 in the `Note.all` list. FSI shows the random note, but a fancier representation will be better:

```fsharp
module Note =
    let name note =
        match note with
        | CSharp -> "C#"
        | DSharp -> "D#"
        | FSharp -> "F#"
        | GSharp -> "G#"
        | ASharp -> "A#"
        | n -> string n

    // other functions and values

// previous code with randomNote

printfn "Chosen note: %s" (Note.name randomNote)
```

`match ... with` is a pattern match, it's like a (very) powerful `switch`. So `name` works like this:
- If it's a sharp note, return `"...#"`
- Else return the string representation of the note

Another big F# feature is that the compiler infers a lot of things for you. It can infers that `name` is a function that takes a `Note` as argument and returns a `string` because the pattern matching matches `Note` values and returns `string`. So no need to be explicit about the types in general, the code will be more concise with this strong typing. But if you prefer to be explicit, you can rewrite this function as follows:
```fsharp
module Note =
    let name (note: Note): string =
        match note with
        | CSharp -> "C#"
        | DSharp -> "D#"
        | FSharp -> "F#"
        | GSharp -> "G#"
        | ASharp -> "A#"
        | n -> string n
```

Then the `printfn` function write in the console:
```
Chosen note: F#
```

You can also use the `|>` operator to simplify the code:
```fsharp
randomNote
|> Note.name
|> printfn "Chosen note: %s"
```

This operator is like the `|` operator in Unix, it takes the value on its left and passes it as the last argument of the function on its right:
```fsharp
let increment x = x + 1

increment 2 // returns 3

3 |> increment // returns 4
```

It is a powerful operator which is used a lot in F#.

## Conclusion

That's all for this step. You can check out the full code [here](https://github.com/cmoinard/FsMusicTheory/blob/main/Scripts/01_RandomNote.fsx).

Next step: [The Major scale](/2022/12/11/fsharp-music-theory-02-major-scale)