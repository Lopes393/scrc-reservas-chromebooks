# 💻 Reserva de Chromebooks
![Status](https://img.shields.io/badge/status-em%20produção-success)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow)
![Vite](https://img.shields.io/badge/Vite-7.x-purple)
![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-green)
![Cloudflare Pages](https://img.shields.io/badge/Cloudflare%20Pages-deployed-orange)
![License](https://img.shields.io/badge/license-MIT-blue)

Sistema web desenvolvido para o **gerenciamento e agendamento de Chromebooks em ambiente escolar**, permitindo que professores e equipe de coordenação organizem a utilização dos equipamentos de forma centralizada, segura e eficiente.

O projeto foi desenvolvido a partir de uma **necessidade real da instituição de ensino**, sendo posteriormente implantado em ambiente de produção e utilizado no dia a dia para o agendamento dos equipamentos.

Além de sua aplicação institucional, o sistema também foi utilizado como **projeto educacional com alunos do 2º ano do Curso Técnico em Desenvolvimento de Sistemas**, possibilitando a abordagem prática de conceitos relacionados ao desenvolvimento de software, banco de dados, autenticação, regras de negócio, segurança, versionamento e implantação.

---

## 🏫 Aplicação Institucional

O sistema está sendo utilizado pelo:

### **CEPI - Maria Ribeiro**
📍 Rio Verde - Goiás

A aplicação foi desenvolvida para atender à rotina de utilização dos Chromebooks da instituição, permitindo que **professores e coordenação** realizem o agendamento dos equipamentos de acordo com suas necessidades pedagógicas.

Antes da aplicação do sistema, o controle de utilização dos equipamentos poderia depender de processos manuais e descentralizados. A solução desenvolvida permite centralizar essas informações em uma aplicação web, proporcionando maior organização e visibilidade das reservas.

### 👥 Usuários do sistema

O sistema foi estruturado considerando diferentes perfis de acesso:

- 👨‍🏫 Professores
- 👩‍💼 Coordenação
- 👑 Usuário Master / Administrador

---

# 🎯 Objetivo do Projeto

O principal objetivo do sistema é **facilitar o gerenciamento da utilização dos Chromebooks**, permitindo que os profissionais da instituição consultem a disponibilidade e realizem seus agendamentos de maneira rápida e organizada.

### Principais objetivos:

- Centralizar as reservas de Chromebooks;
- Facilitar o planejamento das aulas;
- Evitar conflitos de horários;
- Registrar as reservas em banco de dados;
- Controlar o acesso dos usuários;
- Diferenciar permissões de professores e administradores;
- Permitir o gerenciamento da quantidade de equipamentos;
- Disponibilizar o sistema através da internet;
- Reduzir processos manuais de controle;
- Melhorar a organização da utilização dos equipamentos tecnológicos.

---

# 🚀 Funcionalidades

## 🔐 Autenticação

O sistema possui uma tela de login para controle de acesso.

Os usuários realizam autenticação através de:

- E-mail;
- Senha.

A autenticação é realizada utilizando o **Supabase Authentication**, mantendo as credenciais dos usuários separadas dos dados cadastrais utilizados pela aplicação.

---

## 📅 Gerenciamento de Reservas

O usuário pode consultar a agenda de utilização dos Chromebooks através de filtros de:

- 📅 Data da reserva;
- 👥 Turma;
- 👨‍🏫 Professor.

Os horários são organizados de acordo com os turnos escolares.

### ☀️ Turno da Manhã

- 1ª Aula
- 2ª Aula
- 3ª Aula
- 4ª Aula
- 5ª Aula

### 🌅 Turno da Tarde

- 6ª Aula
- 7ª Aula
- 8ª Aula
- 9ª Aula

Os horários são apresentados visualmente de acordo com sua situação:

🟢 **DISPONÍVEL**

🔴 **COM RESERVAS**

---

# ➕ Criação de Reserva

Ao selecionar um horário disponível, o sistema apresenta uma interface para criação de uma nova reserva.

O usuário pode informar:

- 📅 Data;
- 🕐 Horário;
- 👥 Turma;
- 👨‍🏫 Professor;
- 💻 Quantidade de Chromebooks.

A quantidade de equipamentos pode ser ajustada através dos controles de incremento e decremento.

### Limite de equipamentos

Cada reserva permite a utilização de:

**1 a 12 Chromebooks por professor em cada horário.**

---

# ✏️ Edição de Reservas

As reservas podem ser alteradas de acordo com as permissões do usuário.

### Professor

O professor pode editar suas próprias reservas.

### Master

O usuário Master pode editar qualquer reserva cadastrada no sistema.

---

# 🗑️ Exclusão de Reservas

A exclusão de reservas é uma operação restrita ao usuário com perfil administrativo.

### Professor

❌ Não pode excluir reservas.

### Master

✅ Pode excluir reservas.

---

# 👥 Gerenciamento de Usuários

O sistema possui controle de acesso baseado em perfil.

## 👨‍🏫 Professor

O professor possui acesso às funcionalidades necessárias para utilização do sistema em sua rotina.

Pode:

- Realizar login;
- Visualizar reservas;
- Consultar disponibilidade;
- Criar suas próprias reservas;
- Editar suas próprias reservas.

---

## 👑 Master

O usuário Master possui permissões administrativas.

Pode:

- Criar usuários;
- Criar reservas;
- Editar reservas;
- Excluir reservas;
- Administrar o sistema;
- Realizar reservas em nome de outros professores.

---

# 🔒 Segurança

A segurança da aplicação foi projetada considerando autenticação e controle de permissões no banco de dados.

A autenticação é realizada através do **Supabase Auth**.

As senhas dos usuários **não são armazenadas diretamente na tabela `usuarios` da aplicação**.

A arquitetura segue o seguinte fluxo:

```text
┌──────────────────────┐
│       Usuário        │
│ Professor / Master   │
└──────────┬───────────┘
           │
           │ E-mail + Senha
           ▼
┌──────────────────────┐
│    Supabase Auth     │
│   Autenticação        │
└──────────┬───────────┘
           │
           │ Usuário autenticado
           ▼
┌──────────────────────┐
│    Aplicação Web     │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ PostgreSQL / Supabase│
│                      │
│ Usuários             │
│ Turmas               │
│ Reservas             │
└──────────────────────┘
```
## 🛠️ Tecnologias Utilizadas

### Frontend

- **HTML5** — Estrutura das páginas da aplicação.
- **CSS3** — Estilização e organização visual da interface.
- **JavaScript (ES6+)** — Lógica da aplicação, interações e manipulação do DOM.
- **Bootstrap 5** — Componentes, responsividade e elementos visuais.
- **Vite** — Ferramenta de build e desenvolvimento da aplicação.

### Backend e Serviços

- **Supabase** — Plataforma utilizada para infraestrutura backend.
- **Supabase Authentication** — Autenticação e gerenciamento das contas dos usuários.
- **Supabase Edge Functions** — Execução de operações administrativas e lógica protegida no servidor.

### Banco de Dados

- **PostgreSQL** — Banco de dados relacional utilizado pela aplicação.
- **SQL** — Criação, consulta e gerenciamento dos dados.
- **Row Level Security (RLS)** — Controle de acesso e segurança dos dados.
- **Constraints e Índices** — Garantia da integridade e aplicação das regras de negócio.

### Desenvolvimento e Versionamento

- **Git** — Controle de versão do projeto.
- **GitHub** — Hospedagem do código-fonte e versionamento do projeto.
- **GitHub Codespaces** — Ambiente de desenvolvimento em nuvem.
- **Visual Studio Code** — Editor utilizado durante o desenvolvimento.

### Deploy e Hospedagem

- **Cloudflare Pages** — Hospedagem e publicação da aplicação em ambiente de produção.

---

### 🔧 Stack do Projeto

```text
HTML5
CSS3
JavaScript
Bootstrap
Vite
      │
      ▼
Supabase
├── Authentication
├── PostgreSQL
├── Row Level Security
└── Edge Functions
      │
      ▼
Cloudflare Pages
      │
      ▼
Aplicação em Produção
```

## 👨‍💻 Autor

```markdown
### Murilo Henrique Alves Lopes

Professor e desenvolvedor na área de Tecnologia da Informação.

Formação em **Sistemas de Informação** e pós-graduação em **Ciência de Dados**.

Atua na área de desenvolvimento de sistemas e educação profissional, buscando integrar tecnologia, desenvolvimento de software e metodologias práticas de ensino.

O projeto **Reserva de Chromebooks** foi desenvolvido com o objetivo de solucionar uma necessidade real do ambiente escolar e, simultaneamente, proporcionar aos estudantes do **2º ano do Curso Técnico em Desenvolvimento de Sistemas** uma experiência prática com as etapas de desenvolvimento de uma aplicação real.

### 🎓 Contexto Educacional

O projeto também foi utilizado como ferramenta pedagógica com os alunos do:

**2º Ano — Curso Técnico em Desenvolvimento de Sistemas**

Durante o desenvolvimento, os estudantes tiveram contato com conceitos como:

- Levantamento de requisitos;
- Regras de negócio;
- Desenvolvimento Web;
- JavaScript;
- Banco de Dados;
- SQL;
- PostgreSQL;
- Autenticação;
- Segurança;
- Git e GitHub;
- Testes;
- Deploy;
- Manutenção de sistemas.

A proposta teve como objetivo demonstrar aos estudantes como os conhecimentos desenvolvidos durante a formação técnica podem ser aplicados na construção de uma solução utilizada em um ambiente profissional real.
```
## 📄 Licença

Este projeto está licenciado sob a **MIT License**.

A licença permite o uso, cópia, modificação, distribuição e utilização do projeto para fins pessoais ou comerciais, desde que o aviso de copyright e os termos da licença sejam mantidos.

### Copyright

Copyright © 2026 **Murilo Henrique Alves Lopes**

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files, to deal in the Software
without restriction, including without limitation the rights to use, copy,
modify, merge, publish, distribute, sublicense, and/or sell copies of the
Software, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
