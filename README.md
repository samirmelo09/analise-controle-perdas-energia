# Projeto: Controle de Perdas de Energia ⚡

## Objetivo
Este projeto visa identificar desvios de consumo de energia elétrica para detectar possíveis ligações irregulares ("gatos"), utilizando ferramentas de análise de dados.

## Tecnologias Utilizadas
- **Google Sheets**: Armazenamento e estruturação dos dados.
- **Looker Studio**: Criação do dashboard interativo e visualização de dados.
- **GitHub**: Documentação e portfólio.

## Status do Projeto
- [x] Estruturação da base de dados fictícia.
- [x] Conexão com Looker Studio.
- [x] Criação de campos calculados (KPIs de perda).
- [ ] Dashboard finalizado.

## Identidade visual
- Azul/Turquesa (cor principal – marca) #00A6C8 / RGB(0, 166, 200)
- Laranja (cor de destaque) #F57C20 / RGB(245, 124, 32)
- Branco (fundo / respiro) #FFFFFF / RGB(255,255,255)
- Cinza neutro (para textos secundários) #6E6E6E / RGB: (110, 110, 110)

## 📊 Etapa 1 — Validação de Regras de Negócio

Para este projeto, foram desenvolvidas métricas personalizadas no Looker Studio:

### 1. Desvio de Consumo %
Identifica a variação percentual entre o que foi consumido e o que era esperado.
`Fórmula: (consumo_medido_kwh - consumo_estimado) / consumo_estimado`

### 2. Perda Financeira Estimada (R$)
Calcula o prejuízo monetário baseado na tarifa média paga pelo cliente.
`Fórmula: (consumo_estimado - consumo_medido_kwh) * (valor_faturado / consumo_medido_kwh)`

### 3. Classificação de Alerta
Automação para categorizar o risco:

CASE 
  WHEN Desvio_Consumo <= -0.4 THEN "🚨 ALERTA: Suspeita de Gato"
  ELSE "✅ Consumo Normal"
END

### ✅ Validação

A validação foi realizada por meio de uma tabela no Looker Studio contendo:
- ID da unidade consumidora
- Consumo estimado
- Consumo medido
- Desvio percentual
- Classificação de suspeita

Os resultados confirmaram o funcionamento correto da regra.

## 📊 Etapa 2 — Regras de Negócio — Controle de Perdas
✔️ Status do Projeto

### Etapa concluída: Modelagem e Validação de KPIs

- Criação de regras de detecção de consumo suspeito
- Implementação de campos calculados no Looker Studio
- Validação de unidades suspeitas por ID distinto
- Correção de agregações incorretas em KPIs
- Testes de sanidade para garantir confiabilidade dos indicadores

KPIs validados:
- Total de Unidades Distintas
- Possiveis perdas de valores
- Consumo total identificado

## Classificação de Consumo Suspeito

Uma unidade consumidora é classificada como **Suspeita** quando:

- O desvio percentual de consumo é maior ou igual a 40%

<img width="1363" height="643" alt="image" src="https://github.com/user-attachments/assets/1b7c51b2-162e-43ca-9af7-b79971d2af01" />

