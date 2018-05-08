# Review for the CS220 POPL Final

## A Few Basic Problems

### Regular Expressions (REGEX)

--Write a regex for string literals in Clojure.

```
Call $ all characters except " and \
REGEX: "( $ | \(n|t|r|\|") )*"
```

--Ex: Write a regex for class names in C++

Look up refresher on things like class names, variable names, etc in these languages.

### Context Free Grammars

`Func --> (defn VarName \n [params] \n Exprs)`

`VarName --> Legal var syntax`

`Params --> Emptystring | VarName Params`

`Exprs --> Expr | Expr \n Expr`		`Exprs means expressions`

`Expr --> (VarName Args)`

`Args --> Emptystring | VarName Args | literal Args | Expr Args`

![Image result for context free grammar](https://ds055uzetaobb.cloudfront.net/image_optimizer/a0648361f5053c1252b4cef08943b357d9b35c6b.png) Something like this.



### Type Systems

Three main dichotomies

Static vs Dynamic typing	--> typechecking: static is at compile time, dynamic is at run time

Strongly vs Weakly typed	--> language either prohibits or allows calling things on unsupported objects

Declared vs Inferred type	--> stating the type of declared vars, or if the program infers it



RUBY:		Strong		Inferred		Dynamic 	--> super duck typed\*\*

CLOJURE:	Strong		Inferred		Dynamic 	--> no typechecking messages until runtime

HASKELL:	Strong		Both		Static		--> compiler catches a lot

PROLOG:	Strong?*	Inferred		Dynamic	--> compiler doesn't catch errors until called



\*Prolog has atoms, integers/numbers, variables, and complex terms (functors)

​	-- However, it will yell at you if you try to add two atoms together

\*\*Duck Typing: if two things have the same methods, you can treat them like the same type even if they aren't



### I/O in Functional Languages

--Write a function that gets a string from the user and returns the string concatenated with itself.

```haskell
--concatWithSelf :: [a] -> [a]
concatWithSelf x = x ++ x		-- ++ concats any type of list, including strings

doesIO :: IO String
doesIO = do				-- don't need "main" unless it is called from runhaskell
	input <- getLine
	return $ concatWithSelf input	--return takes an X and makes it an IO X
```

```clojure
(defn concatWithSelf
	"gets user input, returns it concatenated with itself"
	[]
	(let [X (read-line)]
	(println (str X X))))
```

