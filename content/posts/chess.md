+++
date = '2026-08-18T16:26:31+02:00'
draft = false
title = 'Chess Programming'
weight = 1
+++

I should mention that I spend a decent part of my time doing chess programming.
I've been working on my chess engine Bread and contributing to Stockfish for a few years.

Bread is a chess engine written in C++. I started working on it when I was in high school, and learned a lot about programming and computer science during the development process. Currently, Bread uses a heavily modified version of the minimax algorithm to search for moves, and an NNUE (Efficiently Updatable Neural Network) to evaluate leaf positions. This summer, Bread has been invited to participate to the TCEC (Top Chess Engine Championship), we'll see how it goes.

If you want more information about chess programming, the readme of my engine is detailed enough to give an overview. I unfortunately do not know about a good all-in-one resource like a book. I will therefore give some helpful references.

- [Sebastian Lague's video](https://youtu.be/U4ogK0MIzqk?si=IbirXWnJiRlI1Bj9)

- [Stockfish's nnue description](https://github.com/official-stockfish/nnue-pytorch/blob/master/docs/nnue.md)
   An *OUTDATED* description of state of the art nnues as of 2022. Many improvements have been made to nnues since then, but the core principle and some optimizations are still well explained.

- [a github nnue guide](https://github.com/Kirill020708/NNUE-guide) This guide is written by known engine developers, I haven't read it yet though.

And the blogs listed in the [Blogroll]({{< relref "../resources/_index.md" >}}).

You can also join the Stockfish discord server. A lot of very helpful people and top engine developers have joined this server, and can discuss or answer questions.