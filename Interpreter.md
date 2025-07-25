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


# Scanner
## Overview
A compiler’s scanner reads the input stream and produces, as output, a stream of words, each labeled with its syntactic category—equivalent to
a word’s part of speech in English. Each time it is called, the scanner produces Lexeme a pair, lexeme,category, where lexeme is the spelling of the word the actual text for a word recognized by a
scanner and category is its syntactic category. This pair is sometimes called a token.


To translate a program, the compiler must understand both its lexical structure—the spellings of the words in the program—and its syntactic
structure—the grammatical way that words fit together to form statements and programs


To find and classify words, the scanner applies a set of rules that describe the lexical structure of the input programming language, sometimes called its microsyntax.

## Finite automata
A finite automaton (FA) is a simple idealized machine used to recognize patterns within input taken from some character set (or alphabet) C. The job of an FA is to accept or reject an input depending on whether the pattern defined by the FA occurs in the input.
Think of a robot with a few states in its brain. It reads one letter at a time (like 'a', 'b', or '0', '1') from a string and changes its state based on what it reads. In the end, the robot decides: ✅ "I accept this string" or ❌ "I reject it".

Formally, a finite automaton (FA) is a five-tuple (S,sigma , δ, s0, SA), where





