# Cálculo Lambda Tipado

- Extensão do [[Calculo Lambda Não Tipado]]
- Tipos são dominios ou coleções, sempre tratamos dados desse jeito por que é mais facil distinguir.
- Tipos são Right-associative e Aplicações são Left-associative

### Tipos simples:
O conjunto $V$ é infinito e contem todos as variáveis tipo e
o conjunto dos tipos simples $T$ pode ser definido por:
1. Tipo da variavel: Se $\alpha \in V$, então $\alpha \in T$
2. Tipo 'flecha': Se $\sigma, \tau \in T$, então $(\sigma \rightarrow \tau) \in T$
- Tipos variáveis são abstrações representadas por tipos básicos como o tipo dos Naturais
- Tipos flecha são tipos de funções como $Nat \rightarrow Real$ 
- Afirmação de tipos (Statements) são um recurso da linguagem formal para declarar os tipos de valores.
- Declaração é uma afirmaçaõ com a variavel sendo sujeito
- Um contexto é uma lista de declarações com diferentes sujeitos
- Um Julgamento está na forma $\Gamma \vdash M : \sigma$ onde $\Gamma$ é o contexto e $M : \sigma$ é a afirmação
$$\frac{premissa1\ premissa2}{conclusao}$$