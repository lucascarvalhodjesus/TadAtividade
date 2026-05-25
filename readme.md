# MyLinkedList - Implementação de Lista Encadeada Simples

Este repositório contém a implementação do Tipo Abstrato de Dados (TAD) de uma Lista Encadeada Simples (*Singly Linked List*) em Java.

O projeto inclui operações básicas de manipulação de nós e a resolução de algoritmos clássicos de manipulação de ponteiros.

## Como funciona

Uma Lista Encadeada é uma estrutura de dados linear onde os elementos não são armazenados em posições contíguas de memória, diferentemente de um array.

Cada elemento é um **Nó** (`Node`) que contém duas partes fundamentais:

- O valor ou dado em si (`element`).
- Um ponteiro ou referência para o próximo nó da sequência (`next`).

A lista possui um ponto de entrada chamado `head` (cabeça), que aponta para o primeiro nó.

Para percorrer a lista, inicia-se no `head` e seguem-se os ponteiros `next` até encontrar um nó cujo próximo seja nulo (`null`), indicando o fim da estrutura.

Frequentemente, esse fim também é rastreado por um ponteiro `tail`, o que ajuda a otimizar inserções no final.

## O porquê: vantagens e utilidade

Não adianta implementar uma estrutura de dados sem entender o problema que ela resolve. Aqui estão os principais motivos para utilizar listas encadeadas em aplicações reais:

- **Alocação dinâmica de memória:** ao contrário de um array padrão, que exige um tamanho fixo na criação e pode precisar de realocações custosas quando enche, a lista encadeada cresce e diminui dinamicamente sob demanda. A memória só é alocada quando um novo dado entra.
- **Inserções e remoções eficientes:** inserir ou remover um elemento no início da lista, ou em uma posição onde já se tem a referência do nó, tem complexidade de tempo $$O(1)$$. Em um array, remover o primeiro elemento exige deslocar todos os demais itens, resultando em $$O(n)$$.
- **Ausência de desperdício espacial:** estruturas baseadas em arrays dinâmicos, como o `ArrayList` do Java, frequentemente aumentam sua capacidade interna para acomodar novos itens, o que pode deixar espaços de memória ociosos. A lista encadeada consome apenas o necessário para os nós existentes.

## Quando usar em aplicações

No contexto de desenvolvimento web e arquitetura de software, raramente essa estrutura será recriada do zero no dia a dia, mas suas variações aparecem com frequência.

Use conceitos de listas encadeadas quando houver cenários como:

- **Sistemas de filas e escalonamento:** gerenciamento de requisições de servidores, tarefas em background (*jobs*) ou filas de trabalhadores em sistemas logísticos. Os elementos entram e saem constantemente, e o tamanho total é altamente variável.
- **Históricos e funcionalidades de desfazer:** navegação em páginas web ou editores de texto costumam usar listas duplamente encadeadas para avançar e retroceder estados de forma eficiente.
- **Processamento de streams de dados:** quando os dados chegam continuamente e o volume total não é conhecido de antemão, encadear os pacotes recebidos pode ser mais eficiente do que realocar arrays repetidamente.

## Estrutura do projeto

- `Node.java`: estrutura base que armazena a informação (tipo genérico `T`) e o ponteiro para o próximo nó.
- `LinkedListTAD.java`: interface que define o contrato da estrutura de dados.
- `MyLinkedList.java`: implementação concreta da interface, controlando `head`, `tail` e `size`. Contém a lógica de algoritmos mais complexos, como `reverse`, `merge` e `sorted insertion`.
- `Main.java`: interface de linha de comando (CLI) interativa para testar as funcionalidades e visualizar as modificações na estrutura em tempo real.

## Como executar

Certifique-se de ter o JDK instalado.

```bash
javac *.java
java Main
```

### Exemplo de menu no terminal

```text
╔══════════════════════════════════════╗
║    Lista Encadeada                  ║
╠══════════════════════════════════════╣
║ 1 - Criar lista                     ║
║ 2 - Q1: Sorted Insertion            ║
║ 3 - Q2: Delete sem predecessor      ║
║ 4 - Q3: Reversal                    ║
║ 5 - Q4: Merge Two Sorted Lists      ║
║ 6 - Q5: Remove Nth From End         ║
║ 0 - Sair                            ║
╚══════════════════════════════════════╝
```

## Exemplo de uso via código

```java
MyLinkedList<Integer> list = new MyLinkedList<>();

list.addLast(10);
list.addLast(20);
list.addLast(40);

list.addAscendingSorted(30);

list.reverse();
```
