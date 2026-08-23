# Demonstração completa do Centraliza

Esta página apresenta os principais fluxos funcionais do Centraliza através do ambiente demonstrativo do projeto.

Todos os pacientes, profissionais, unidades, documentos e credenciais exibidos são fictícios e foram criados exclusivamente para demonstração.

> Para uma visão geral da arquitetura, tecnologias e instruções de execução, consulte o [README principal](../README.md).

---

## Visão rápida

O Centraliza reúne em uma única aplicação:

- Call Backs;
- Lembretes;
- Remanejamentos;
- busca integrada de pacientes;
- usuários;
- cargos e permissões;
- auditoria;
- documentos;
- automação integrada com Python e Selenium.

# Demonstração completa do Centraliza

## 1. Autenticação / Login

![Login](screenshots/login.png)

O acesso ao sistema é protegido por autenticação JWT.

---

## 2. Dashboard

![Dashboard](screenshots/dashboard.png)

O Dashboard concentra indicadores dos principais fluxos operacionais.

---

## 3. Call Backs

### Painel

![Call Back](screenshots/callback-panel.png)

### Detalhes

![Detalhes](screenshots/callback-details.png)

### Auditoria

![Auditoria](screenshots/callback-audit.png)

---

## 4. Lembretes

![Lembretes](screenshots/reminders.png)

### Detalhes

![Detalhes](screenshots/reminders-details.png)

### Auditoria

![Auditoria](screenshots/reminders-audit.png)

### Filipeta

![Documentos](screenshots/reminders-filipeta.png)

---

## 5. Remanejamentos

![Remanejamentos](screenshots/rescheduling.png)

### Detalhes

![Detalhes](screenshots/rescheduling-details.png)

### Auditoria

![Auditoria](screenshots/rescheduling-audit.png)

### Filipeta

![Documentos](screenshots/rescheduling-documents.png)

---

## 6. Busca integrada

![Busca](screenshots/patient-search.png)

---

## 7. Automação

### Em execução

![Automação em execução](screenshots/automation.png)

### Finalizada

![Automação finalizada](screenshots/automation-completed.png)

### Auditoria

![Auditoria](screenshots/automation-audit.png)

---

## 8. Administração

### Usuários

![Usuários](screenshots/users.png)

### Cargos e permissões

![Permissões](screenshots/permissions.png)

### Visualizar permissões

![Permissões](screenshots/view-permissions.png)

---

## 9. Fluxo completo da automação

A automação é iniciada diretamente pela interface do Centraliza.

O fluxo ocorre entre os três componentes do projeto:

```mermaid
sequenceDiagram
    actor Usuario as Usuário
    participant Web as Centraliza Web
    participant API as Centraliza API
    participant Python as Python Runner
    participant Selenium as Selenium
    participant Demo as Ambiente Demo

    Usuario->>Web: Inicia automação
    Web->>API: Solicita execução
    API->>Python: Inicia processo
    Python->>Selenium: Inicializa navegador
    Selenium->>Demo: Executa fluxo demonstrativo

    loop Durante a execução
        Python-->>API: CENTRALIZA_PROGRESS
        Web->>API: Consulta status
        API-->>Web: Progresso atualizado
    end

    Python-->>API: Código de saída
    API-->>Web: Execução finalizada
    Web-->>Usuario: Exibe resultado
```

---

## 9. Tema claro e escuro

O Centraliza possui suporte a diferentes temas de interface.

A preferência visual pode ser alterada sem modificar as funcionalidades ou permissões disponíveis no sistema.

### Modo escuro

![Dashboard em modo escuro](screenshots/dashboard.png)

### Modo claro

![Login em modo claro](screenshots/login-light.png)

![Dashboard em modo claro](screenshots/dashboard-light.png)

---

## 10. API e Swagger

A **Centraliza API** possui documentação OpenAPI/Swagger para visualização dos endpoints disponíveis e das operações oferecidas pelo backend.

A API é dividida por domínio, facilitando a localização das funcionalidades e a manutenção do projeto.

### Autenticação, Automação e Usuários

![Swagger - Autenticação, Automação e Usuários](screenshots/swagger-01.png)

Nesta parte da API estão documentados recursos relacionados a:

- autenticação de usuários;
- consulta do usuário autenticado;
- inicialização da automação;
- acompanhamento da execução;
- histórico de execuções;
- interrupção da automação;
- importação de Remanejamentos;
- administração de usuários.

---

### Usuários, Health e Lembretes

![Swagger - Usuários, Health e Lembretes](screenshots/swagger-02.png)

Além da administração de usuários, a API disponibiliza:

- endpoint de verificação de disponibilidade;
- criação de Lembretes;
- consulta;
- edição;
- exclusão;
- envio e visualização de filipetas;
- preview de documentos PDF;
- registro de tentativas de contato;
- reabertura de pacientes;
- auditoria.

---

### Permissões, Busca e Call Backs

![Swagger - Permissões, Busca e Call Backs](screenshots/swagger-03.png)

A documentação também demonstra:

- gerenciamento de cargos;
- gerenciamento de permissões;
- busca integrada de pacientes;
- preview de Remanejamentos;
- criação de Call Backs;
- consulta;
- edição;
- exclusão;
- tentativas de contato.

---

### Call Backs, Dashboard e Remanejamentos

![Swagger - Call Backs, Dashboard e Remanejamentos](screenshots/swagger-04.png)

Nesta parte aparecem funcionalidades como:

- registro de tentativas de Call Back;
- cancelamento;
- auditoria;
- indicadores do módulo;
- Dashboard consolidado;
- upload e visualização de filipetas;
- gerenciamento de Remanejamentos.

---

### Credenciais e documentos da automação

![Swagger - Credenciais e Filipetas](screenshots/swagger-05.png)

Também estão disponíveis endpoints para:

- tentativas de contato em Remanejamentos;
- reabertura de pacientes;
- auditoria;
- gerenciamento das credenciais da automação;
- consulta e envio de filipetas;
- consulta dos metadados dos documentos.

> Os endpoints protegidos exigem autenticação e autorização de acordo com as permissões do usuário.
---

## 11. O que existe por trás da interface

A demonstração apresentada nesta página utiliza uma arquitetura composta por três aplicações independentes:

- **Centraliza Web:** React + TypeScript + Vite;
- **Centraliza API:** Java + Spring Boot + PostgreSQL;
- **Centraliza Automation:** Python + Selenium.

O projeto também utiliza:

- autenticação JWT;
- cargos e permissões (RBAC);
- auditoria de operações;
- Flyway para versionamento do banco;
- testes automatizados no backend;
- JaCoCo para cobertura;
- GitHub Actions;
- criptografia de credenciais da automação;
- integração Java/Python com `ProcessBuilder`;
- acompanhamento do progresso da automação em tempo real.

Para detalhes técnicos e instruções de execução, consulte o [README principal](../README.md).