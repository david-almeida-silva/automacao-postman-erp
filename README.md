# 🛒 Automação de Testes de Integração - ERP Varejo (Postman)

Este repositório contém uma suíte de testes de API desenvolvida no **Postman**, criada para validar regras de negócio, fluxos de integração e resiliência de um sistema simulado de ERP para o varejo.

## 🎯 Objetivo do Projeto
Demonstrar na prática os conhecimentos técnicos exigidos para testes e homologação de integrações, garantindo a qualidade da comunicação entre sistemas (como balanças, leitores e PDV) e o ERP central.

## 🛠️ O que foi testado?
* **Validação de Regras de Negócio:** Testes baseados na lógica do sistema (ex: cálculos, validação de IDs de produtos).
* **Testes de Fluxo Operacional:** Uso de Variáveis de Ambiente para capturar dados gerados dinamicamente (`POST`) e utilizá-los nas requisições seguintes (`GET`).
* **Testes Negativos:** Validação de comportamento do sistema ao buscar dados inexistentes (Status 404 e tratamento de erros).
* **Autenticação:** Simulação de acesso seguro utilizando `Bearer Token` gerado dinamicamente no login.

## 🚀 Como executar este projeto
1. Baixe o arquivo `.json` disponível neste repositório.
2. Abra o seu Postman.
3. Vá em **File > Import** e selecione o arquivo baixado.
4. Clique em **Run Collection** para executar todos os cenários de forma automatizada.
