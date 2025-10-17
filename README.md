# 💻 Sistema Bancário Simples em Python

![Python](https://img.shields.io/badge/python-3.10+-blue.svg)

## 📄 Descrição do Projeto

Este projeto é uma simulação de um sistema bancário básico, desenvolvido inteiramente em Python. O objetivo principal é aplicar e demonstrar conceitos fundamentais de programação, como manipulação de estruturas de dados, modularização de código e lógica condicional, através de uma interface de linha de comando interativa.

O sistema gerencia usuários e contas correntes, permitindo a execução das operações financeiras mais comuns, como depósitos, saques e consulta de extratos.

## ✨ Funcionalidades Principais

O sistema oferece um menu interativo com as seguintes operações:

* **[d] Depositar:** Adiciona um valor ao saldo da conta. Apenas valores positivos são permitidos.
* **[s] Sacar:** Retira um valor do saldo da conta, sujeito a regras de negócio específicas.
* **[e] Extrato:** Exibe o histórico completo de transações (depósitos e saques) e o saldo atual da conta.
* **[nu] Novo Usuário:** Cadastra um novo cliente no sistema. O CPF é utilizado como identificador único, e o sistema impede a criação de múltiplos usuários com o mesmo CPF.
* **[nc] Nova Conta:** Cria uma nova conta corrente. Cada conta é vinculada a um usuário existente (localizado pelo CPF) e recebe um número de conta sequencial e uma agência fixa (`0001`).
* **[lc] Listar Contas:** Exibe uma lista formatada de todas as contas cadastradas, mostrando a agência, o número da conta e o nome do titular.
* **[q] Sair:** Encerra a execução do programa.

## 🏦 Regras de Negócio Implementadas

Para simular um ambiente bancário mais realista, o sistema implementa as seguintes regras:

1.  **Operação de Saque:**
    * **Limite por transação:** O valor máximo por saque é de R$ 500,00.
    * **Limite diário de saques:** O usuário pode realizar no máximo 3 saques por dia.
    * **Saldo insuficiente:** Não é possível sacar um valor maior que o saldo disponível em conta.

2.  **Operação de Depósito:**
    * Somente valores positivos podem ser depositados. Valores negativos ou nulos são rejeitados.

3.  **Cadastro de Usuários:**
    * O sistema valida o CPF para garantir que não existam dois usuários com o mesmo número de documento, mantendo a integridade dos dados.

## 🛠️ Estrutura do Código

O projeto foi desenvolvido de forma procedural e modularizada, separando as responsabilidades em diferentes funções para garantir um código mais limpo e organizado.

### Funções Principais:

* `main()`: Orquestra todo o fluxo do programa. Contém o loop principal que exibe o menu e direciona o usuário para a função correspondente à sua escolha.
* `menu()`: Responsável por exibir o menu de opções e capturar a entrada do usuário.
* `depositar()` e `sacar()`: Contêm a lógica de negócio para as transações financeiras. A função `sacar` é um exemplo de implementação de múltiplos critérios de validação.
* `exibir_extrato()`: Formata e exibe o histórico de transações e o saldo final.
* `criar_usuarios()` e `criar_conta()`: Gerenciam a criação de novos usuários e contas, garantindo que as regras de negócio sejam seguidas.
* `filtrar_usuarios()`: Uma função auxiliar crucial que busca por um usuário na lista de usuários com base no CPF, sendo essencial para vincular contas a usuários.
* `listar_contas()`: Percorre a lista de contas e exibe suas informações de forma clara para o usuário.

Os dados (usuários e contas) são armazenados em memória durante a execução do programa, utilizando listas e dicionários do Python.

## 🚀 Como Executar o Projeto

Para executar este projeto, você precisa ter o **Python 3** instalado em sua máquina.

1.  **Clone o repositório (ou baixe os arquivos):**
    ```bash
    git clone [https://github.com/danilogep/Sistema-Bancario-Python.git](https://github.com/danilogep/Sistema-Bancario-Python.git)
    cd nome-do-diretorio
    ```

2.  **Execute o script:**
    Abra um terminal na pasta do projeto e execute o seguinte comando:
    ```bash
    python sistema-bancario.py
    ```
    
3.  **Interaja com o menu:**
    O menu do sistema bancário será exibido no terminal, e você poderá interagir digitando as opções desejadas.

## 🔮 Possíveis Melhorias Futuras

* **Persistência de Dados:** Implementar o salvamento dos dados de usuários e contas em um arquivo (como JSON ou CSV) ou em um banco de dados (como SQLite) para que as informações não sejam perdidas ao fechar o programa.
* **Refatoração para Orientação a Objetos (POO):** Estruturar o código utilizando classes, como `Cliente`, `ContaCorrente` e `Transacao`, para um melhor encapsulamento e escalabilidade.
* **Tratamento de Erros:** Aprimorar o tratamento de entradas inválidas do usuário (ex: digitar texto onde se espera um número).
* **Múltiplas Contas por Usuário:** Permitir que um mesmo usuário possa ter mais de uma conta.
