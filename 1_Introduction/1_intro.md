---
title: | 
         CS 474/574 Machine Learning \
         1. HW1
author: |
          Ibne Farabi Shihab \
          Dept. of Computer Science \
          Iowa State University \
          Ames, IA, USA \
date:   \today
header-includes: |
     \usepackage{amssymb}
     \usefonttheme[onlymath]{serif}
---

# Warm up.

- the first one is Newton's first law of motion,
- the second one is Einstein's mass-energy equation, and
- the last one is the time complexity of Quicksort on average in Big-O notation

# Why ML is attractive

- We are lazy. We want to shift the heavy lifting to the computers. 
- We are incompetent. No kidding! Sometimes it is very difficult to come up with step-by-step instructions. 
- Examples: Self-driving, AlphaGo, Automated circuit routing, Machine translation, Commonsense reasoning, text entailment, Document generation, auto-reply of messages/emails, [fly a helicoper inversely](https://www.youtube.com/watch?v=M-QUkgk3HyE), [van-Gogh-lize paints](https://blogs.nvidia.com/blog/2016/05/25/deep-learning-paints-videos/). 
- It is a dream. "Creating an artificial being has been the dream since the beginning of science." -- Movie A.I., Spielberg et al., 2001

# Three types of MLs

ML (in current approaches) is about finding/approximating functions. 

- Supervised, finding $\hat{f}(x) \approx f(x)$ with ground truth provided by human. 
    * Let $x$ and $y$ be two (vectors of) variables, and a function connecting them $y = f(x)$ But only god knows $f$. 
    * We construct another function $\hat{f}$ to approximate $f$ such that $\hat{y} = \hat{f}(x) \approx y = f(x)$ for a(ny) given $x$. 
    * **Supervised** because we  provide many pairs of $x$'s and $y$'s for the computer to know the difference between $\hat{y}$ and $y$ on a large pool of samples. 
    * Examples: object detection from images, [Flavia](http://flavia.sourceforge.net/), [CPU branch prediction](https://www.electronicdesign.com/technologies/microprocessors/article/21802106/ai-helps-amds-ryzen-take-on-intel),  [COVID-19 diagnosis from blood profile](https://arxiv.org/abs/2005.06546), [Epileptic EEG recognition](https://www.technologyreview.com/2009/04/29/213440/a-neural-net-that-diagnoses-epilepsy/), [depression treatment from brain shapes](https://mfr.osf.io/render?url=https://osf.io/b58jr/?action=download%26mode=render).
    * Beyond categorization/classification: [Mflux](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004838), [Review helpfulness prediction](https://www.aclweb.org/anthology/P15-2007.pdf), [Document summarization](https://www.aclweb.org/anthology/E17-2112.pdf), predict house prices
- Unsupervised, finding $\hat{f}(x)$ without ground truth
- Reinforcement, let the machine find ground truth itself

# Representation of $x$

- $x$ is usually not a simple (vector of) number(s). How to tell it to a computer? 
- Example: bananas vs. apples
- **Feature engineering**: manually craft functions to **extract** features from raw data, e.g,. SIFT, bag-of-words. 
- Automated feature extraction in deep learing: E.g., filters in CNNs. 
- If $x$ involves categorical values (e.g., gender), there are usually two approaches: [**One-hot encoding**](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html) and [**embedding**]() (in DL context, to be discussed later). 

# Supervised ML
- Given many pairs of inputs and outputs: $\{(\mathbf{X_1, y_1}), (\mathbf{X_2, y_2}), \dots, (\mathbf{X_N, y_N})\}$, 
- that underline a "black-box" function $f:\mathbb{R}^n \mapsto \mathbb{R}^m$ such that $\forall i \in [1..n], f(\mathbf{X}_i)=\mathbf{y}_i$, 
- construct a function $\hat{f}$ that approximates the function $f$. 
- "approximate": usually $\min || \hat{f}(x) - f(x)||^{p}$ where $p$ is usually 1 or 2. [See $\ell_p$-norm](https://en.wikipedia.org/wiki/Norm_(mathematics)) . 
<!-- - In other words, $f$ is a black box. And we need to find $\hat{f}$ that mimick the black box.  -->
- The process of finding the approximation function $\hat{f}$ is called **training** or **learning**. 
 - $\hat{f}$ is called a **model** or an **estimator**. 
- $\mathbf{X_i}$: an **input** (especially when raw data is used as the input) or **feature vector** (if using feature engineering). 
- $\mathbf{y_i}$, often $\in \mathbb{R}^1$ a **label** (in classification) or **target** (used more generally and lately). 
- Classification vs. Regression: When $y$ is continuous or discrete. In modern DL context, such division is usually no mentioned, expecially in generative tasks. 
