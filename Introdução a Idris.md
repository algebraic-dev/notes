# Introdução
Idris é construido em cima da teoria de tipos intuistica de Martin Löf. Tem tipos simples como Nat e arrow types e tem tipos do System F_w_ que são tipos que dependem em tipos como os Sum types e os Product types.

## Tipagem dependente
Em simple typed lambda calculus, os valores e os tipos são ligados por um predicado mas tipos não são permitidos de depender de valores. Um sistema de tipos dependentes retira essa restrição.
- **Tipo dependente de produto:** Coleção de tipos $B: A \rightarrow U$ que para todo tipo $\alpha : A$ tenha um tipo $B(\alpha) : U$ onde U é o conjunto universo dos tipos.
	- Exemplo:
		$U = \{Type, Nat, List\ n, ....\}$
		Tipos de interesse: $A = \{List\ n\}$
		Então deve existir uma função: $B(n) = List\ n$
- **Tipo dependente de soma:** Coleção de tipos de pares indexados que o segundo elemento depende do primeiro. Ou seja, se tivermos $a: \alpha$ e $b :B(a)$ então isso é um tipo dependente de soma. Por exemplo, $\Sigma((x: Nat), List\ x)$ por exemplo (1, List 1)

## Teoria de tipos intuistica
É baseada em isomorfismo que proposições são iguais a tipos e programas são iguais a provas matemáticas. Com isso para matemática construtiva, para provar que que $4=4$ primeiramente tem que achar um objeto $x$ que tenha tipo $4=4$, ou seja, $x: 4=4$ e o unico objeto possivel é o $refl$ que pode ser pensado como um axioma de reflexibilidade. 

## Linguagem de programação Idris
Função simples em Idris
```haskell
succ1: Nat -> Nat
succ1 x = x + 1
```
