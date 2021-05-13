# Lógica de primeira ordem
É um sistema de lógica formal que usa Qualificadores([[Lógica de primeira ordem]]) e permite o uso de sentenças que tem variáveis. E é fundamentado pela [[Lógica proposicional]]. Além disso introduz o conceito de  **predicado** que é a formalização de uma *declaração* que pode ser entendida como uma afirmação verdadeira ou falsa. Pode ser definido pela função $x \mapsto B$
## Quantificadores
Para todos: $\forall$ que o inverso pode ser $\exists$. $x: \forall x, P(x)$ sendo $P(x)$ um predicado que abstrai sobre uma proposição como por exemplo: $P(x) = x\ é\ filosofo$

### Negação de quantificadores
Para todos: $\lnot(\forall x, P(x)) = \exists x, \lnot P(x)$
Por exemplo: `Nem todos são filosofos` de forma não negada seria `Existe pelo menos uma pessoa que não é filosofo`

Existe pelo menos um: $\lnot(\exists x, P(x)) = \forall x, \lnot P(x)$
Por exemplo: `Não(existe pelo menos um filosofo)` com quantificador não negado é`Todos não são filosofos`