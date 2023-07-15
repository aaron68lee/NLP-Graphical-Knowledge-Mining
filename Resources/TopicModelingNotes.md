# Blei, David M. “Probabilistic Topic Models.” Communications of the ACM 55, no. 4 (April 2012): 77–84. https://doi.org/10.1145/2133806.2133826.

## Key Points

- "Topic models are algorithms [using statistical methods] for discovering the main themes that pervade a large and otherwise unstructured collection of documents. Topic models can organize the collection according to the discovered themes." (77)
    
- They don't require any prior labeling
    
- **Latent Dirichlet Allocation (LDA): "**The intuition behind LDA is that documents exhibit multiple topics. ... [It] is a statistical model of document collections that tries to capture this intuition." (78)  
    
    - "The distinguishing characteristic of latent Dirichlet allocation [is that] all the documents in the collection share the same set of topics, but each document exhibits those topics in different proportion." (79)
        
    - "The documents themselves are observed, while the topic structure - the topics, per-document per-word topic assignments - is *hidden structure*. The central computational problem for topic modeling is to use the observed documents to infer the hidden topic structure. This can be thought of as 'reversing' the generative process - what is the hidden structure that likely generated the observed collection?" (79)
        
    - "The utility of topic models stems from the property that the inferred hidden structure resembles the thematic structure of the collection." (79)
        
- **Topic**: is a distribution over [of] a fixed vocabulary. The words in each topic are generated through a two-stage process that reflects the intuition of LDA because "each document exhibits the topics in different proportion (step #1); each word in each document is drawn from one of the topics (step #2b), where the selected topic is chosen from the per-document distribution over topics (step #2a):
    
    1. Randomly choose a distribution over [of] topics
        
    2. For each word in the document: (a) randomly choose a topic from the distribution over topics in step #1. (b) randomly choose a word from the corresponding distribution over the vocabulary.
        

### Mathematical Description:

We can describe LDA more formally with the following notation. The topics are b1:K, where each bk is a distribution over the vocabulary (the distributions over words at left in Figure 1). The topic proportions for the dth document are qd, where qd,k is the topic proportion for topic k in document d (the cartoon histogram in Figure 1). The topic assignments for the dth document are zd, where zd,n is the topic assignment for the nth word in document d (the colored coin in Figure 1). Finally, the observed words for document d are wd, where wd,n is the nth word in document d, which is an element from the fixed vocabulary. With this notation, the generative process for LDA corresponds to the following joint distribution of the hidden and observed variables,

Notice that this distribution specifies a number of dependencies. For example, the topic assignment zd,n depends on the per-document topic proportions qd. As another example, the observed word wd,n depends on the topic assignment zd,n and all of the topics b1:K. (Operationally, that term is defined by looking up as to which topic zd,n refers to and looking up the probability of the word wd,n within that topic.) **These dependencies define LDA**. They are encoded in the statistical assumptions behind the generative process, in the particular mathematical form of the joint distribution, and—in a third way—in the probabilistic graphical model for LDA.

#### Assumptions:

- "One assumption that LDA makes is the “bag of words” assumption, that the order of the words in the document does not matter. (To see this, note that the joint distribution of Equation 1 remains invariant to permutation of the words of the documents.)" (82)
    
- "Another assumption is that the order of documents does not matter." (82)
    
    - **Problematic when dealing with documents that span longer timer frames.** "One approach to this problem is the dynamic topic model—a model that respects the ordering of the documents and gives a richer posterior topical structure than LDA." (82) **Dynamic models allow us to analyze how topics change over time.**
        
- "the number of topics is assumed known and fixed." (82-3)
    
    - "The Bayesian non-parametric topic model provides an elegant solution: the number of topics is determined by the collection during posterior inference, and furthermore, new documents can exhibit previously unseen topics. **Bayesian nonparametric topic models have been extended to hierarchies of topics, which find a tree of topics, moving from more general to more concrete, whose particular structure is inferred from the data**." (83)
        

### Research in Topic Modeling:

- "one of the main advantages of formulating LDA as a probabilistic model is that it can easily be used as a module in more complicated models for more complicated goals. Since its introduction, LDA has been extended and adapted in many ways." (82)
    
- "The correlated topic model and pachinko allocation machine allow the occurrence of topics to exhibit correlation (for example, a document about geology is more likely to also be about chemistry than it is to be about sports); the spherical topic model allows words to be unlikely in a topic (for example, “wrench” will be particularly unlikely in a topic about cats); sparse topic models enforce further structure in the topic distributions; and “bursty” topic models provide a more realistic model of word counts." (83)
    
- Incorporating metdata, such as the author-topic model: "The topic proportions are attached to authors; papers with multiple authors are assumed to attach each word to an author, drawn from a topic drawn from his or her topic proportions. The author-topic model allows for inferences about authors as well as documents." (83)
    
- Relational topic model

----------------------------------------------------------------------

# Blei, David M. “Topic Modeling and Digital Humanities.” Journal of Digital Humanities 2, no. 1 (Winter 2012). http://journalofdigitalhumanities.org/2-1/topic-modeling-and-digital-humanities-by-david-m-blei/.


## Key Points

- "A topic model takes a collection of texts as input. It discovers a set of ‘topics’ - recurring themes that are discussed in the collection - and the degree to which each document exhibits those topics. … Formally, a topic is a probability distribution over terms. In each topic, different sets of terms have high probability, and we typically visualize the topics by listing those sets. … [T]opic models find the sets of terms that tend to occur together in texts. They look like ‘topics’ because terms that frequently occur together tend to be about the same subject."
    
- "In particular, LDA is a type of probabilistic model with hidden variables. Viewed in this context, LDA specifies a *generative* *process*, an imaginary probabilistic recipe that produces both the hidden topic structure and the observed words of the texts. Topic modeling algorithms perform what is called *probabilistic inference*. Given a collection of texts, they reverse the imaginary generative process to answer the question ‘What is the likely hidden topical structure that generated my observed documents?'"
    
- The generative process for LDA is as follows.
    

    1. choose the topics, each one from a distribution over distributions.
        
    2. Then, for each document, choose topic weights to describe which topics that document is about.
        
    3. Finally, for each word in each document, choose a topic assignment -- a pointer to one of the topics -- from those topic weights and then choose an observed word from the corresponding topic. Each time the model generates a new document it chooses new topic weights, but the topics themselves are chosen once for the whole collection."
        

- "The simplest topic model is latent Dirichlet allocation (LDA), which is a probabilistic model of texts. Loosely, it makes two assumptions:
    
    - There are a fixed number of patterns of word use, groups of terms that tend to occur together in documents. Call them *topics*.
        
    - Each document in the corpus exhibits the topics to varying degree."
        
- "these analyses require that we know the topics and which topics each document is about. Topic modeling algorithms uncover this structure. They analyze the texts to find a set of topics - patterns of tightly co-occurring terms -- and how each document combines them."

