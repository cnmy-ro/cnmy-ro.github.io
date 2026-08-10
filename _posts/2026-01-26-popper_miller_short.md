---
title: "A Short Exposition of the Popper-Miller Theorem"
excerpt: ""
last_modified_at: 2026-01-26T20:00:00-00:00
author_profile: false
# header:
#  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories: [epistemology]
toc: true
---


## Introduction

Probability theory generalizes [propositional logic](https://plato.stanford.edu/entries/logic-propositional/) by enabling reasoning with degrees of certainty and has therefore been used as the foundation of the scientific language in which humanity's best theories of nature are expressed. 
Science has often been mis-understood to be driven by the process of induction -- of obtaining supposedly absolute and general laws from limited observations of nature.
Thus, under this assumption, it is natural to expect probabilistic logic to be able to explain the phenomenon of induction.
Popper and Miller's result shatters this expectation. This short article attempts to be an intuitive exposition of the Popper-Miller Theorem [(Popper and Miller, Letters to Nature 1985)](https://fitelson.org/probability/popper_miller.pdf). 

Central to this topic is the philosophical [*problem of induction*](https://plato.stanford.edu/entries/induction-problem/) first formulated by David Hume [(Hume, *A Treatise of Human Nature*, 1739)](https://davidhume.org/texts/t/). The problem of induction may be stated as follows: 
> Given a set of local observations (local in time, space, etc.), how does it logically produce (or rather "induce") a general theory whose reach goes well beyond the local scope of this data?

This is a profound problem as it questions the foundation of what we can possibly know, both as individual entities living our personal lives and as a knowledge-creating scientific community. How does a child implicitly learn the physics of the World and the social norms of its culture by merely interacting with them, and what is the reach of its explanations? How robust is the knowledge that is learned by evolutionary selection, encoded in genes, and transmitted across aeons? What exactly happens when an AI system is learning from data, and is it possible to know a priori the full set of scenarios and ways in which it will fail? What is the guarantee that the World as we understand it will keep working the same way it always has — can the rules not change the very next moment?


## Notation
- $h$: proposition representing the general hypothesis
- $e$: proposition representing the local empirical evidence in favor of $h$


## The Given
- $e$ is deducible from $h$, i.e. $p(e\mid h) = 1$
- Bayes rule: $p(h\mid e) = \frac{p(h) p(e\mid h)}{p(e)}$
- Assume $0 < p(e) < 1$ and $p(h) > 0$
- Hence: $p(h\mid e) > p(h)$ (Eq.1)
- That is, the probability of $h$ increases in the light of $e$.
- This may lead to the mistaken interpretation that $h$ is induced from $e$ by the process of Bayesian probabilistic inference.


## The Problem Formulation
- Popper's decomposition: $h = (e \lor h) (e \rightarrow h) = d \cdot i$
    - where $d = (e \lor h)$ is the component of $h$ deducible from $e$, and $i=(e \rightarrow h)$ is the non-deducible component.
    - In other words, $h$ is true if $e$ is true AND $h$ holds beyond the scope of $e$.
- Now:
    - Without knowing $e$: $p(h) = p(i) p(d)$
    - In the light of $e$: $p(h\mid e) = p(i\mid e) p(d\mid e) = p(i\mid e) \cdot 1$
- $p(h\mid e)$ is greater than $p(h)$ (from Eq.1) and $p(d\mid e)=1$ is greater than $p(d)$. But, it's not clear whether the probability of $i$ increases in the light of $e$.
- Since $n$ goes beyond the scope of the evidence $e$, the problem of induction can be formulated as follows: 
    - Is $p(i\mid e) > p(i)$?


## A Visual Proof
Truth value of $i=e \rightarrow h$ as a function of $e$ and $h$ is shown in the following table:

![e implies h](/assets/images/signum_figs/fig--poppermillershort--eimph.drawio.png)

Note that:
- With no knowledge of $e$, proposition $i$ holds in 3 out of 4 possibilities. In the light of $e$, it holds only in 1 out of 2 possibilities. 
- Thus, the more likely $e$ is to be `True`, the less likely $i$ is to be `True`.

More concretely:
- Since $(i) = p(e,h)p(i∣e,h) + p(−e,h)p(i∣−e,h) + p(−e,−h)p(i∣−e,−h)$ 

  $= p(e)p(h\mid e)\cdot 1 + p(-e,h)\cdot 1 + p(-e,-h)\cdot 1$ 
  
  $= p(e)p(h\mid e) + p(-e)$,
- And $p(i\mid e) = p(h)p(i\mid e,h) = p(h)\cdot 1 = p(h)$,
- Therefore, $p(i∣e) = p(h)p(i∣e,h)$ 
    
    $= p(-e) - p(h\mid e)(1 - p(e))$ 
    
    $= p(-e)(1 - p(h\mid e))$
    
    $= p(-e)p(-h\mid e) > 0$.
- Q.E.D.

In other words, the probability of the inductive component $i$ decreases after observing $e$. The net increase from $p(h)$ to $p(h∣e)$ via Bayesian inference is explained by the fact that the increase from $p(d)$ to $p(d∣e)=1$ more than compensates for the drop from $p(i)$ to $p(i∣e)$. This latter drop in probability after observing e is proportional to both $p(−e)$ and $p(−h∣e)$.


## Conclusion

Any evidence supports a hypothesis only deductively, i.e., so far as the general hypothesis explains the local measurement. Beyond the scope of the evidence, nothing can be said about the truth of our hypothesis, except when considering also the “surprise” towards the source of this evidence (i.e., the improbability of observing it) and the chance of falsification of our hypothesis despite this evidence (i.e., the improbability of its truth in situations where there’s a lack of data). These latter two factors exist, in a sense, on a level above the evidence itself, and they depend on the background knowledge of the enquiring agent, e.g., its understanding of the problem at hand and the limits of its hypothesis and of its experimental setup. In fact, the more improbable (the post-measurement inductive component of) our hypothesis is, the more “empirical content” it is said to have, the more falsifiable it will be, and thus, the “better” it is as a hypothesis.

Thus, there is no such thing as the (probabilistic) process of induction of a general theory from local empirical data. Accumulation of positively supporting pieces of evidence does not automatically justify our confidence in the general truth of our hypothesis beyond the scope of this data.

And there is no need for such logical justification. Knowledge, if defined as a web of yet-to-be-falsified hypotheses in the context of some set of problems, can never be certain, infallible, and all-encompassingly general. It is because any piece of data is always theory-laden and fundamentally limited — its sampling is guided by, and its interpretative meaning resides in, the context of the problem-situation and the set of competing conjectures proposed to overcome the problem.