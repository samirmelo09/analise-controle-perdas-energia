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

Nesta etapa foi construída e validada a regra de identificação de possíveis perdas de energia elétrica, com base na comparação entre consumo estimado e consumo medido.

### 🔢 Regra de cálculo do desvio percentual
(consumo_medido_kwh - consumo_estimado) / consumo_estimado

### 🚨 Classificação de suspeita

- Desvio ≥ 30% → **Suspeito**
- Desvio < 30% → **Normal**

### ✅ Validação

A validação foi realizada por meio de uma tabela no Looker Studio contendo:
- ID da unidade consumidora
- Consumo estimado
- Consumo medido
- Desvio percentual
- Classificação de suspeita

Os resultados confirmaram o funcionamento correto da regra.

## 📊 Etapa 2 — Regras de Negócio — Controle de Perdas

## ✔️ Status do Projeto

### Etapa concluída: Modelagem e Validação de KPIs

- Criação de regras de detecção de consumo suspeito
- Implementação de campos calculados no Looker Studio
- Validação de unidades suspeitas por ID distinto
- Correção de agregações incorretas em KPIs
- Testes de sanidade para garantir confiabilidade dos indicadores

KPIs validados:
- Total de Unidades Distintas
- Unidades Suspeitas Distintas
- Percentual de Unidades Suspeitas

## Classificação de Consumo Suspeito

Uma unidade consumidora é classificada como **Suspeita** quando:

- O desvio percentual de consumo é maior ou igual a 30%

Fórmula aplicada:

(desvio_consumo_percentual >= 30%)

## Indicadores Principais

- Total de Unidades Distintas:
  COUNT_DISTINCT(id_unidade_consumidora)

- Unidades Suspeitas Distintas:
  COUNT_DISTINCT(id_unidade_consumidora WHERE classificacao = "Suspeito")

- Percentual de Unidades Suspeitas:
  unidades_suspeitas_distintas / total_unidades_distintas
