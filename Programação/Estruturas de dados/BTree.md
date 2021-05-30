# B tree
-  É uma [[Listas Encadeadas]] só que com "Páginas"
-  Paginas são arrays com varias listas encadeadas.
- Cada nó é chamado de página
- Cada nó armazena alguns $m$ chaves e $m-1$ nó filhos
- Cada nó filho menor fica a esquerda e maior a direita.
- A raiz é a unica que contem 1 chave.

# [[Big O]]
- Push O(log(n))
- Pop O(log(n))
- Search O(log(n))