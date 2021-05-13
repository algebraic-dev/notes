# Lógica proposicional
É um sistema de lógica formal que utiliza *proposições* e a relação entre elas utilizando conectores lógicos. Tambem é chamada de Lógica de grau zero.
## Três principios
- Principio da não contradição: Não pode ser falso e verdadeiro ao mesmo tempo
- Principio do terceiro excluido: Não existe outra probabilidade a não ser Falso e Verdadeiro
- Principio da identidade: Para todo A, A é A

---

## Operadores lógicos
- **E**: $\land$ = Conjunção

- **Disjunção**: $\lor$ =  
	- **Disjunção inclusiva:** True e True é True 
	- **Disjunção exclusiva  $\oplus$ :** True e True é False (XOR) 
- **Não**: $\lnot$ = Negação
	- **De re**: Da coisa "O maior numero primo **não** é par" (Proposição com objeto negado). Nos comprometemos com a existência do maior numero primo em De re
	- **De dicto**: Da proposição "**Não é o caso que** o maior numero primo é par". Em De Dicto não nos comprometemos com a exitencia do maior numero primo.

- **Implicação**: $\implies$ = no caso de $a \implies b$ A implica em B, então, caso A seja verdadeiro e B verdadeiro, A falso e B falso ou somente B verdadeiro, a implicação é verdadeira porque podemos penasr a implicação como uma "promessa" que somente é invalida se quebrada. Ou seja, Se A é verdadeiro e B é falso quebramos a "promessa", porém, se B é verdadeiro e A é falso a "promessa" não foi quebrada.
	- Elementos:
		- **Antecedente** - Vem antes da seta
		- **Consequente** - Vem depois da seta 
	- **Tautologia**: Verdade lógica
	- **Causalidade**: Entre antecedente e consequente
	- **Implicação semântica**: `Fulano é casad*o* então ele é homem`

- **Bicondicional**: $\leftrightarrow$ = Caso os dois sejam verdadeiros ou caso os dois sejam falsos a bicondicional é verdadeira.
	-  $P \leftrightarrow Q \equiv \lnot(P \oplus Q)$ 
- **Sheffer's Stroke / Nand:**  $P|Q$ Um dos dois é falso 

## Interconversão de operadores

1. $P \leftrightarrow Q \equiv \lnot (P \oplus Q)$ 
2. $\lnot (P \oplus Q) \equiv (P \lor Q) \land \lnot (P \land Q)$
3. $P \implies Q \equiv \lnot (P \land \lnot Q)$
4. $P \land Q \equiv \lnot (\lnot P \lor \lnot Q)$
5. $P|P \equiv \lnot P$
6. $P | Q \equiv \lnot (P \land Q)$
7. $\lnot (P | Q) \equiv \lnot \lnot(P \land Q)$


## Teorema da expressividade maxima

é possivel ter 16 operadores verofuncionais no máximo porém da pra definir todos os operadores usando 5 operadores. 

---

## Tautologia, contigência e contradição

- *Tautologia:* Só é uma tautologia se todas as interpretações de uma formula é verdadeira ex: $P \lor \lnot P$
- *Contradiçao*: Só é uma contradição se todas interpretadores de uma formula são falsas ex: $P \land \lnot P$
- *Contingência*: Pelo menos um verdadeiro e um falso $P \implies Q$
