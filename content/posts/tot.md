---
title: "Tree of Thoughts - A Review"
date: 2025-01-12T11:30:04+03:00
draft: false
tags: ['prompting', 'machine learning', 'LLMs']
---

This is my take on the paper **Tree of Thoughts: Deliberate Problem Solving with Large Language Models** by researchers from DeepMind and Princeton University (Yao et al., 2023). It's based on my understanding, and corrections and discussions would be welcome!
_____________________

In my analysis, the ‘Tree of Thoughts’ framework effectively identifies the problem with simple left-to-right decoding in LMs in tasks like lexical reasoning, and combines the generation and evaluation capabilities of LMs with search over a ‘thought tree’. In a way, the CoT framework can be seen as ‘augmenting’ the input with the intermediate steps, and ToT further ‘navigates’ the best of these augmentations. The paper is comprehensive in the sense that it properly sets-up the IO prompting and CoT baselines for the proposed tasks and studies ablations, which gives an idea of performance of the individual components like pruning, evaluator etc.
- The current approach however, has a lot of human-dependence in my opinion, for example, in deciding the task-specific BFS-vs-DFS, or sample-vs-prompt. Example, in the crossword task, we specifically translate the intermediate thoughts into letter constraints for the next input, and this may be an under-utilization of the capabilities of LM. 
Handling the process more autonomously, i.e, the LM deciding whether to use the ToT approach, and then strategies for search, state evaluation, though generation etc. could make it more generalizable and efficient, like Alpha-Go with pure RL and no human-intervention. Retrieval augmented generation, where possible, could be used to save some training in the process.
- Two branches never meet in a tree, however in human thought process for tasks like writing a book in some genre, the author may be considering multiple possible story-lines, and then use elements from the other lines into their final approach. A ‘merging’ of nodes or graph-like approach (like the inter-connection of neurons in original neural networks) might thus benefit creative tasks.
- Though I believe that the paper works towards a general problem solver and not for specific tasks, increasing number of ToT steps for creative writing tasks – deciding the plan, then working the intricate details within parts of the plan, may improve coherence. This will also probably better suit practical use-cases beyond the task of writing paragraphs with given end-sentences.
Another extended research direction would be to extend the framework to handle multimodal tasks.