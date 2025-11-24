# ENGENHARIA DE SOFTWARE  
## MANUTENÇÃO E INTEGRAÇÃO DE SOFTWARE  
### TRABALHO PRÁTICO 5 – ENGENHARIA REVERSA

---

**Prof. Dr.:** Andey Rodrigues  
**Aluno:** Sérgio Ademir Rocha do Carmo  

---


# IEsporte – Movimento Inteligente

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)  
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/Guide/HTML/HTML5)  
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://www.javascript.com/)  
[![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)](https://www.sqlite.org/index.html)

---


## 🧾 Introdução

O **IEsporte - Movimento Inteligente** é uma plataforma web interativa voltada para fisioterapia e análise clínica de movimento. Desenvolvido com tecnologias modernas, o sistema proporciona a profissionais e pacientes o acesso a um painel dinâmico de exercícios corretivos, recursos avançados de cadastro, relatórios clínicos e futuras integrações com inteligência artificial e acessibilidade.

---

## 🧾 Objetivo

O objetivo principal do sistema IEsporte é:
- Facilitar o diagnóstico e acompanhamento do progresso de pacientes por profissionais de saúde.
- Prover aos usuários um ambiente digital para explorar, filtrar e executar exercícios voltados à correção postural e coordenação funcional.
- Garantir uma experiência inclusiva, segura e expansível para todos os públicos, com apoio à acessibilidade (Libras), segurança e privacidade de dados.

---

## 🧾 Escopo

O escopo do IEsporte compreende:
- Cadastro e autenticação de usuários, garantindo acesso seguro.
- Cadastro de atletas, atividades e sessões de treino, estruturando o histórico e o progresso individual.
- Visualização interativa dos exercícios, com filtros, detalhes e recomendações personalizadas.
- Geração e consulta de relatórios clínicos, apoiando decisões profissionais.
- Exclusão definitiva de conta e gerenciamento completo dos dados do usuário.
- Suporte à acessibilidade via integração sugerida com VLibras/HandTalk (Libras).
- Estrutura preparada para evolução, permitindo integração futura de módulos de IA e funcionalidades inclusivas, como chat adaptado.

O sistema organiza seu funcionamento em multiparalelismo de frontend SPA (HTML5/CSS3/JS) e backend Django (Python), com persistência por ORM e banco SQLite3, sendo fiel ao código e à arquitetura implementada no repositório original.

---

## 🌐 Visão Geral

IEsporte – Movimento Inteligente é um sistema web/móvel (ou híbrido) para **gerenciamento de atividades esportivas**, com login de usuários, visualização de atividades e painel administrativo para administradores. Ele utiliza arquitetura em camadas (cliente-servidor), e seu backend é construído em **Python**, com armazenamento em **SQLite**, enquanto o frontend usa **HTML5** e **JavaScript**.

---

## 🧾 Requisitos Funcionais

As funcionalidades do sistema são descritas como **histórias de usuário**, com critérios de aceitação e regras de negócio.

| ID    | História de Usuário                                                                                      | Critérios de Aceitação                                                                                                                                                   | Regras de Negócio                                                                                          |
|-------|----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| **RF01** | Enquanto **novo usuário interessado**, quero **criar uma conta** informando e-mail e senha para poder acessar o painel e explorar exercícios corretivos. | - E-mail deve ser único e obrigatório.<br>- Cadastro requer leitura e aceite dos Termos de Uso.<br>- Após cadastro, usuário é autenticado e direcionado à tela principal. | - Não pode haver dois usuários com mesmo e-mail.<br>- Checkbox dos Termos é obrigatório.<br>- Senha armazenada com hash seguro. |
| **RF02** | Enquanto **usuário cadastrado**, quero **realizar login** para acessar funcionalidades restritas da plataforma. | - Apenas usuários cadastrados podem acessar.<br>- Dados corretos liberam painel; erro exibe mensagem.<br>- Logout deve ser seguro (encerra sessão/cookies). | - E-mail é validado quanto à existência.<br>- Senha validada via hash seguro.<br>- Logout invalida autenticação. |
| **RF03** | Enquanto **usuário autenticado**, quero **visualizar lista interativa de exercícios** para explorar recomendações de correção postural. | - Permitir filtrar exercícios por categoria.<br>- Clique em card exibe detalhes.<br>- Imagens e descrições acessíveis. | - Filtros para “Todos” ou categoria.<br>- Card abre modal com detalhes.<br>- Dados vêm do sistema ou do JS embutido. |
| **RF04** | Enquanto **usuário autenticado**, quero **excluir minha conta permanentemente** se desejar sair da plataforma. | - Informar que ação é irreversível.<br>- Modal de confirmação/aborto.<br>- Após exclusão, usuário é deslogado e redirecionado à tela inicial. | - Só usuário autenticado pode excluir.<br>- Dados são removidos do banco.<br>- Exclusão é definitiva, sem reversão. |
| **RF05** | Enquanto **profissional de saúde ou usuário**, quero **cadastrar atletas** com nome, idade e e-mail para associar atividades no sistema. | - Nome, idade e e-mail obrigatórios.<br>- E-mail do atleta deve ser único. | - Não permitir duplicidade de e-mail.<br>- Idade deve ser positiva. |
| **RF06** | Enquanto **usuário**, quero **cadastrar atividades** com nome, descrição e nível de dificuldade, mantendo um catálogo organizado. | - Nome, descrição (opcional) e nível obrigatório.<br>- Nome deve ser único. | - Nível só pode ser uma das opções predefinidas.<br>- Nome não pode repetir. |
| **RF07** | Enquanto **atleta autenticado**, quero **registrar sessões** vinculando atividade, data e duração para acompanhar histórico de treinamentos. | - Sessão deve associar atleta, atividade, data e duração positiva.<br>- Não pode haver duplicidade de sessão (mesmo atleta, atividade e data). | - Restrição: unique_together.<br>- Duração deve ser positiva. |
| **RF08** | Enquanto **atleta ou profissional**, quero **gerar e visualizar relatório de progresso** detalhado das sessões realizadas. | - Relatório apresenta detalhes e data.<br>- Apenas usuários autenticados acessam seus próprios relatórios. | - Relatório vinculado ao usuário.<br>- Detalhes armazenam observações e recomendações. |
| **RF09** | Enquanto **usuário com deficiência auditiva**, quero acessar conteúdo do sistema com **tradução automática para Libras** para garantir acessibilidade. | - Recurso disponível em todas as páginas principais.<br>- Conteúdo textual pode ser traduzido via VLibras ou HandTalk. | - Tradutor Libras deve ser facilmente ativável.<br>- Uso de ferramentas padronizadas.<br>- Não pode interferir na interface. |
| **RF10** | Enquanto **usuário surdo ou com deficiência auditiva**, quero **usar chat inclusivo** para me comunicar com acessibilidade garantida. | - Chat exibe textos em formato compatível com tradução para Libras.<br>- Aceita mensagens escritas e, opcionalmente, exibe avatar Libras.<br>- Mensagens de áudio transcritas para texto. | - Chat não depende de áudio.<br>- Ícone ativa tradução.<br>- Mensagens acessíveis em Libras para consulta futura. |
---



## 🧾 Requisitos Não Funcionais — Sistema IEsporte

| ID      | Requisito Não Funcional                 | Descrição                                                                                               | Evidência/Código/Fonte                                        |
|---------|-----------------------------------------|---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| **RNF01** | Usabilidade                           | Interface intuitiva, responsiva e fácil navegação para todos os públicos.                               | Tailwind CSS, SPA, filtros interativos em `index.html`/`script.js`. |
| **RNF02** | Segurança                             | Proteção de dados, CSRF, hash de senhas e rotas/autenticação restrita.                                  | `csrf_token` em formulários Django; senha via hash; rotas protegidas nas views. |
| **RNF03** | Compatibilidade                       | Compatibilidade com os principais navegadores web e dispositivos móveis.                                | HTML5, CSS3 responsivo, testes multiplataforma.               |
| **RNF04** | Desempenho                            | Painel carrega rápido e sem travamentos, garantindo experiência fluida.                                 | Lógica SPA, scripts otimizados, manipulação DOM dinâmica.     |
| **RNF05** | Persistência de Dados                 | Dados (usuários, atletas, atividades, sessões) armazenados com confiabilidade.                          | ORM Django e banco `db.sqlite3`.                              |
| **RNF06** | Extensibilidade                       | Integração facilitada de novos módulos, IA ou plugins de acessibilidade.                                | Padrão Facade, modularização dos arquivos/código.             |
| **RNF07** | Acessibilidade                        | Acessível a usuários deficientes, incluindo tradução automática para Libras.                            | Integração sugerida VLibras/HandTalk; estrutura para inclusão no frontend. |
| **RNF08** | Localização e Internacionalização     | Preparado para múltiplos idiomas, ajustando datas e formatos conforme usuário.                         | Suporte Django a i18n/l10n e templates dinâmicos.             |
| **RNF09** | Privacidade                           | Dados pessoais tratados com confidencialidade, com opção de exclusão definitiva.                        | Funcionalidade para exclusão/autenticação, remoção do banco.  |


## 📐 Modelagem Estrutural e Comportamental

### Diagrama de Classes (UML)

<img width="1039" height="807" alt="image" src="https://github.com/user-attachments/assets/8dfb15b1-2637-4886-83b2-dd2c34a50900" />

---

### Diagrama de Sequência (UML) – Login

<img width="1016" height="838" alt="image" src="https://github.com/user-attachments/assets/3f14e0f3-25c9-46ea-af0a-5f13921d7915" />

---


## 🏗 Padrão de Arquitetura do Sistema IEsporte

## 1. MVC/MTV Django

O sistema segue o padrão **MVC** (Model–View–Controller), adaptado ao Django como **MTV** (Model–Template–View):

- **Model:**  
  Define as estruturas de dados e regras do domínio (`models.py`).  
  Exemplos: `User`, `Atleta`, `Atividade`, `Sessao`, `RelatorioProgresso`.

- **Template:**  
  Arquivos HTML que recebem dados e renderizam a interface para o usuário (`index.html` em `templates/`).

- **View (Controller):**  
  Implementa a lógica de processamento de requisições, manipula os modelos e define o que será mostrado nos templates (`views.py`).  
  Opera rotas, autenticação, filtros, respostas aos AJAX/REST, tratando o fluxo da aplicação.

---

## 2. Facade Pattern (Padrão Fachada)

- O sistema implementa o padrão **Facade** como componente centralizador do backend (`facade.py`).
- O **Facade** expõe métodos de alto nível para login, cadastro, listagem, registro, geração de relatório, abstraindo a complexidade das operações internas e tornando o sistema mais simples de usar e manter.
- Todo o fluxo complexo do backend passa, direta ou indiretamente, pelo Facade, garantindo desacoplamento e organização.

---

## 3. Camadas Separadas

- **Frontend:** SPA independente, focada na interface e consumo de APIs.
- **Backend:** Lógica central organizada no Django, com o Facade intermediando funcionalidades.
- **Banco de Dados:** Persistência relacional (SQLite) acessada exclusivamente pelo ORM do Django.

Essa arquitetura favorece separação de responsabilidades: o cliente (navegador ou app) apenas consome a API, o backend lida com a lógica de negócio e persistência, e o banco guarda os dados localmente ou em servidor.


  <img width="593" height="688" alt="Arquitetura Sistema IEsporte   MVC" src="https://github.com/user-attachments/assets/f966286c-0d38-4a47-92db-2f3291f222b9" />

  

  <img width="809" height="509" alt="Arquitetura do Sistema Iesporte" src="https://github.com/user-attachments/assets/23df85c4-2578-4f02-9c39-54f6299f2712" />

---

## 🧰  Stack Tecnológica do Sistema IEsporte

## Frontend

- **HTML5**
  - Estrutura principal da interface, organização dos elementos da SPA.
- **CSS3 (Tailwind CSS via CDN)**
  - Framework utilitário para layouts responsivos.
- **JavaScript (ES6+)**
  - Lógica dinâmica: filtros, manipulação de DOM, integração AJAX/REST.
- **Chart.js**
  - Gráficos interativos para painel de visualização dos dados.
- **Arquivos principais**
  - `index.html`: template SPA
  - `style.css`: estilos customizados
  - `script.js`: lógica dinâmica e requisições REST
- **[Futuro/Opcional]**
  - VLibras ou HandTalk: integração sugerida para acessibilidade via Libras.

---

## Backend

- **Python 3.13+**
  - Linguagem principal
- **Django 5.2.7**
  - Framework MVC/MTV: gerenciamento de rotas, autenticação, regras de negócio e segurança
- **Principais componentes**
  - `manage.py`: comando principal do projeto
  - `settings.py`, `urls.py`, `wsgi.py`: configuração global
  - `esporte_app/models.py`: entidades do domínio
  - `esporte_app/views.py`: controle de rotas e requisições
  - `esporte_app/facade.py`: padrão Facade, operações complexas centralizadas
  - `esporte_app/urls.py`: roteamento do app
  - `templates/`: HTML dinâmico
  - `static/js/`, `static/css/`: arquivos JS e CSS estáticos
- **Dependências (`requirements.txt`)**
  - Django==5.2.7
  - asgiref==3.10.0
  - sqlparse==0.5.3
  - tzdata==2025.2
- **Segurança**
  - Proteção CSRF, hash de senhas, rotas protegidas

---

## Banco de Dados

- **SQLite3**
  - SGBD relacional embutido, gerenciado pelo Django via ORM
  - Arquivo principal: `db.sqlite3`
  - Persistência de todas as entidades do domínio (usuários, atletas, atividades, sessões, relatórios)

---

## Padrões & Extras

- **Facade Pattern**
  - Centralizador das operações complexas no backend (`facade.py`)
- **MVC/MTV Django**
  - Separação clara entre dados (models), lógica/processamento (views) e interface (templates)
 

<img width="1276" height="575" alt="Stack Tecnologica 2" src="https://github.com/user-attachments/assets/ea083677-1007-4fe3-8fcd-fd435399b095" />




## ✅ Próximos Passos


---





