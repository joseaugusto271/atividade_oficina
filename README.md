# ⚙️ Sistema de Gestão para Oficina Mecânica (SAEP / SENAI)

Este repositório contém o código-fonte e a documentação completa para a construção de um sistema web de gestão de oficina mecânica, desenvolvido como guia de estudo e prática para a avaliação prática **SAEP / SENAI**.

---

## 🚀 Tecnologias Utilizadas

* **Linguagem Backend:** Python 3
* **Framework Web:** Flask 3.0.3
* **Banco de Dados:** MySQL (Driver: `mysql-connector-python` 8.4.0)
* **Segurança & Criptografia:** Bcrypt 4.1.3 (Hash de senhas e LGPD)
* **Frontend:** HTML5, CSS3 e JavaScript Puro (Sem frameworks externos)

---

## 📌 Funcionalidades e Regras de Negócio

O sistema foi desenvolvido atendendo a 100% dos requisitos e regras exigidos no edital:

1. **Autenticação & Sessão:**
   * Login seguro com verificação de hash Bcrypt.
   * Tratamento e feedback explícito em caso de falha de autenticação.
   * Sessão de utilizador com expiração automática configurada para 15 minutos.
   * Exibição do nome e cargo do utilizador logado no cabeçalho global.

2. **Gestão de Clientes:**
   * Validação obrigatória de exatamente 11 dígitos para o CPF.
   * Proteção de dados (LGPD): Armazenamento do CPF criptografado com algoritmo Bcrypt no banco de dados.
   * Funcionalidade de pesquisa por termo com atualização dinâmica da listagem.
   * Permite editar os dados dos clientes e salvar diretamente no MySQL.

3. **Gestão de Veículos:**
   * Regra obrigatória: Todo veículo cadastrado **deve ser vinculado a um cliente** previamente existente no sistema.
   * Atualização e edição completa dos dados do veículo no banco de dados.

4. **Agendamentos de Serviços:**
   * Listagem completa exibida em **ordem cronológica (por data)**.
   * Exibição detalhada de todos os dados do cliente e do veículo associado.
   * Funcionalidade de alteração e reagendamento de datas de serviços com persistência no banco de dados[cite: 1].

---

## 📁 Estrutura do Projeto

```text
oficina_mecanica/
├── saep_db.sql               # Script SQL de criação do banco e dados iniciais
├── README.md                 # Documentação do repositório
└── sistema/
    ├── app.py                # Servidor principal Flask e tempo de sessão
    ├── autenticacao.py       # Módulo de login, logout e verificação Bcrypt
    ├── banco.py              # Conexão e teste de banco MySQL
    ├── clientes.py           # CRUD de clientes, validação de CPF e LGPD
    ├── veiculos.py           # CRUD de veículos e vínculo com clientes
    ├── agendamento.py        # CRUD de agendamentos e ordenação por data
    ├── rotas.py              # Controlador de rotas e injeção de sessão
    ├── requirements.txt      # Dependências do projeto Python
    ├── static/
    │   ├── css/
    │   │   └── style.css     # Estilização da interface
    │   └── js/
    │       └── main.js       # Scripts para manipulação de modais
    └── templates/
        ├── base.html         # Template base (Navbar e alertas)
        ├── login.html        # Ecrã de autenticação
        ├── dashboard.html    # Painel principal
        ├── clientes.html     # Vista de clientes
        ├── veiculos.html     # Vista de veículos
        └── agendamentos.html # Vista de agendamentos