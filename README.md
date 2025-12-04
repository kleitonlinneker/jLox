
# ☕ Lox – Interpretador Parcial


Disciplina **Compiladores** – Engenharia da Computação UFMA

Professor: Sérgio Costa

Desenvolvedores:
- **Kleiton Linneker Barbosa Pinheiro**
- **Isabel Silva de Araujo**


## 🎯 Objetivo
Implementação incremental de um interpretador completo para a linguagem **Lox**, seguindo o conteúdo do livro *Crafting Interpreters* (Robert Nystrom).  

Até o momento, a implementação cobre:

- ✔ Scanner (Cap. 4)
- ✔ Representação da AST via GenerateAst (Cap. 5)
- ✔ Parser recursivo descendente (Cap. 6)
- ✔ **Interpreter** capaz de avaliar expressões (Cap. 7)
- ✔ Suporte a:
    - Números
    - Booleanos
    - Operadores aritméticos `+ - * /`
    - Operadores de comparação `> >= < <= == !=`
    - Operadores lógicos `!` e `or`/`and`
    - Agrupamento `( ... )`

Com isso, o Lox já **lê → analisa → constrói AST → interpreta → imprime o resultado.**

---

## 📘 Referência
**Livro:** *[Crafting Interpreters – Robert Nystrom](https://craftinginterpreters.com/)*  
**Capítulo:** 4 – *Scanning*  
**Capítulo:** 5 – *Representing Code*  
**Capítulo:** 6 – *Parsing Expressions*  
**Capítulo:** 7 – *Evaluating Expressions*  
**Progresso até:** Seção **7.4 – Hooking Up the Interpreter**

---

## 📂 Estrutura do Projeto

```text
src/
└── com/
    └── craftinginterpreters/
        ├── lox/
        │   ├── AstPrinter.java
        │   ├── Expr.java
        │   ├── Interpreter.java
        │   ├── Lox.java
        │   ├── Parser.java
        │   ├── RuntimeError.java        
        │   ├── Scanner.java
        │   ├── Token.java
        │   └── TokenType.java
        └── tool/
            └── GenerateAst.java
```

---

## 📄 Explicação dos Arquivos

### 🔹 **Lox.java**
Arquivo principal.  
Responsável por iniciar o scanner → parser → interpreter.

### 🔹 **Scanner.java**
Lê os caracteres de entrada e transforma em tokens.

### 🔹 **Token / TokenType**
Estruturas que representam um token e seus tipos.

### 🔹 **Expr.java**
Arquivo gerado automaticamente por `GenerateAst.java`.  
Define a representação da árvore sintática abstrata.

### 🔹 **Parser.java**
Converte uma lista de tokens em uma AST seguindo a gramática.

### 🔹 **Interpreter.java**
Avalia a AST e retorna o resultado.

Implementa os métodos `visitLiteralExpr`, `visitBinaryExpr`, `visitUnaryExpr`, etc.

### 🔹 **AstPrinter.java**
Usado para depurar a AST imprimindo a estrutura da expressão.

### 🔹 **GenerateAst.java**
Ferramenta que gera automaticamente o arquivo `Expr.java`.

---


## 🧪 Testando o Interpretador

Você pode rodar o programa e digitar:

```
(1 + 2) * (3 - 4) == 7
```

A saída esperada do `Lox` é:

```
false
```

---

## 🛠️ Tecnologias Utilizadas

- Linguagem: **Java 21**
- IDE: **IntelliJ IDEA 2025.2.3 (Ultimate Edition)**
- Git + GitHub

---

## ▶ Como Executar

### Via linha de comando:

```sh
javac com/craftinginterpreters/lox/*.java com/craftinginterpreters/tool/*.java
java com.craftinginterpreters.lox.Lox
```

Ou execute diretamente via IDE.

---
