# React
React é uma biblioteca do Javascript para construir interfaces de usuário com Hooks e componentes.

## JSX
JS e HTML juntos:
```jsx
const element = <h1>Hello, world!</h1>;
```
Ao invés de separar o código por markdown e sintaxes adicionais além do JSX, o React tenta separar o código por SoC([[Separation of concerns]]) que cria unidades chamadas de "componentes".

Da para colocar expressões de Javascript dentro do HTML do JSX Usando chaves ex:
```jsx
const element = <h1>Hello, {name}</h1>;
```

JSX tambem faz o "escaping" de qualquer valor. Então é seguro colocar varios valores que são potencialmente inseguros dentro do DOM sem correr risco de XSS(cross-site-scripting, onde o usuário pode ter um problema de ataque por outro usuário do site por burlar o same-origin-policy)

## Elementos 
Elementos são imutaveis por padrão e você só pode trocar fazendo uma mudança dentro do elemento. Além disso, o react só muda o DOM quando necessário. 

## Componentes
A maneira mais simples de definir um componente é dentro de uma função utilizando *componentes funcionais* ex:
```jsx
function Welcome(props){
	return <h1> Hello World {props.name} </h1>
}
```
Todo componente funcional recebe `props` e retorna um componente.
**Convenção:** Sempre começar nome de elemento com letra maiuscula.

Todos componentes em react agem como funções puras.

## Eventos
Utiliza-se camelCase ao invés de lowercase no nome dos atributos referentes a eventos.
**Warning:** Tomar cuidado ao usar `this` em componentes utilizando Classes do ES6 porquê o resultado pode ser o indefinido.

## Renderização condicional
Só usar If, ternário ou `&&` por exemplo ex:
```jsx
{
	unreadMessages > 0 && 
	<h2> 
		Voce não leu as mensagens 
	</h2>
}
```

## Listas e chaves 
Da para utilizar o `map` para mapear diversos elementos para uma lista por exemplo:

```jsx
function NumberList(props) {
  const todoList = props.todo;
  const listItems = todoList.map((todo) =>
	<li key={todo.id}>{todo.number}</li>);
  return <ul>{listItems}</ul>;
}
```

Keys ajudam o react a detectar mudanças na lista. 

## Formulários

Componentes controlados por state fica mais facil do React ser "a unica fonte de verdade" do sistema. 
Ex:
```jsx
<select value={state} onChange={() => setState(!state)}>
```

Todo componente `read-only` é uncontrollable pelo react Ex: field de seleção de arquivo.

**Dica:** Formik é uma boa solução pra Forms.

## Pensando em React
1. Dividir responsabilidades dos componentes
	- Seguindo o Single responsability Principle
2. Montar uma versão estática
3. Pensar no minimo estado possivel para representação da UI
	- Só o necessário
4. Identificar onde os estados devem estar
	- Exemplo de lista de procura com search filtravel. Da pra armazenar o estado no componente pai para ficar tudo maisfacil
5. Data flow inverso
	- Basicamente pegar coisas do input e mandar pro componente pai via props