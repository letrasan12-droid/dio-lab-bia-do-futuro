# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

[negociação de empréstimos]

### Solução
> Como o agente resolve esse problema de forma proativa?

[entrando em contato com o cliente que tem uma dívida e renegociando a divida no valor que o cliente quer.]

### Público-Alvo
> Quem vai usar esse agente?

[devedores] 

---

## Persona e Tom de Voz

### Nome do Agente
[Resolva Fácil]

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

[educativdo e objetivo] 

### Tom de Comunicação
> Formal, informal, técnico, acessível?

[informal]

### Exemplos de Linguagem
- Saudação: [ex: "Olá! Como posso ajudar com suas finanças hoje?"]
- Confirmação: [ex: "Entendi! Deixa eu verificar isso para você."]
- Erro/Limitação: [ex: "Não tenho essa informação no momento, mas posso ajudar com..."]

---

## Arquitetura

### Diagrama

import streamlit as st

def interface_renegociacao():
    st.header("🤝 Portal de Renegociação")
    
    # 1. Dados da Dívida (Simulados)
    divida_original = 5000.00
    desconto_maximo = 0.30  # 30% de desconto para pagamento à vista
    
    st.info(f"Identificamos uma pendência de **R$ {divida_original:,.2f}**")
    
    # 2. O Simulador (UX: Controle nas mãos do usuário)
    col1, col2 = st.columns(2)
    
    with col1:
        num_parcelas = st.select_slider(
            "Em quantas vezes deseja pagar?",
            options=[1, 6, 12, 18, 24]
        )
        
    # 3. Lógica de Negócio (Python)
    if num_parcelas == 1:
        valor_final = divida_original * (1 - desconto_maximo)
        texto_parcela = "Pagamento único com 30% de desconto!"
    else:
        # Simulação de juros leves para parcelamento
        valor_final = divida_original * (1 + (0.01 * num_parcelas))
        texto_parcela = f"{num_parcelas}x de R$ {valor_final/num_parcelas:,.2f}"

    # 4. Painel de Resumo (UI Clara)
    with col2:
        st.metric("Total do Acordo", f"R$ {valor_final:,.2f}")
        st.write(f"ℹ️ {texto_parcela}")

    # 5. Fechamento
    st.divider()
    metodo = st.radio("Forma de pagamento:", ["Pix (Liberação imediata)", "Boleto", "Cartão de Crédito"])
    
    if st.button("Confirmar Acordo", type="primary"):
        st.success("✅ Acordo registrado com sucesso! Gerando seu comprovante...")
        st.balloons()

# Para rodar, basta chamar a função em um ambiente Streamlit
interface_renegociacao()

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [ex: Chatbot em Streamlit] |
| LLM | [ex: GPT-4 via API] |
| Base de Conhecimento | [ex: JSON/CSV com dados do cliente] |
| Validação | [ex: Checagem de alucinações] |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ] [ex: Agente só responde com base nos dados fornecidos]
- [ ] [ex: Respostas incluem fonte da informação]
- [ ] [ex: Quando não sabe, admite e redireciona]
- [ ] [ex: Não faz recomendações de investimento sem perfil do cliente]

### Limitações Declaradas
> O que o agente NÃO faz?

[ele não faz funções do banco convencional, o canal seria apenas para renegociação]
