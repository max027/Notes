# Phases of compiler 
1. lexical analysis(Scanning)
2. Syntax analysis(Parsing)
3. Intermediate representations
4. Optimization
5. Code generation

## Types of compiler
1. Single-pass compiler
2. Tree walking interpreter
3. Transpilers
4. Just-in-time compiler

# compiler and interpreter
* Compiling is an implementation technique that involves translating a source language to some other—usually lower-level—form. When you generate bytecode or machine code, you are compiling. When you transpile to another high-level language, you are compiling too.
* When we say a language implementation “is a compiler”, we mean it translates source code to some other form but doesn’t execute it. The user has to take the resulting output and run it themselves.
* Conversely, when we say an implementation “is an interpreter”, we mean it takes in source code and executes it immediately. It runs programs “from source”.

# Language processors
Simply stated, a compiler is a program that can read a program in one language - the source language  and translate it into an equivalent program in another language  the target language.
An interpreter is another common kind of language processor. Instead of producing a target program as a translation, an interpreter appears to directly execute the operations specied in the source program on inputs supplied by the user,

## A language processing system
```text
            source-program
                |
            Preprocessor
                |
            modified source-program
                |
            compiler
                |
            target assembly program
                |
            Assembler
                |
            relocated machine code
                |
            Linker/Loader
                | 
            target machine code
```

## Structure of a Compiler
```text
           character stream
                |
           Lexical Analyzer
                |
           token stream
                |
           Syntax Analyzer
                |
           syntax tree
                |
           Semantic Analyzer
                |
           syntax tree
                |
           Intermediate Code Generator
                |
           intermediate representation
                |
           Machine-Independent
           Code Optimizer
                |
           intermediate representation
                |
           Code Generator
                |
           target-machine code
                |
            Machine-Dependent
            Code Optimizer
                |
            target-machine code
```
# History of compiler
First-generationlanguages are the machine languages, second-generation the assembly languages,
and third-generation the higher-level languages like Fortran, Cobol, Lisp, C,
C++, C#, and Java. Fourth-generation languages are languages designedfor specic applications like NOMAD for report generation, SQL for database
queries, and Postscript for text formatting.

* Another classication of languages uses the term imperative for languages in which a program species how a computation is to be done and declarative
for languages in which a program species what computation is to be done.
Languages such as C, C++, C#, and Java are imperative languages

* The term von Neumann language is applied to programming languages
whose computational model is based on the von Neumann computer architecture. Many of today's languages, such as Fortran and C are von Neumannlanguages 


# programming language basics
## Static/Dynamic distinction
* If a language uses a policy that allows the compiler to decide an issue, then we say that the language uses a static policy or that the issue can be decided at compile
time.
* 	a policy that only allows a decision to be made when we execute the program is said to be a dynamic policy or to require a decision at run time.

## Environment and state
* The environment is a mapping from names to locations in the store. Since variables refer to locations ("l-values" in the terminology of C), we could alternatively define an environment as a mapping from names to variables.
* The state is a mapping from locations in store to their values. That is, the state maps l-values to their corresponding r-values, in the terminology of C.
* Static versus dynamic binding of names to locations. Most binding of names to locations is dynamic, and we discuss several approaches to this binding throughout the section
* Static versus dynamic binding of locations to values. The binding of locations to values is generally dynamic as well, since we cannot tell the value in a location until we run the program. Declared constants are an exception.

## Names ,Identifiers ,Variables
Although the terms "name" and "variable," often refer to the same thing, we use them carefully to distinguish between compile-time names and the
run-time locations denoted by names.

* Although the terms "name" and "variable," often refer to the same thing, we use them carefully to distinguish between compile-time names and the
run-time locations denoted by names.
* A variable refers to a particular location of the store. It is common for the same identifier to be declared more than once; each such declaration
introduces a new variable.
* Even if you write a variable (like x) only once in your code, if it's declared inside a recursive function, it will point to a new memory location each time the function is called.

## Procedure ,Function and Method
A function generally returns a value of some type (the "return type"),while a procedure does not return any value.

C and similar languages, which have only functions, treat procedures as functions that have a special return type "void", to signify no return value.

## static scope and block Structure
The scope rules for C are based on program structure the scope of a declaration is determined implicitly by where the declaration appears in the program.

a block is a grouping of declarations and statements. C uses braces { and} to delimit a block; the alternative use of begin and end for the same purpose dates back to Algol.

* The scope of a top-level declaration of a name x consists of the entire program that follows, with the exception of those statements that lie within a function that also has a declaration of x. 

In C, the syntax of blocks is given by
1. One type of statement is a block. Blocks can appear anywhere that other
types of statements, such as assignment statements, can appear.
2. A block is a sequence of declarations followed by a sequence of statements,
all surrounded by braces.

* We say that a declaration D "belongs" to a block B if B is the most closelynested block containing D; that is, D is located within B, but not within anyblock that is nested within B

## Dynamic scope
The term dynamic scope, however, usually refers to the following policy: a use of a name x refers to the declaratn
of x in the most recently called, not-yet-terminated, procedure with such declaration


# A simple syntax directed translation
```text
if ( expression ) statement else statement
```
 if-else statement is the concatenation of the keyword if, an opening parenthesis, an expression, a closing parenthesis, a statement, the keywordelse, and another statement. Using the variable expr to denote an expression and the variable stmt to denote a statement, this structuring rule can be expressed as
 ```text
 stmt -> if ( expr ) stmt else stmt
 ```
in which the arrow may be read as "can have the form." Such a rule is called aproduction. In a production, lexical elements like the keyword if and the parentheses are called terminals. Variables like expr and stmt represent sequences of
terminals and are called nonterminals.
## Defination of grammer
A context-free grammar has four components:
1. A set of terminal symbols, sometimes referred to as "tokens." The terminals are the elementary symbols of the language dened by the grammar.
2. A set of nonterminals, sometimes called "syntactic variables." Each nonterminal represents a set of strings of terminals, in a manner we shall describe.
3. A set of productions, where each production consists of a nonterminal,
called the head or left side of the production, an arrow, and a sequence of terminals and/or nonterminals, called the body or right side of the production.
4. A designation of one of the nonterminals as the start symbol.

## Token vs Terminals
The lexical analyzer reads the characters of the source program, groups them into lexically meaningful units called lexemes, and produces as output tokens representing these lexemes.A token consists of two
components, a token name and an attribute value

## Derivation
A grammar derives strings by beginning with the start symbol and repeatedly replacing a nonterminal by the body of a production for that nonterminal.
* Parsing is the problem of taking a string of terminals and guring out how to derive it from the start symbol of the grammar, and if it cannot be derived from the start symbol of the grammar, then reporting syntax errors within the string

## Parse Tree 
A parse tree pictorially shows how the start symbol of a grammar derives astring in the language
Formally, given a context-free grammar, a parse tree according to the grammar is a tree with the following properties:
1. The root is labeled by the start symbol.
2. Each leaf is labeled by a terminal or by .
3. Each interior node is labeled by a nonterminal.
4. If A is the nonterminal labeling some interior node and X1,X2,..,Xn are the labels of the children of that node from left to right, then there must be a production A->X1X2X3...Xn.  

## Ambiguity
We have to be careful in talking about the structure of a string according to agrammar. A grammar can have more than one parse tree generating a givenstring of terminals. Such a grammar is said to be ambiguous.
* Since a string with more than one parse tree usually has more than one meaning, we need to design unambiguous grammars for compiling applications, or to use ambiguous grammars with additional rules to resolve the ambiguities.

## Associativity of Operator
We say that the operator + associates to the left, because an operand with plus signs on both sides of it belongs to the operator to its left.


## Syntax-Directed Translation
Syntax-directed translation is done by attaching rules or program fragments to productions in a grammar.

## attribute's
attributes are special annotations or metadata that provide extra information to the compiler about how to handle certain parts of your code.
Examples of attributes are data types of expressions, the number of instructions in the generated code, or the location of the instruction in the generated code for a construct, among many other possibilities

## (Syntax-directed) translation schema
a translation schema (or syntax-directed translation schema) is a formal way to specify how to translate a source program into some target form — such as machine code, intermediate code, or even another language — based on its grammar.


## Postfix Notation
Postfix Notation, also known as Reverse Polish Notation (RPN), is a way of writing arithmetic expressions without parentheses and operators follow their operands.

The postfix notation for an expression E can be defined inductively as follows:
1. If E is a variable or constant, then the post x notation for E is E itself.
2. If E is an expression of the form E1 op E2, where op is any binary operator, then the post x notation for E is E1' E2' op, where E1 and E2 are the postfix notation for E1 and E2.
3. If E is a parenthesized expression of the form (E1), then the postix notation for E is the same as the post x notation for E1.

## Synthesized Attributes
A synthesized attribute is an attribute whose value is computed from the attributes of its children in the parse tree.
* A syntax-directed definition associates
    1. With each grammar symbol, a set of attributes, and
    2. With each production, a set of semantic rules for computing the values often the attributes associated with the symbols appearing in the production.

