---
title: "Unboxing and Exploration"
date: 2018-09-30T09:44:43-04:00
description: "My experience with the installation and first bout of exploratory F# coding, along with it some links and references I might end up following"
tags: [
    "introduction",
    "installation",
    "tools"
]
---

## Naive Observations

Unlike most other languages I learned, there wasn't many surprises for me with *F#*. This was mostly because I was eased into the languages through Scott's book. I didn't intend to learn it while reading it, but still had to comprehend what the codes were trying to tell me. While the book's wisdom is easily transferrable to other languages, it's the beauty of the syntax which led me to explore the language further. 

I had prior (and brief) encounter with ReasonML and that was my only ML before this. The differences *F#* seemed to sport in syntax felt pleasant to me. That was followed by blind explorations at [repl.it](https://repl.it). There was nothing wrong with the syntax till I've `Console.WriteLine`ed something and saw the parenthesis, where `printfn` did not. That's where I started looking into .NET integration and the slight syntax differences were something I didn't like as much. But I guess that's why I put **Naive Observations** as the title here.

Lots of F# tutorials felt like they were targeting C# programmers. Many had lots of .NET terms in it (I had to google BCL). The same thing goes for object oriented treatments. I am not saying those are bad things but I wondered how interesting the learning experience might get if I spend the first few weeks filtering out the objects and non F# things and extract the functional parts? That *could* keep some challenges at bay while inviting new ones? I guess I'll find out.
 
## Unboxing

Even without trying, I was expecting the installation to be painful as I'm using Linux and am unwilling to change my OS because of just one language. I head off [here](https://fsharp.org/use/linux/) and it started to work fine, no pain involved. The VSCode integration was perfect as expected. I later ended up installing `dotnet` as well.

I fired up `fsharpi` and typed out `printfn "Hello F#"`, it worked fine.

Then I fire up the console and  create `~/repos/fsharp/first`, then `echo 'printfn "Hello World"' > Hello.fs`, `fsharpc Hello.fs`, `./Hello.fs`.

Now I am equipped to explore the language in a `REPL` and also store some code and run it.

## Running a File

Since I installed `dotnet`, I *can* do a `dotnet new console -lang F#` and followed by a tool of `dotnet build` and `dotnet run` etc, I can run project. The process is documented [here](https://docs.microsoft.com/en-us/dotnet/fsharp/get-started/get-started-command-line).

But I don't know what a `sln` file is, and I really think that would be a noise in my learning experience, learning the build tool and all that. So I'd stay within command line with common faces. In the previous section I had run a single file source code, now I would go multiple.

So my directory is `~/repos/fsharp/first` and added two files to it- `Pi.fs` and `Main.fs`. My intention was to add an `pi` as a value in one file and print it from the other. Lots of trials and errors happened here. There's `namespace` and `module`. Any except the last source file needs to have those. To use a namespace you need to `open` it. So at the end, my files looked like-

`Pi.fs`

```fsharp
module Main.Library

let pi = 3.1416
```

And `Main.fs`

```fsharp
open Main.Library

printfn "%s" pi
```

To run it, I did a `fsharpc *.fs` followed by `./Program.exe` and it worked. However, when playing around again it didn't. The order of file inputs that you feed to the compiler is important and `*.fs` had changed orders based on last edits of the file. It is important that I put the "Entry Point" last. So `fsharpc Pi.fs Main.fs` works *all the time*. Will get more treatment of this once I get to compile complexly related files. Hopefully fun times ahead.

As for editor, the [SpaceVim](https://spacevim.org/) `fsharp layer` looked fine, I've been running codes on it while writing this post. Except for some repl integration didn't seem to work. But I think I'll use it for now, keep things light.

## REPL

I have always been a big fan of REPLs. I've been introduced to that lifestyle by Python and I felt immediately productive as I've never seen anything like that before. Richer the REPL experience, more engaging the language is for me. I usually head to the interactive modes of languages way before trying to save the files. If the experience isn't at par and the language isn't a job/school requireent, I run and hide.

For `F#` it was a bit different as I had experienced [repl.it](https://repl.it), the runtime was alien to me, and my purpose was to use one chunk of the system, so I had to make sure I'd know how equipped I'll be. So I started out with the file and then moved on to the REPL.

The interactive mode of *F#* is not as great as ones Python or Elixir have. At least not at first look. There's some code intelligence, an okayish timing tool, some silencers, readline support etc. But not multiline history editing, magic commands, in-code documentation. Not that I could know of at first try. But that's good enough, typed languages are more fun on the editor I guess, it allows you to put some thought and attention the paradigm deserves.

Anyway, `fsharpi` lets me go to interactive mode and write codes there. Thus far I just tried out simpler things but surely I'll try to see how power users use it and write about it some day. For now, my opinion is that *F#* has an average REPL. That'd do.

## OO and C#

Yes *F#* is a multiparadigm language and no matter how functional first it is, that side of the featureset is inevitable. I will just try to delay that.

I am not against Object Oriented Programming. That was the first paradigm I was introduced to and the only one for the next year or so. But functional half of *F#* seemed pretty full featured to me. Especially because I am not using it for my job or something and I have all the time I need.

Whatever I said before becomes easier to accomplish by minimizing C#iness and hardcore .NET intervension. I will try to use pure F# libraries (Is that the term they use?) whenever possible, and note down the use cases where mixed paradigm looks inevitable, probably make a wrapper at least. But something tells me it will unlikely be the case.

## Link List

So what am I using as learning aid? I have [Domain Modeling gone Functional](https://pragprog.com/book/swdddf/domain-modeling-made-functional) already but that is not exactly about learning the language. I was browsing HumbleBundle yesterday and saw [this](https://www.humblebundle.com/books/learn-you-some-code-books). There's an *F#* book there. It's kindof old but I like the feelings of sequencial learning experience books offer. So bought it yesterday and looks like it's a nice book. No *F#* reference list can be complete without mentioning of [Scott's site](https://fsharpforfunandprofit.com/) and the ~2000 pages worth wisdom that gets generated, yet it doesn't seem to be too intimidating or overwhelming. And then there's the [Microsoft Guide](https://docs.microsoft.com/en-us/dotnet/fsharp/). There's `/r/fsharp` and lots of really friendly individuals in Twitter-land.

That's all reference in my arsenal and I'm sure it will improve. No section of reference should be complete without mentioning the "Awesome X" and for *F#* it's [here](https://github.com/fsprojects/awesome-fsharp)

## Coming Soon

I intend to dive deep into making functions in *F#* later today. So that's what I will write about, as I'm working with them. I may have a head start during last week's playing around but I will replay those too.
