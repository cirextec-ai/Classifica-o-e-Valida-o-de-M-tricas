# IEsporte – Movimento Inteligente

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)  
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/Guide/HTML/HTML5)  
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://www.javascript.com/)  
[![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)](https://www.sqlite.org/index.html)

---

## 🌐 Visão Geral

IEsporte – Movimento Inteligente é um sistema web/móvel (ou híbrido) para **gerenciamento de atividades esportivas**, com login de usuários, visualização de atividades e painel administrativo para administradores. Ele utiliza arquitetura em camadas (cliente-servidor), e seu backend é construído em **Python**, com armazenamento em **SQLite**, enquanto o frontend usa **HTML5** e **JavaScript**.

---

## 🧾 Requisitos Funcionais

As funcionalidades do sistema são descritas como **histórias de usuário**, com critérios de aceitação e regras de negócio.

| ID    | História de Usuário | Critérios de Aceitação | Regras de Negócio |
|---|---|---|---|
| **HU01** | Enquanto **usuário**, quero **realizar login** para **acessar o sistema com segurança**. | - Deve fornecer e-mail e senha válidos.<br>- Validar credenciais.<br>- Mostrar mensagem de erro se falhar. | - Senha mínima de 6 caracteres.<br>- Usuário deve já estar cadastrado. |
| **HU02** | Enquanto **usuário**, quero **visualizar a lista de atividades** para **acompanhar meu desempenho**. | - Exibir atividades com nome, data e status.<br>- Carregar automaticamente ao acessar a página. | - Somente atividades associadas ao usuário logado são mostradas. |
| **HU03** | Enquanto **usuário**, quero **ver informações de contato / falar com suporte** para **tirar dúvidas ou relatar problemas**. | - Página com e-mail, telefone, endereço.<br>- Botão ou opção para voltar. | - Dados de contato devem ser atualizáveis pelo admin. |
| **HU04** | Enquanto **administrador**, quero **gerenciar os dados do app** para **manter as informações atualizadas**. | - Criar, editar e excluir registros.<br>- Apenas admin pode acessar essa parte. | - Admin deve autenticar com credenciais especiais. |

---

## 📐 Modelagem Estrutural e Comportamental

### Diagrama de Classes (UML)


---

### Diagrama de Sequência (UML) – Login


---

## 🏗 Arquitetura do Sistema

- **Modelo**: Cliente-Servidor  
- **Organização em Camadas**:  
  1. **Frontend** — HTML5 + JavaScript  
  2. **Backend** — Python (poderia ser Django, Flask ou outro)  
  3. **Banco de Dados** — SQLite  

Essa arquitetura favorece separação de responsabilidades: o cliente (navegador ou app) apenas consome a API, o backend lida com a lógica de negócio e persistência, e o banco guarda os dados localmente ou em servidor.

---

## 🧰 Stack Tecnológica

**Frontend**  
- HTML5  
- CSS (padrão ou framework, dependendo da implementação)  
- JavaScript  

**Backend**  
- Python  
- Framework web (Django, Flask ou similar)  

**Banco de Dados**  
- SQLite  

**Outras dependências**  
- Bibliotecas para autenticação  
- ORM (se usar Django ou SQLAlchemy)  
- APIs REST  

---

## ✅ Próximos Passos

1. Gerar diagramas visuais (por exemplo, em **draw.io**) para as UMLs.  
2. Especificar requisitos não funcionais (segurança, performance, escalabilidade).  
3. Definir rotas da API (endpoints).  
4. Criar estrutura de diretórios no repositório Git para backend, frontend e documentação.  
5. Escrever testes automatizados (unitários e de integração).

---

Se quiser, posso gerar um **README.md já pronto para colocar direto no seu repositório GitHub**, com base no código real do seu projeto — posso analisar o repositório (se você me der a estrutura) e montar tudo certinho. Quer que eu faça isso?
::contentReference[oaicite:0]{index=0}



