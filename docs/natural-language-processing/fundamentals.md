# NLP Fundamentals
## Concepts
### Perplexity

Consider a test set $W = w_{1}w_{2}\ldots w_{n}$:

\begin{subequations}
\begin{align}
        \text{perplexity}(W) & = \probability{w_{1}w_{2}\ldots w_{n}}^{-\frac{1}{N}} \\
        & = \sqrt[N]{\frac{1}{\probability{w_{1}w_{2}\ldots w_{n}}}} \\ 
        & = \sqrt[N]{\prod_{i=1}^{N} \frac{1}{\probability{\condprob{w_i}{w_1\ldots w_{i-1}}}}}
\end{align}
\end{subequations}
Then we have the perplexity for a unigram~\eqref{eq:nlp-fundamentals-perplexity-unigram},
bigram~\eqref{eq:nlp-fundamentals-perplexity-bigram} language model (geometric mean of the unigram, bigram probabilities):
\begin{subequations}
    \begin{align}
        \label{eq:nlp-fundamentals-perplexity-unigram}
        \text{perplexity}(W) & = \sqrt[N]{\prod_{i=1}^{N} \frac{1}{\probability{w_i}}}\\
        \label{eq:nlp-fundamentals-perplexity-bigram}
        & = \sqrt[N]{\prod_{i=1}^{N} \frac{1}{\probability{\condprob{w_i}{w_{i-1}}}}}
    \end{align} 
\end{subequations}
Perplexity can be understood as the weighted average branching factor of a language. Minimizing perplexity is equivalent to maximizing the
test set probability according to the language model[[cite:jurafsky2000speech]]~\cite{jurafsky2000speech}.
