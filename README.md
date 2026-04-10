# Tabuada-de-Multiplicao-Bipide
Projeto acadêmico da disciplina de Organização e Arquitetura de Computadores, desenvolvido com a linguagem Portugol no simulador BIP IDE.

# Relatório de Funcionamento: Multiplicação por Somas Sucessivas no BIPIDE IV

## 1. Introdução

Este relatório tem como objetivo explicar como o código de multiplicação por somas sucessivas funciona dentro da arquitetura simulada pelo **BIPIDE IV**. A análise aborda tanto o funcionamento do microprocessador quanto o caminho dos dados (datapath) entre os componentes internos durante a execução do programa.

---

## 2. Visão Geral do Código

O código, escrito na linguagem **Portugol**, implementa a tabuada de um número fornecido pelo usuário. Para isso, utiliza uma função `multiplica(a, c)` que realiza a operação de multiplicação através de somas sucessivas.

O algoritmo funciona da seguinte forma: para calcular `a * c`, a função soma o valor de `a` a um acumulador, repetindo esse processo por `c` vezes dentro de um laço de repetição.

---

## 3. Arquitetura do BIPIDE: Unidade de Controle vs. Caminho de Dados

No BIPIDE IV, a arquitetura do processador é dividida em duas partes funcionais principais: a **Unidade de Controle** e o **Caminho de Dados (Datapath)**.

### 🔹 Unidade de Controle
É responsável por decodificar as instruções do programa e ativar os sinais necessários para a sua correta execução. Em outras palavras, contém a lógica que decide *o que* acontece e *quando*. Suas principais funções são:
1.  **Decodificar comandos:** Interpreta instruções como `leia`, `escreva`, `para`, `retornar`, etc.
2.  **Atualizar o Contador de Programa (PC):** Garante que o processador saiba qual é a próxima instrução a ser executada.
3.  **Controlar a ULA:** Envia os sinais que ativam as operações na Unidade Lógica e Aritmética.

### 🔹 Caminho de Dados (Datapath)
É onde as operações são efetivamente realizadas e os dados são armazenados e processados. Seus componentes incluem:
1.  **Registradores:** Armazenam as variáveis do programa, como `a`, `c`, `i` e `result`.
2.  **Acumulador (ACC):** Registrador especial que armazena os resultados intermediários das operações da ULA.
3.  **Unidade Lógica e Aritmética (ULA):** Realiza as operações matemáticas, como a soma `result + a`.

---

## 4. Detalhamento dos Componentes

### Componentes da Unidade de Controle
* **PC (Program Counter):** Armazena o endereço de memória da próxima instrução a ser executada.
* **+1:** Circuito que incrementa o valor do PC após cada instrução ser buscada.
* **Decodificador:** Interpreta a instrução corrente e ativa as linhas de controle correspondentes que comandam o caminho de dados.
* **SP (Stack Pointer) e Pilha:** Utilizados para gerenciar o fluxo de chamadas e retornos de procedimentos (funções).

### Componentes do Caminho de Dados
* **Extensor de Sinal:** Prepara os dados (operandos) para serem processados corretamente pela ULA.
* **ACC (Acumulador):** Armazena valores temporários e resultados de operações da ULA.
* **ULA (Unidade Lógica e Aritmética):** Realiza operações como soma, subtração e comparações.
* **E/S (Entrada/Saída):** Componente responsável por interagir com o usuário, exibindo os resultados na interface do BIPIDE.

---

## 5. Exemplo de Caminho de Dados na Simulação

Analisando a instrução `ADD MULTIPLICA_A`, que soma o valor da variável `a` ao acumulador, o fluxo de dados ocorre da seguinte forma:

1.  A **Unidade de Controle** busca a instrução `ADD MULTIPLICA_A` da memória.
2.  O **Decodificador** interpreta a instrução e ativa os sinais de controle necessários.
3.  O valor armazenado no endereço de memória correspondente à variável `MULTIPLICA_A` é carregado e enviado para a **ULA**.
4.  A **ULA** recebe o sinal para realizar uma soma entre este valor e o conteúdo que já está no registrador **ACC**.
5.  O resultado da soma é armazenado de volta no **ACC**.

Este ciclo se repete a cada iteração do laço na função `multiplica`, acumulando as somas no registrador `ACC` até que a multiplicação seja concluída.

---

## 6. Considerações Finais

A arquitetura **BIP IV** presente no simulador BIPIDE permite uma visualização clara e didática da separação fundamental entre a **unidade de controle** (a lógica) e o **caminho de dados** (a execução). O código da tabuada, implementado com somas sucessivas, é um excelente exemplo prático para observar, passo a passo, como as instruções de alto nível são traduzidas em operações de baixo nível dentro de um processador simples.

---

## 👥 Autores

* **Gabrieli Jorge Barbosa**
* **Leticia Veran**
* **Emanuela Kemper**
* **Valentina Ragnini**
