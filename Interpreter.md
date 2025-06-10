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

