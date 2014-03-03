---
title:  'Scholarly Markdown: a Markdown-compatible format for academic communication'
author:
- name: First Author
  affiliation: Technical U
- name: Second Author
  affiliation: U of Technical
tags: [test, markdown, scholarly]
date: January 1, 2000
---

## Scholarly Markdown math support

### Math as (fenced) code blocks

This is a line of text with a `simple code block` in it.

`` `this should be just a `normal` inline code block
surrounded by literal backticks` ``

This is another line of text. Here should be some math: ``\mathbf{F = ma}<2\mathbf{ma}``. There should be some displaymath environment on the following line

```math
    \mathbf{F = ma} < 2\mathbf{ma}
```

and there should be no line breaks between the displaymath block and here. **This should be bold**. *This should be italic.*

The following is a displaymath with an aligned environment in a separate paragraph (preceded with, and followed by, two blank lines), with identifier `matheqn1`. It should automatically be wrapped with the `aligned` environment.


```math {#matheqn1}
    \mbox{minimize}\quad & f(x) = \max_{i=1,\ldots,m} (a_i^T x + b_i) \\
    & \|x\|_2 \le \sigma.
```


Here is an implicit align math environment consisting of multiple lines of equations with no newline in between, with at least one `&` symbol in the whole expression. It should be in the same paragraph as this one.

```math
      \sum_{j_1, j_2, \ldots j_m} \sum_{k_1, k_2, \ldots, k_m} & \widetilde{A}_{j_1,k_1}^{\ast} \widetilde{A}_{j_1,k_2} \tilde{A}_{j_2,k_2}^{\ast} \widetilde{A}_{j_2,k_3}  \ldots \widetilde{A}_{j_m,k_m}^{\ast} \widetilde{A}_{j_m,k_1}
```  
```math #middleAlignMathNumber
     =   \sum_{j_1, j_2, \ldots j_m} \sum_{k_1, k_2, \ldots, k_m} & \left(  R_{\Lambda} T_{k_1}^{\ast} P_{\Omega} T_{j_1} R_{\Lambda}^{\ast} \right) \left(  R_{\Lambda} T_{j_1}^{\ast} P_{\Omega} T_{k_2} R_{\Lambda}^{\ast} \right)   \left(  R_{\Lambda} T_{k_2}^{\ast} P_{\Omega} T_{j_2} R_{\Lambda}^{\ast} \right)
```
```math
     & \left(  R_{\Lambda} T_{j_2}^{\ast} P_{\Omega} T_{k_3} R_{\Lambda}^{\ast} \right) \ldots \left(  R_{\Lambda} T_{k_m}^{\ast} P_{\Omega} T_{j_m} R_{\Lambda}^{\ast} \right) \left(  R_{\Lambda} T_{j_m}^{\ast} P_{\Omega} T_{k_1} R_{\Lambda}^{\ast} \right).
```

And here is an implicit gather math environment consisting of multiple lines of equations with no newline in between, with no `&` symbol appearing anywhere:

```math
    \left.\begin{aligned}
    B'&=-\partial\times E\\
    E'&=\partial\times B - 4\pi j
    \end{aligned}
    \right\} \quad \text{Maxwell's equations}
```
```math {#firstGatherMathNumber}
A = B
```
```math
AAAAAAA = BBBBBB
```


Single math equations that have line-breaks (the `\\` command) are automatically wrapped in a `split` environment. If alignment commands (symbol `&`) also exist, they get wrapped in an `aligned` environment instead. This behaviour can be disabled using the `math_plain` environment:

```math
y = ax \\
f = kg^{-1}
```

```math
y &= ax \\
f &= kg^{-1}
```

```math_plain
y &= ax \\
f &= kg^{-1}
```

The following has an ampersand and line breaks in comma, but is actually a single-line equation that should be untouched:

```math
|y|\ \&\ |x| % an & and \\ that should be ignored
= 99\% z    % an & and \\ that should be ignored
```


Here are two proposed internal link to the previous math equations.

Referencing using the `\ref` tag: Equation [#matheqn1].

Referencing using the `\eqref` tag: Equation (#middleAlignMathNumber).

Below is more internal vertical alignment tests. The first is one that uses `cases` internally:
```math
#matheqn2
    P_{r-j}=\begin{cases}
    0& \text{if $r-j$ is odd},\\
    r!\,(-1)^{(r-j)/2}& \text{if $r-j$ is even},
    \end{cases}
```
and another one that uses `aligned` internally.
```math #matheqn3
    \left.\begin{aligned}
    B'&=-\partial\times E\\
    E'&=\partial\times B - 4\pi j
    \end{aligned}
    \right\}
    \qquad \text{Maxwell's equations}
```

### Math and lists

Here's a list with both inline and display math environments:

- Item 1
- Item 2 with a `code block` and ``\mathsf{\text{inline math}}`` with equation ``\mathbf{y=Ax}``
- Item 3
    - Indented item 4
    - Indented item 5, followed by display math, which cannot be indented:
```math
\mathbf{F_1 = m_1a}
```
      with some text below
    - Indented item 6, which does not recognize list-item display math surrounded by one additional blank line:

```math
\mathbf{F_2 = m_2a}
```

      without breaking this text out of the list and into a pre block
- Item 4
    1. Numerical Item 1
    2. Numerical item 2 

## Figures