---
layout: post
title: Multi-Armed Bandits
---

See these combined and condensed notes of [Chapters 2 and 6 from Bayesian Hackers](ABTestingNotes.pdf) book.


<!-- TODO  MAB intro text, context --> 
<!-- TODO  MAB flow: does this follow ID or MDP? --> 
<!-- TODO  where is this text from? did I copy it? --> 
<!--
## n-Armed Bandits
This is the simplest domain where the exploitation-exploration tradeoff occurs. 
There is simply one state and a $n$ actions which can be taken. Each action has
an independent reward function, which is a distribution. The agent maintains an
estimate of the value of each action and wants to maximize its reward over time
given its uncertainty. The actions don't change the world, you are just trying
to determine the reward model for a single state of a frozen MDP. That's why
they use bandits, since the state is irrelevant, each pull is independent of
the last pull.
The best strategy is to mix some exploration, choosing actions which aren't the
best according to your estimates, in order to increase your certainty and then
to exploit your estiamte of the best action the rest of the time.

More and more complexity can be added by making the rewards drift over time,
causing the bandits to be correlated together, to alter the reward based on as
sequence of actions and of course by adding states to the bandits so that it
becomes a normal MDP again.{% include sidenote.html id="refSutton" note="See Sutton Reinforcement Learning book chapter 2." %}:

-->

<!--
## Three Fundamental Pieces of RL in Term of Bandits
- **Reward Model Based on Actions** 
  - Given one bank of n bandits, you need to learn the optimal policy for pulling arms. ie. the reward distirubtion over actions.
  - **(MDP: 1 state, n actions)**
- **Different Reward Model per State** 
  - Multiple sets/banks/rows of bandits.  
  - Each bank has its own reward model for the arms, you don't know any of them.
  - But if you are given a signal about which bank you are at, ie. which state you are in, then you can learn a policy.
  - **(MDP: m states and n actions for m banks of n-armed bandits and a random transition model)**.
- **Actions Affect State Transition** 
  - Finally, if actions influence which state you end up in next then it is a full RL problem. 
  - This is like each arm pull influencing which bank of bandits you will go to next.
  - **(MDP: m states and n actions for m banks of n-armed bandits and transition model $$T(a'\vert a,s)$$.)**

-->


