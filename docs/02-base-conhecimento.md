# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente resolva facil |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores ser dinâmico no atendimento |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir soluções adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e uma saúde financeira |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

[Sua descrição aqui]

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

[ex: Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt]

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

{
  "id_transacao": "NEG-2026-X99",
  "cliente_id": 12345,
  "acordo": {
    "tipo": "parcelado",
    "valor_original": 2000.00,
    "valor_final": 2100.00,
    "numero_parcelas": 10,
    "valor_entrada": 200.00,
    "data_vencimento_primeira": "2026-03-01"
  },
  "canal": "Chatbot_Lia",
  "status": "aguardando_pagamento_entrada"
}

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo devedor: R$ 5.000

Último pagamento das parcelas:
- 01/114:  R$ 450
- 02/114:  R$ 450
...
```
