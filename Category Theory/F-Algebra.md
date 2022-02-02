# F-Algebra
Algebras abstracts the idea of perform calculations on numbers and symbols. Lets define a type called `ExprF`.
```haskell
data ExprF a 
	= Const Int
	| Add a a
	| Mul a a
```
We can express the recursion using `Fix` in the place of `a` so we can have something like `ExprF (Fix ExprF)` to express the same thing as something like `Expr`.  So `ExprF` itself is a functor and we can eval it using map (kinda a strange approuch). 	
## In category theory
In category theory if consists of 
1. An endofunctor F in a [[Category]] C
2. An object A in that category
3. A morphism from F(A) to A

So a F-Algebra is defined by a functor `f`, a carrier type `a`and a function from `f a` to `a`. The category C is the Category [[Hask]], the `f` is the Functor and `a` is the type.

## A initial algebra
There's only one homomorphism  from it to any algebra 