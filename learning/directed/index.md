---
layout: post
title: Learning in directed models
---
We now turn our attention to the task of *learning* some of the parameters of a model. Given a dataset, we would like to fit a model that will make useful predictions on various tasks that we care about.

A graphical model has two components: the graph structure, and the parameters of the factors induced by this graph. These components lead to two different learning tasks:

- *Parameter learning*, where the graph structure is known and we want to estimate the factors.
- *Structure learning*, where we want to estimate the graph, i.e. determine from data how the variables depend on each other.
<!-- TODO drop structure entirely, just mention it --> 

In this course we will look only at parameter learning. For more on structure learning see [other sources online](https://ermongroup.github.io/cs228-notes/learning/structure/).

We will consider parameter learning in directed models which can admit easy, closed form solutions. Undirected model learning often involves potentially intractable numerical optimization techniques. Later we will look at Bayesian learning, a general approach to statistics that offers certain advantages to more standard approaches.

## The learning task

Before, we start our discussion of learning, let's first reflect on what it means to fit a model, and what is a desirable objective for this task.

Let's assume that the domain is governed by some underlying distribution $$p^*$$. We are given a dataset $$D$$ of $$m$$ samples from $$p^*$$; The standard assumption is that the data instances are independent and identically distributed (iid). We are also given a family of models $$M$$, and our task is to learn some "good" model in $$M$$ that defines a distribution $$p$$. For example, we could look at all Bayes nets with a given graph structure, with all the possible choices of the CPD tables.

The goal of learning is to return a model that precisely captures the distribution $$p^*$$ from which our data was sampled. This is in general not achievable because limited data only provides a rough approximation of the true underlying distribution, and because of computational reasons.
Still, we want to somehow select the "best" approximation to the underlying distribution $$p^*$$.

What is "best" in this case? It depends on what we want to do:

- Density estimation: we are interested in the full distribution (so later we can compute whatever conditional probabilities we want)
- Specific prediction tasks: we are using the distribution to make a prediction, e.g. is this email spam or not?
- Structure or knowledge discovery: we are interested in the model itself, e.g. how do some genes interact with each other?

## Maximum likelihood

Let's assume that we want to learn the full distribution so that later we can answer any probabilistic inference query. In this setting we can view the learning problem as *density estimation*. We want to construct a $$p$$ as "close" as possible to $$p^*$$. How do we evaluate "closeness"? We will again use the KL divergence, which we have seen when we covered variational inference:

$$
KL(p^*\|p) = \sum_x p^*(x) \log \frac{p^*(x)}{p(x)} = -H(p^*) - \E_{x \sim p^*} [ \log p(x) ].
$$

The first term does not depend on p; hence minimizing KL divergence is equivalent to maximizing the expected log-likelihood

$$ \E_{x \sim p^*} [ \log p(x) ]. $$

This objective asks that $$p$$ assign high probability to instances sampled from $$p^*$$, so as to reflect the true distribution. Although we can now compare models, since we are not computing $$H(p^*)$$, we don’t know how close we are to the optimum.

However, there is still a problem: in general we do not know $$p^*$$. We will thus approximate the expected log-likelihood $$\E_{x \sim p^*} [ \log p(x) ]$$ with the empirical log-likelihood (a Monte-Carlo estimate):

$$
\E_{x \sim p^*} [ \log p(x) ] \approx \frac{1}{|D|} \sum_{x \in D} \log p(x),
$$

where $$D$$ is a dataset drawn i.i.d. from $$p^*$$.

Maximum likelihood learning is then defined as

$$
\max_{p \in M} \frac{1}{|D|} \sum_{x \in D} \log p(x),
$$

### An example

As a simple example, consider estimating the outcome of a biased coin. Our dataset is a set of tosses and our task is to estimate the probability of heads/tails on the next flip. We assume that the process is controlled by a probability distribution $$p^*(x)$$ where $$x \in \{h,t\}$$. Our class of models $$M$$ is going to be the set of all probability distributions over $$\{h,t\}$$.

How should we choose $$p$$ from $$M$$ if 60 out of 100 tosses are heads? Let's assume that $$p(x=h)=\theta$$ and $$p(x=t)=1−\theta$$. If our observed data is $$D = \{h,h,t,h,t\}$$, our likelihood becomes $$\prod_i p(x_i ) = \theta \cdot \theta \cdot (1 − \theta) \cdot \theta \cdot (1 − \theta)$$; maximizing this yields $$\theta = 60\%$$.

More generally, our log-likelihood function is simply

$$
L(\theta) = \text{# heads} \cdot \log(\theta) + \text{# tails} \cdot \log(1 − \theta),
$$

for which the optimal solution is

$$ \theta^* = \frac{\text{# heads}}{\text{# heads} + \text{# tails}}. $$

## Maximum likelihood learning in Bayesian networks

Let us now apply this long discussion to a particular problem of interest: parameter learning in Bayesian networks.

Suppose that we are given a Bayesian network $$p(x) = \prod^n_{i=1} \theta_{x_i \mid x_{pa(i)}}$$ and i.i.d. samples $$D=\{x^{(1)},x^{(2)},\ldots,x^{(m)}\}$$. What is the maximum likelihood estimate of the parameters (the CPDs)? The likelihood is

$$
L(\theta, D) = \prod_{i=1}^n \prod_{j=1}^m \theta_{x_i^{(j)} \mid x_{pa(i)}^{(j)}}.
$$

Taking logs and combining like terms, this becomes

$$
\log L(\theta, D) = \sum_{i=1}^n \sum_{x_{pa(i)}} \sum_{x_i} \#(x_i, x_{pa(i)}) \cdot \log \theta_{x_i \mid x_{pa(i)}}.
$$

Thus, maximization of the (log) likelihood function decomposes into separate maximizations for the local conditional distributions! This is essentially the same as the head/tails example we saw earlier (except with more categories). It's a simple calculus exercise to formally show that

$$ \theta^*_{x_i \mid x_{pa(i)}} = \frac{\#(x_i, x_{pa(i)})}{\#(x_{pa(i)})}. $$

We thus conclude that in Bayesian networks with discrete variables, the maximum-likelihood estimate has a closed-form solution. Even when the variables are not discrete, the task is equally simple: the log-factors are linearly separable, hence the log-likelihood reduces to estimating each of them separately. The simplicity of learning is one of the most convenient features of Bayesian networks.


<br/>

|[Index](../../) | [Previous](../../inference/variational) | [Next](../undirected)|
