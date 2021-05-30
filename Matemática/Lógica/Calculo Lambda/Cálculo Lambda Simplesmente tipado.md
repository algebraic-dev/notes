# Cálculo Lambda Tipado

- Extensão do [[Calculo Lambda Não Tipado]]
- Tipos são dominios ou coleções, sempre tratamos dados desse jeito por que é mais facil distinguir.
- Tipos são Right-associative e Aplicações são Left-associative
- Termos são tipados se existe um $\sigma$ que $t : \sigma$ onde t é chamado de *sujeito* e t de *tipo* 

### Tipos simples:
O conjunto $V$ é infinito e contem todos as variáveis tipo e
o conjunto dos tipos simples $T$ pode ser definido por:
1. Tipo da variavel: Se $\alpha \in V$, então $\alpha \in T$
2. Tipo 'flecha': Se $\sigma, \tau \in T$, então $(\sigma \rightarrow \tau) \in T$
- Tipos variáveis são abstrações representadas por tipos básicos como o tipo dos Naturais
- Tipos flecha são tipos de funções como $Nat \rightarrow Real$ 

## Tipagem:
- Afirmação de tipos (Statements) são um recurso da linguagem formal para declarar os tipos de valores. exemplo $x : \Omega$
- Declaração é uma afirmaçaõ com a variavel sendo sujeito
- Um contexto é uma lista de declarações com diferentes sujeitos
- Um Julgamento está na forma $\Gamma \vdash M : \sigma$ onde $\Gamma$ é o contexto e $M : \sigma$ é a afirmação
$$\frac{premissa1\ premissa2}{conclusao}$$

### Regras de derivação
1. $\text{(Var)} \Gamma \vdash x: \sigma$ if $x : \sigma \in \Gamma$

2. $\text{(App)} \dfrac{\Gamma \vdash M : \sigma \rightarrow t, \Gamma \vdash N: \sigma}{\Gamma \vdash M N : t}$

3. $\text{(Abs)} \dfrac{\Gamma,x: \sigma \vdash M: t}{\Gamma \vdash (\lambda x : \sigma. M) : \sigma \rightarrow t}$

## Termos $\lambda \rightarrow$ legais
Um termo lambda tipado M é considerado legal  se existe um contexto $\Gamma$ com tipo p que $\Gamma \vdash M: p$

## Dominio e Permutação
- No contexto $\Gamma \vdash x_0: \sigma_0, x_1: \sigma_1 ... x_n: \sigma_n$, então o dominio de $\Gamma$ é $(x_0, x_1, ... x_n)$
- O contexto $\Gamma'$ é um sub-contexto do contexto $\Gamma$ se $\Gamma' \subseteq \Gamma$ se todas declarações em $\Gamma'$ estão contidas em $\Gamma$ na mesma ordem
- O contexto $\Gamma'$ é uma permutação de $\Gamma$ se todas declarações nos 2 são iguais e na mesma ordem
- Dado o contexto $\Gamma$ e o conjunto de variáveis $\Phi$ a projeção de  $\Gamma$ em $\Phi$ é o sub contexto  $\Gamma'$
## Thinning,  Condensação e permutação
1. Thinning: Se $\Gamma'$ é uma permutação de $\Gamma''$ e $\Gamma' \vdash M : \sigma$ então $\Gamma'' \vdash M: \sigma$. Ser thinner é ser um contexto com mais variáveis sujeito do que o contexto original. (???) é o inverso do subcontext basicamente. 
2. Condensação: Se o $\Gamma \vdash M: \sigma$ então a projeção do contexto $\Gamma \upharpoonleft FV(M) \vdash M: \sigma$. Ou seja, nesse lema, podemos condensar o contexto(proposições) de tipagem usando somente as proposições que importam(as que são projeção com as free variables)

## Consequencias
Tipos são unicos ou seja o problema do self-referential é resolvido. $M M$ é um termo lambda legal caso exista um contexto $\Gamma$ com tipo p que $M M$ tenha tipo $\sigma$. Por exemplo, $M$ tem que ter tipo $\Gamma \vdash M: \sigma \rightarrow t$ e  $\Gamma \vdash M: \sigma$. Seguindo pelo Lema de Singularidade dos Tipos, é impossivel $\sigma \rightarrow t \equiv \sigma$.