# 💻 Sistema Bancário em Python (Versão Refatorada)

![Python](https://img.shields.io/badge/python-3.10+-blue.svg)

## 📄 Descrição do Projeto

Este projeto é uma simulação de um sistema bancário básico, desenvolvido inteiramente em Python. Esta é uma **versão refatorada** de um projeto inicial, agora utilizando uma estrutura de dados mais robusta com listas e dicionários para gerenciar múltiplos usuários e contas de forma independente e escalável.

O objetivo é aplicar conceitos fundamentais de programação através de uma interface de linha de comando interativa, focando em clareza, modularidade e boas práticas de organização de código procedural.

## ✨ Funcionalidades Principais

O sistema oferece um menu interativo com as seguintes operações:

-   **[d] Depositar:** Adiciona um valor ao saldo da conta de um cliente específico (localizado por CPF).
-   **[s] Sacar:** Retira um valor do saldo da conta, sujeito a regras de negócio.
-   **[e] Extrato:** Exibe o histórico de transações e o saldo atual da conta de um cliente.
-   **[nu] Novo Usuário:** Cadastra um novo cliente no sistema. O CPF é utilizado como identificador único para evitar duplicidade.
-   **[nc] Nova Conta:** Cria uma nova conta corrente, que é obrigatoriamente vinculada a um usuário já cadastrado.
-   **[lc] Listar Contas:** Exibe uma lista formatada de todas as contas cadastradas no sistema.
-   **[q] Sair:** Encerra a execução do programa.

## 🏦 Regras de Negócio Implementadas

Para simular um ambiente bancário, o sistema implementa as seguintes regras:

1.  **Operação de Saque:**
    -   **Limite por transação:** O valor máximo por saque é de R$ 500,00.
    -   **Limite diário de saques:** O usuário pode realizar no máximo 3 saques.
    -   **Saldo insuficiente:** Não é possível sacar um valor maior que o saldo disponível em conta.

2.  **Operação de Depósito:**
    -   Somente valores positivos podem ser depositados.

3.  **Gerenciamento de Dados:**
    -   O sistema impede a criação de múltiplos usuários com o mesmo CPF.
    -   Cada conta está diretamente associada a um único usuário.

## 🛠️ Estrutura do Código (Refatorada)

O projeto foi refatorado para uma abordagem procedural mais organizada e escalável, com uma clara separação de responsabilidades.

A principal melhoria foi a **centralização dos dados em listas de dicionários**:
-   `usuarios`: Uma lista onde cada item é um dicionário contendo os dados de um usuário (`nome`, `cpf`, etc.).
-   `contas`: Uma lista onde cada item é um dicionário representando uma conta corrente (`agencia`, `numero_conta`, `saldo`, `cpf_usuario`, etc.).

Essa estrutura permite que o sistema gerencie múltiplos clientes e contas de forma independente e consistente.

### Funções Principais:

-   `main()`: Orquestra o fluxo do programa, inicializa as listas de dados e contém o loop principal que chama as outras funções com base na escolha do usuário.
-   `menu()`: Exibe o menu de opções e captura a entrada do usuário.
-   `depositar()`, `sacar()`, `exibir_extrato()`: Funções que manipulam os dados de uma conta específica. Elas agora recebem a lista `contas` e localizam a conta correta usando o CPF do cliente.
-   `criar_usuario()` e `criar_conta()`: Gerenciam a criação de novos usuários e contas, adicionando novos dicionários às listas `usuarios` e `contas`, respectivamente.
-   `buscar_usuario_por_cpf()` e `buscar_conta_por_cpf()`: Funções auxiliares essenciais que encapsulam a lógica de busca, tornando o código mais limpo e evitando repetição.
-   `listar_contas()`: Percorre a lista de contas e exibe suas informações de forma clara.

## 🚀 Como Executar o Projeto

Para executar este projeto, você precisa ter o **Python 3** instalado em sua máquina.

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/danilogep/Sistema-Bancario-Python.git](https://github.com/danilogep/Sistema-Bancario-Python.git)
    cd seu-repositorio
    ```

2.  **Execute o script:**
    Abra um terminal na pasta do projeto e execute o seguinte comando (substitua `nome_do_arquivo.py` pelo nome real do seu script):
    ```bash
    python sistema-bancario-python.py
    ```
    
3.  **Interaja com o menu:**
    O menu do sistema bancário será exibido no terminal, e você poderá interagir digitando as opções desejadas.

## 🔮 Possíveis Melhorias Futuras

-   **Persistência de Dados:** Salvar os dados de usuários e contas em um arquivo (JSON, CSV) ou em um banco de dados (SQLite) para que não se percam ao fechar o programa.
-   **Refatoração para Orientação a Objetos (POO):** Como próximo passo de aprendizado, estruturar o código utilizando classes como `Cliente` e `ContaCorrente`.
-   **Tratamento de Erros Aprimorado:** Validar as entradas do usuário de forma mais robusta (ex: garantir que o valor de um depósito seja um número).
-   **Modularização em Múltiplos Arquivos:** Separar as funções em arquivos diferentes por responsabilidade (ex: `operacoes.py`, `clientes.py`).
