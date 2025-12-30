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
