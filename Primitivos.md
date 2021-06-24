# Primitivos
`Int`, `Double`, `Integer`, `Char`, `String`, `Ptr`, `Bool` para dados e para funções arrow types tipo `Nat -> Nat`

```haskell
fib : Int -> Int
fib n =
	case n < 2 of
	True => n
	False => (fib (n - 1)) + (fib (n - 2))
```

```haskell
record Person where
    constructor MkPerson
    firstName, middleName, lastName : String
    age : Int
```
```haskell
record { a.b.c = val } x
```
```haskell
record SizedClass (size : Nat) where
    constructor SizedClassInfo
    students : Vect size Person
    className : String
```
```haskell
interface Eq a where
    (==) : a \-> a \-> Bool
    (/=) : a \-> a \-> Bool

    x /= y \= not (x \== y)
    x \== y \= not (x /= y)
```