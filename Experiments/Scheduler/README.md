# Scheduler

> Sketch of how a general purpose spaced repetition scheduler might work.

We want to find out how a general purpose spaced repetition scheduler might work. 

## Sub Experiment 1 (Began 10/23/2024) 

**Goal:** Implement a simple scheduler.

What does a scheduler actually do?

Given a set of factoids, and some review history of those factoids, the scheduler has two functions:

- get_factoid, which returns a factoid
- update_history, which updates the review history of the factoid

Problems:

- How would we incorporate information about how factoids are related?
- We have assumed that the factoids were like individual flashcards being presented to the user, but what if they are not individual cards, but rather the user is presented questions that require / include multiple factoids.

This second is really important in the context of a language learning app, where the factoid is the word, but where the question is a phrase (comprehension or production).
Is this true? Suppose I'm learning japanese. Sometiems the factoid is not a word per-say, but the representation of a word such as when learning kanji. 
Perhaps different factoids have different rules for how they are rendered? I.e. kanji<>word pairs are factoids, but when they are presented as prompts they are presented as front-back flashcards? Alternatively, the kanji can be treated just as another 'word' and appear in sentences normally. The sentence would have to have some glossing to make it initially comprehensible... This seems like a more graceful solution to the kanji problem.

Conclusion: kanji will be treated as any other inflected form of a word

Corrolary: Inflected forms will be treated independently. (We will reffer to this as the naieve approach to inflected forms.)

I'm worried I'm trying to be too abstract too early. Now that we have shown that the word as factoid approach is sufficiently general to handle Japanese's problem of having multiple representations of a word, lets assume this approach for initial experiments. 

Now that we have established that we can use the inflected-form as factoid approach. We need to consider how we will map the factoids to prompts. 


## Glossary

- Prompt, a question posed to the user to get them to recall a fact or practice a skill. A practice problem.
- Factoid, the lowest level knowledge unit. The smallest knowledge unit the memory model operates on.

