---
title: "Learning Agent That Plays Tic-Tac-Toe"
date: 2018-04-18T12:45:54+05:30
tags:
- artificial intelligence
- python
- how-to
categories:
- project
---

## Defining the problem
The problem is to create a learning agent that plays Tic-Tac-Toe.
The accompanying implementation can be found [here](https://github.com/coditva/tic-tac-toe).

## The knowledge base

Our agent starts with some knowledge about the game. It knows:

 - Three `x` or `o` in a row end the game in a win/loss respectively.
 - No boxes left end the game in a draw.
 - Always try to win. If not possible, try to not lose.

The positions on the board are assumed to be numbered from 0 to 8. We will define the atoms for our knowledge base as follows:

 - `W[x]` is true if putting mark at position `x` results in a win.
 - `X[x]` is true if position `x` is marked by agent (i.e. X).
 - `O[x]` is true if position `x` is marked by other player (i.e. O).
 - `E[x]` is true if position `x` is empty.

### Initializing knowledge base

 Since the agent knows about what results in a win/loss, it can fill up the knowledge base with these basic inferences:
```
E[x] = (not X[x]) and (not O[x])

X[x] and O[x] = false

W[0] = W[0] or (E[0] and X[1] and X[2])
W[0] = W[0] or (E[0] and X[3] and X[6])
W[0] = W[0] or (E[0] and X[4] and X[8])
...
```

## Game play

When this initial knowledge base is complete, our agent starts playing. Whenever the game state changes, the agent add new information to the knowledge base and evaluates the possible models for the game. If it's agents turn, it chooses the model which results in a win and takes turn accordingly. If there are multiple models, it chooses any one of them randomly.

### Scene 1
Suppose that the state at a given moment is:
```text
x  x  -
-  o  -
o  o  -
```
The agent can place mark on `x` if `E[x]` is true i.e. 2, 3, 5 or 8. Now, our agent knows from the knowledge base that `E[2]` is true and `X[0]` is true and `X[1]` is true. It can conclude that `W[2]` must be true and places the mark there.

### Scene 2
Now suppose that the state at another given moment is:
```text
o  x  -
-  o  -
x  o  -
```
The agent sees that there is no place for a win, it checks if there is any place that can result in a loss. It sees that if the opponent places a mark on position 8, the agent loses. So, it goes and places a mark on 8 to block it.

### Scene 3
Now suppose that the state at yet another given moment is:
```text
o  x  -
o  -  -
x  o  -
```
The agent sees that there is no apparent win or loss. So, it looks ahead to find if there is a possibility of a loss. It sees that if the opponent places the mark on 4, 5 or 8, it can lose. It also sees that if the agent places the mark on 4, it might later win. Now, it finds that the position 4 is desirable for winning as well as stopping a loss, so it places the mark on 4.
