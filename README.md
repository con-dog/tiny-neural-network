# Summary

> [!WARNING]
> This write-up is an active work in progress. Some benchmarks and claims are changing as I continue to revisit the project. My speed of experimentation outpaced my speed of understanding.
>
> This is the public write-up for a private repository, so some of the content is intentionally vague or incomplete. If you have questions, please reach out to me directly.

[Link to the Maze Solver]()

> [!NOTE]
> This maze solver was intended as a weekend project where I naively thought I could implement a maze-solving neural network in a weekend, that could solve 100% of unseen mazes. How wrong I was.

## Watch a 14 Byte Neural Network Solve a Maze

![Watch a 14 Byte Neural Network Solve a Maze](./media/minimio-maze-solver-main.png)

## Watch a 178 Byte State Machine Classify Lexical Tokens

![Watch a 178 Byte State Machine Classify Lexical Tokens](./media/minimio-microlex-main.png)

# Architecture

## The Quick and Dirty Version

This project was/is an experiment across 47 distinct phases, initially attempting to create a 100% solve rate maze-solving neural network from scratch, then quickly realizing I'm not going to achieve that, so instead trying to solve the highest % of mazes with the most compact neural network representation.

The flagship maze solver occured in phase 43 at - 14 bytes (not including the runtime, the 14 bytes is the state machine) - with a 96.5% solve rate on unseen/untrained mazes upto a 21x21 grid, at which point increasing grid size decreases the solve rate - to what exact extent I am yet to measure and benchmark.

The maze-solving agent/s were trained on "perfect" mazes, "perfect" mazes with "loops", "open" grids with no walls, and open grids with walls/obstacles/islands.

A common critique of these sorts of training regimens is that the models learn maze-solving specigic to the maze-generation algorithm they were trained on. To understand if that was the case, the benchmarking suite was extended to contain other common/famous maze-generation algorithms for benchmarking only - not for training. For the flagship models, the median solve rate drops by roughly 1% on alternative maze generation algorithms. A result that indicates the models are not actually biased to the training-specific mazes.
