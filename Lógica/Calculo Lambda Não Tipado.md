# Cálculo λ não tipado
Pagina 9 do capitulo 1

### Tres piláres
*Variáveis*: `X` são conceitos abstratos
*Abstração* :  `λx . x²+1` A função mapeia x para x²+1
*Aplicação* :   `(λx . x²+1) 3` 

### Redução e Conversão
*redução β*: Substituição definido normalmente por `M[x := N]` que significa "M em que N foi substituido por x"

### Elementos
*$‘M \equiv N’$* : Significa que o termo  λ M e N são identicos

### Variaveis livres e vinculadas
Em `λx . M` A abstração de x em M (Função x.m) vincula todas as ocorrencias de x em M e então M é considerado uma variavel vinculante.

### [[Multi Conjunto]] dos sub-termos
- Base: Sub(x) = {x} 
- Application: Sub((M N)) = Sub(M) U Sub(N) U {(M N)}
- Abstraction: Sub((λx. M)) = Sub(M) U {(λx. M)}
- Reflexividade:  ∀M, M ∈ Sub(M).
- Transitividade: *Se* L ∈ Sub(M), M ∈ Sub(N) *então* L ∈ Sub(N)

### [[Multi Conjunto]] das variaveis livres
- Base: FV(x) = {x}
- Application: FV((M N)) = FV(M) U FV(N)
- Abstraction: FV((λx. M)) = FV(M) \ {x}

Termos λ fechados (Closed λ-Terms) = $FV(M) = \emptyset$

### Conversão $\alpha$
Nomes não são essenciais então podemos renomea-los para impedir ambiguidade ou cálculo incorreto.
-Condições em $\lambda y. M^{x \rightarrow y}$:
	- $y \not\in FV(M)$ se existesse uma variável livre y em M então y se vincularia a expressão. Então essa condição é necessária pra não causar mudança semântica.
   - y não é uma variável vinculante por exemplo se fosse, ocorreria um problema assim: $$\lambda x.M \equiv \lambda x.\lambda y. x\ \rightarrow\ \lambda y. M^{x \rightarrow y} \equiv \lambda y.\lambda y. y$$

### Equivalencia $\alpha$
se $M =_a N$, então, M e N tem estruturas correspondentes, com as variáveis livres tendo mesmo nome e as variáveis vinculadas e vinculantes tendo nomes correspondentes

### Redução $\beta$
1. Base - $(\lambda x.M) N \rightarrow M[x := N]$
2. Compatibilidade - Se $M \rightarrow N$ então $ML \ \rightarrow NL$
Exemplo de uma redução de 1 passo:

$$((\lambda x. M) N) \rightarrow _\beta (M[x := N])$$

Um redex(reducible expression) é uma expressão que pode ser aplicada intermediariamente por exemplo: $(\lambda y.y)z$ que pode virar $(y[y:=z])$

### Convenção de Barendregt 
"Nós escolhemos os nomes das variáveis vinculantes em um termo lambda de uma maneira que eles são todos diferentes, e que cada um deles seja diferente de todas a variáveis livres que ocorrem em um termo" Por exemplo, $(\lambda xy.xz)(\lambda xz.z)$ está incorreto e devemos utilizar $(\lambda xy.xz)(\lambda uv.v)$.

### Normalização $\beta$
1. M é numa forma beta se M não contem nenhum redex
2. M tem uma forma beta se existe N em $\beta$-nf em que $M=_\beta N$ e que N está numa $\beta$-nf de M
Obs: se não tem forma intermediaria então não há mais calculos, ou seja, está em $\beta$-nf

### Combinador de ponto fixo ( Recursão )
$$Y \equiv \lambda y.(\lambda x. y(xx))(\lambda x. y(xx)).$$

Existe um  termo-$\lambda$ M cujo $M x =_b xMx$?
Primeiro definimos $L := (\lambda x.xyz)$, Então $LM \rightarrow _b \lambda x. xMx$. Se conseguirmos $M =_b LM$, então acabou. $YL =_\beta L(YL)$ então end.
