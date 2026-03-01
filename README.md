# 📊 Integração RD Station → Google Sheets via Apps Script

> Automatize o envio e registro de leads do RD Station diretamente no Google Sheets usando Google Apps Script — sem servidores, sem custos extras.

---

## 📌 Visão Geral

Este projeto implementa uma integração entre o **RD Station** (CRM e Marketing) e o **Google Sheets** utilizando **Google Apps Script**.

O objetivo é automatizar o recebimento e registro de leads, dados de conversão e métricas de redes sociais diretamente em planilhas, permitindo análise, automação e criação de relatórios personalizados sem depender de ferramentas pagas de ETL.

---

## 🎯 Objetivo

Centralizar dados de marketing e vendas em planilhas para:

- Monitoramento de leads em tempo real
- Criação de dashboards personalizados no Google Sheets/Looker Studio
- Integração com fluxos internos de marketing e vendas
- Auditoria e histórico de dados de CRM e Instagram

---

## ⚙️ Funcionalidades

| Funcionalidade | Descrição |
|---|---|
| ✅ Webhook RD Station CRM | Recebe dados de negócios e contatos via webhook |
| ✅ Dados do Instagram | Coleta métricas de perfil e posts via API |
| ✅ Inserção automática | Registra dados diretamente nas abas da planilha |
| ✅ Personalização de colunas | Mapeamento flexível dos campos recebidos |
| ✅ Baixo custo | Roda 100% no Google Apps Script — gratuito |

---

## 🧱 Estrutura do Repositório

```
rdstation-conexao-sheets-appscript/
├── Data-RDStation-CRM       # Script para integração com RD Station CRM via webhook
├── Data-Insta               # Script para coleta de dados do perfil do Instagram
├── Data-Posts-Insta         # Script para coleta de dados dos posts do Instagram
└── README.md
```

---

## 🚀 Como Usar

### Pré-requisitos

- Conta no [RD Station CRM](https://www.rdstation.com/) ou RD Station Marketing
- Conta Google com acesso ao [Google Sheets](https://sheets.google.com)
- Acesso ao [Google Apps Script](https://script.google.com)
- Token de acesso da API do RD Station (para CRM) e/ou token da API do Instagram/Meta (para os scripts de Instagram)

---

### 1. Configurar o Google Apps Script

1. Abra sua planilha no **Google Sheets**
2. Acesse **Extensões → Apps Script**
3. Copie o conteúdo do script desejado (`Data-RDStation-CRM`, `Data-Insta` ou `Data-Posts-Insta`) e cole no editor
4. Salve o projeto

---

### 2. Configurar credenciais

Dentro do script, localize as variáveis de configuração e preencha com suas credenciais:

```javascript
// Exemplo (verifique o script específico para os nomes exatos)
const ACCESS_TOKEN = 'SEU_TOKEN_AQUI';
const SPREADSHEET_ID = 'ID_DA_SUA_PLANILHA';
const SHEET_NAME    = 'Nome da Aba';
```

---

### 3. Publicar como Web App (para webhook do RD Station CRM)

1. No editor do Apps Script, clique em **Implantar → Nova implantação**
2. Selecione o tipo **App da Web**
3. Configure:
   - **Executar como:** Eu mesmo
   - **Quem tem acesso:** Qualquer pessoa (necessário para o RD Station enviar dados)
4. Copie a **URL gerada** da implantação

---

### 4. Configurar o Webhook no RD Station

1. Acesse as configurações do **RD Station CRM** ou **RD Station Marketing**
2. Vá em **Integrações → Webhooks**
3. Crie um novo webhook apontando para a **URL do Apps Script** gerada no passo anterior
4. Selecione os eventos desejados (ex: novo negócio, mudança de etapa, conversão)

---

### 5. Testar a integração

- No Apps Script, execute a função manualmente clicando em **Executar**
- Verifique os logs em **Visualizar → Registros**
- Confirme que os dados aparecem na aba correta da planilha

---

## 📂 Descrição dos Scripts

### `Data-RDStation-CRM`
Recebe dados de leads/negócios enviados pelo RD Station via **webhook HTTP POST**. Processa o payload JSON e insere uma nova linha na planilha com os campos mapeados (nome, email, telefone, etapa do funil, etc.).

### `Data-Insta`
Coleta métricas do **perfil do Instagram** (seguidores, seguindo, total de posts, alcance, etc.) usando a API do Instagram Graph e registra os dados periodicamente na planilha.

### `Data-Posts-Insta`
Coleta dados individuais de **posts do Instagram** (curtidas, comentários, alcance, impressões, data de publicação) e os registra na planilha para análise de desempenho de conteúdo.

---

## 🔧 Personalização

Você pode adaptar os scripts para:

- Adicionar ou remover colunas na planilha
- Filtrar apenas determinados eventos do RD Station
- Enviar alertas por e-mail ao registrar um novo lead
- Acionar outros serviços via `UrlFetchApp` (ex: Slack, Telegram)

---

## 💡 Vantagens desta Abordagem

| Fator | Benefício |
|---|---|
| **Custo** | 100% gratuito (Apps Script + Google Sheets) |
| **Manutenção** | Simples — sem infraestrutura para gerenciar |
| **Escalabilidade** | Adequado para volumes médios de leads |
| **Flexibilidade** | Fácil customização direto no script |
| **Integração** | Conecta facilmente com Looker Studio, Data Studio e outras ferramentas Google |

---

## ⚠️ Limitações

- O Google Apps Script possui [limites de cota diária](https://developers.google.com/apps-script/guides/services/quotas) (ex: número de execuções, tempo de processamento)
- Para volumes muito altos de eventos, considere uma solução com Cloud Functions ou servidor dedicado
- Tokens de API têm validade e podem precisar de renovação periódica

---


## 👤 Autor

Desenvolvido por [IgorJF](https://github.com/IgorJF)

---

> 💬 Dúvidas ou sugestões? Abra uma [issue](https://github.com/IgorJF/rdstation-conexao-sheets-appscript/issues) no repositório.
