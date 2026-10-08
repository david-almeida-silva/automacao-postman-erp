# 🛒 Automação de Testes de Integração - ERP Varejo (API)

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-000000?style=for-the-badge&logo=npm&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

Este repositório contém uma suíte de testes de API automatizada, criada para validar regras de negócio, fluxos de integração e resiliência de um sistema simulado de ERP para o varejo.

O projeto demonstra a aplicação de testes em um cenário real de comunicação entre sistemas (balanças, leitores, PDV e ERP central), executado de forma contínua em uma esteira de CI/CD.

## 🎯 Objetivo e Impacto do Projeto
Garantir a integridade dos dados no backend, validando contratos, regras de negócio e segurança antes que qualquer falha chegue às interfaces de usuário (Shift-Left Testing).

## 🛠️ Cenários Validados
* **Validação de Regras de Negócio:** Cálculos de precificação, validação de IDs e integridade de payload.
* **Fluxos Operacionais (End-to-End na API):** Uso de variáveis de ambiente para capturar dados gerados dinamicamente (ex: `POST` criando um produto) e utilizá-los em requisições subsequentes (`GET`, `PUT`, `DELETE`).
* **Testes Negativos e Resiliência:** Validação do comportamento da API ao receber dados inválidos ou inexistentes (Status `400`, `404`, `500`) e mensagens de erro estruturadas.
* **Autenticação e Segurança:** Simulação de acesso seguro utilizando `Bearer Token` gerado dinamicamente via fluxo de login.

## 🚀 Como executar este projeto

### 1. Execução na Pipeline (CI/CD)
Este projeto está integrado com o **GitHub Actions**. Toda alteração no código dispara a esteira de testes automaticamente usando o Newman.
* Os relatórios de execução em formato HTML (`htmlextra`) ficam disponíveis para download na aba [Actions](../../actions) deste repositório, em *Artifacts*.

> **⚠️ Nota sobre a Execução em CI/CD (GitHub Actions):**
> Como este projeto utiliza a *FakeStoreAPI* (uma API pública de terceiros), a execução automatizada via GitHub Actions pode ocasionalmente falhar com o **Status Code 403**. Isso não é um erro nos testes, mas sim o **WAF (Cloudflare)** da API bloqueando os IPs dos datacenters do GitHub (Prevenção contra Bots). Em um ambiente corporativo real, as APIs internas seriam configuradas com *Whitelist* para permitir o tráfego da esteira de CI/CD. Para ver os testes passando 100%, recomendo a execução local via Newman.

### 2. Execução Local via Linha de Comando (Newman)
Para rodar os testes localmente gerando o relatório rico em HTML, certifique-se de ter o [Node.js](https://nodejs.org/) instalado e execute:

```bash
# Instale o Newman e o gerador de relatórios globalmente
npm install -g newman newman-reporter-htmlextra

# Execute a collection
newman run erp-testes.json -r htmlextra
```

### 3. Execução Visual (Postman)
Caso deseje visualizar as requisições graficamente:
1. Clone este repositório.
2. Abra o Postman e vá em **File > Import** para importar a collection.
3. Selecione a collection e clique em **Run** para executar os cenários.
