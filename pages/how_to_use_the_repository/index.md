---
layout: main
title: How to use the attacks repository
order: 1
class: deployments-registry
permalink: /how-to-use-the-attacks-repository
---

## How to use the repository

The information associated with each paper follows the format:

- **A. URL**
- **B. BibTeX entry**
- **C. Authors**
- **D. Title**
- **E. Short description**
- **F. Type of data (inputs)**
- **G. Type of data release (outputs)**
- **H. Threat model — attacker objectives**
- **I. Threat model — attacker capabilities**
- **J. Research type**
- **K. Link to artifacts**
- **L. Additional comments**
- **M. Submitter information**

Columns A--D and J--M we believe are fairly standard. Columns F--I are more structured and rely on specialized terminology associated with the research on privacy attacks. For users who are just getting started with this literature, we give a quick introduction to the terminology and links to resources for further reading.

### Type of data (inputs)

- **Tabular**: Data laid out in a traditional table with one axis (typically rows) representing different data points and another axis (typically columns) representing different features. In these datasets we often think of each individual person’s data as corresponding to a single row of the table.
- **Image**: Data composed of pixels arranged in a 2D (or 3D for color images) grid. Each image is typically represented by numerical pixel intensity values across channels (e.g., RGB). Typical image datasets might look like ImageNet and CIFAR-10.
- **Text**: Data composed of sequences of characters or tokens (e.g., words, subwords). Typically represented numerically using embeddings or tokenized integers.

### Type of data release (outputs)

- **Counts and linear queries**: A count query has the form “How many elements of this dataset are voting-age, Hispanic, males living in Massachusetts?” In the literature these are often called linear queries for technical reasons. These queries are most commonly associated with tabular datasets and applications such as the US Decennial Census, but are well defined for other types of data.
- **Predictive models**: Predictive models map input features to target outputs and are trained on labeled data. They are typically used to predict unknown or future values based on historical data. Examples include:
  - Simple predictive models (e.g., linear regression)
  - Neural networks (deep learning models)
- **Generative models**: Produce new synthetic data points (e.g., text, images, audio) that resemble the training data distribution. LLMs (e.g., GPT), diffusion models for images (e.g., Stable Diffusion), and generative adversarial networks (GANs) are typical examples.

### Threat model — attacker objectives

Describes what constitutes “success” for the attacker, typically by specifying some piece of information that is unknown to the attacker and a criterion for recovering that information sufficiently well. While there are some variations in how each attacker objective is defined, and sometimes different threat models can blur together at the boundaries, the basic categories are:

- **Data reconstruction**
- **Membership inference**
- **Data extraction**
- **Attribute inference**

### Threat model — attacker capabilities

This describes the particular capabilities that we assume the attacker needs to run the attack successfully. These capabilities often take the form of some kind of background knowledge about any or all of (1) the distribution the data was drawn from as well as the specific dataset, and (2) the particulars of the algorithm producing the release and how the attacker can interact with that release. Some examples include:

- Issue adaptive queries to the privacy mechanism
- Insert poisoned examples into the training data
- …

This information is much less structured, and often the ways research papers differ in attacker capabilities is highly specific to the data type, release type, and attacker objective. As a result, we left the column free-text.   
