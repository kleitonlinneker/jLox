
# ☕ Lox – Interpretador em Java


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
- ✔ Declarações e Atribuições de Variáveis (Cap. 8)
- ✔ Condicionais(IF), Operadores Lógicos (AND /OR) e Loops (WHILE  / FOR) (Cap. 9)
- ✔ Funções, parâmetros, retorno e closures (Cap. 10)
- ✔ Resolução estática de variáveis e escopos (`Resolver`) (Cap. 11)
- ✔ Programação orientada a objetos:
    - Classes
    - Instâncias
    - Métodos
    - Construtores (`init`)
    - Palavra-chave `this`
      (Cap. 12)

Com isso, o **Lox já funciona como uma linguagem dinâmica completa**, com escopo léxico, funções de primeira classe e orientação a objetos.

---

## 📘 Referência
**Livro:** *[Crafting Interpreters – Robert Nystrom](https://craftinginterpreters.com/)*  
**Capítulo:** 4 – *Scanning*  
**Capítulo:** 5 – *Representing Code*  
**Capítulo:** 6 – *Parsing Expressions*  
**Capítulo:** 7 – *Evaluating Expressions*  
**Capítulo:** 8 – *Statements and State*  
**Capítulo:** 9 – *Control Flow*  
**Capítulo:** 10 – *Functions*  
**Capítulo:** 11 – *Resolving and Binding*  
**Capítulo:** 12 – *Classes*  
**Progresso até:** Seção **12.7 – Constructors and Initializers**

---

## 📂 Estrutura do Projeto

```text
src/main/java
└── com/
    └── craftinginterpreters/
        ├── lox/
        │   ├── AstPrinter.java
        │   ├── Environment.java        
        │   ├── Expr.java
        │   ├── Interpreter.java
        │   ├── Lox.java
        │   ├── LoxCallable.java
        │   ├── LoxClass.java
        │   ├── LoxFunction.java
        │   ├── LoxInstance.java        
        │   ├── Parser.java
        │   ├── Resolver.java
        │   ├── Return.java        
        │   ├── RuntimeError.java               
        │   ├── Scanner.java
        │   ├── Stmt.java         
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

### 🔹 **Token.java / TokenType.java**
Estruturas que representam um token e seus tipos.

### 🔹 **Expr.java / Stmt.java**
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

### 🔹 **Environment.java**
Implementação do encadeamento de escopos.
Armazena e recupera variáveis.

### 🔹 **Resolver.java**
Realiza a resolução estática de variáveis antes da interpretação.
Define a profundidade de cada variável para acesso eficiente no ambiente correto.

### 🔹 **LoxCallable.java**
Interface que representa qualquer entidade chamável:
Funções
Métodos
Classes (construtores)

### 🔹 **LoxFunction.java**
Implementa funções do Lox.
Suporta:
Parâmetros
Retorno (return)
Closures

### 🔹 **LoxClass.java**
Representa uma classe do Lox.
Armazena métodos, herança e construtor (init).

### 🔹 **LoxInstance.java**
Representa uma instância de uma classe.
Armazena campos e permite acesso a métodos.


---


## 🧪 Testando o Interpretador


### **Exemplo com laço `for`:**
Você pode rodar o programa e digitar:

```
for (var i = 0; i < 10; i = i + 1) print i;
```

A saída esperada do `Lox` é:

```
0
1
2
3
4
5
6
7
8
9
```


### **Exemplo com funções:**
Você pode rodar o programa e digitar:

```
fun soma(a, b) {
  return a + b;
}

print soma(3, 4);

```

A saída esperada do `Lox` é:

```
7
```


### **Exemplo com classes:**
Você pode rodar o programa e digitar:

```
class Pessoa {
  init(nome) {
    this.nome = nome;
  }

  falar() {
    print this.nome;
  }
}

var p = Pessoa("Lox");
p.falar();

```

A saída esperada do `Lox` é:

```
Lox
```

---

## 🛠️ Tecnologias Utilizadas

- Linguagem: **Java 21**
- Build: **Maven**
- IDE: **IntelliJ IDEA 2025.2.3 (Ultimate Edition)**
- Controle de versão: **Git + GitHub**

---

## ▶ Como Executar

### Via linha de comando:

```sh
javac com/craftinginterpreters/lox/*.java com/craftinginterpreters/tool/*.java
java com.craftinginterpreters.lox.Lox
```

### Via Maven
```sh
mvn install
mvn exec:java -Dexec.mainClass="com.craftinginterpreters.lox.Lox"
```

### Via IDE
Execute diretamente a classe `Lox.java`.

---
