# Previsão de Atendimentos Individuais — Florianópolis (SC)

> Modelagem e previsão de séries temporais com ARIMA e SARIMA aplicados à rede de atenção primária em saúde.

<p align="center">
  <img src="https://img.shields.io/badge/Status-Publicado-brightgreen" alt="Status: Publicado"/>
  <img src="https://img.shields.io/badge/Congresso-CBIS%202024-blue" alt="Congresso: CBIS 2024"/>
  <img src="https://img.shields.io/badge/Modalidade-Artigo%20Cient%C3%ADfico-orange" alt="Modalidade: Artigo Científico"/>
  <img src="https://img.shields.io/badge/Python-%E2%89%A5%203.8-3776AB?logo=python&logoColor=white" alt="Python ≥ 3.8"/>
</p>

---

## Publicação Científica

Este projeto originou o artigo científico submetido, aceito e apresentado no principal congresso brasileiro da área de informática em saúde:

| | Detalhes |
|:---|:---|
| **Título** | *Análise de Predições de Atendimentos na Saúde em Florianópolis* |
| **Congresso** | **XX Congresso Brasileiro de Informática em Saúde — CBIS 2024** |
| **Modalidade** | Artigos originais de pesquisas concluídas (inclui revisões de escopo, sistemáticas e integrativas) |
| **Local** | Belo Horizonte — MG, Brasil |
| **Período** | 08 a 11 de outubro de 2024 |
| **Autores** | Luciano Weber, Luís Antonio Lourenço, Vinicius Faria Culmant Ramos, Pedro Matiucci Pereira e **Martina Klippel Brehm** |
| **Apresentação** | Luís Antonio Lourenço |
| **Certificado** | [Verificar autenticidade (Even3)](https://www.even3.com.br/documentos) — Código: `36651834.307944.124522.6.88254969173665062008` |

---

## Objetivo

Prever o volume mensal de **atendimentos médicos individuais** na cidade de Florianópolis (SC), utilizando dados históricos e técnicas de modelagem de séries temporais. A série histórica abrange **60 meses** (janeiro/2019 – dezembro/2023), e os modelos são utilizados para projetar o volume de atendimentos futuros.

## Metodologia

| Etapa | Descrição |
|:------|:----------|
| **1. Análise Exploratória** | Avaliação de autocorrelação (ACF/PACF) e teste de Ljung-Box para identificação de padrões temporais |
| **2. Seleção de Hiperparâmetros** | Busca automática via `auto_arima` (critério AIC, abordagem *stepwise*) |
| **3. Modelagem** | Ajuste de modelos ARIMA e SARIMA ao conjunto de treino |
| **4. Avaliação** | Comparação por métricas de acurácia (MAE, MSE, RMSE, MAPE, Theil U₂) |
| **5. Diagnóstico** | Teste de Durbin-Watson para autocorrelação residual |

### Hiperparâmetros Selecionados

| Modelo | Ordem |
|:-------|:------|
| **ARIMA** | (1, 1, 0) |
| **SARIMA** | (0, 1, 0)(0, 1, 1)[12] |

## Dados

- **Fonte:** Registros administrativos de atendimentos na atenção primária de Florianópolis
- **Granularidade:** Mensal
- **Período:** Janeiro/2019 – Dezembro/2023 (60 observações)
- **Variável-alvo:** Número de atendimentos individuais por mês

## Modelos Utilizados

### ARIMA (*AutoRegressive Integrated Moving Average*)

Modelo clássico de séries temporais que captura a autocorrelação entre observações ao longo do tempo por meio de três componentes: autoregressivo (AR), diferenciação (I) e média móvel (MA).

### SARIMA (*Seasonal ARIMA*)

Extensão do ARIMA que incorpora **componentes sazonais** explícitos, sendo especialmente adequado para séries com comportamento periódico (e.g., sazonalidade mensal com período *m* = 12).

## Métricas de Avaliação

| Métrica | Descrição |
|:--------|:----------|
| **MAE** | Erro Absoluto Médio — magnitude média dos erros |
| **MSE** | Erro Quadrático Médio — penaliza erros de maior magnitude |
| **RMSE** | Raiz do MSE — mesma unidade dos dados originais |
| **MAPE** | Erro Percentual Absoluto Médio — erro relativo (%) |
| **Theil U₂** | Coeficiente de Theil — desempenho relativo à previsão ingênua |

## Estrutura do Projeto

```
previsao_atendimentos/
├── data/
│   └── VISITAxATENDIMENTOv6.xls      # Dataset — série histórica de atendimentos
├── legacy/
│   └── previsao_atendimentos_backup.ipynb  # Versão original do notebook (referência)
├── previsao_atendimentos.ipynb        # Notebook principal com análise completa
└── README.md                          # Documentação do projeto
```

## Requisitos

- Python ≥ 3.8
- pandas
- numpy
- matplotlib
- scipy
- statsmodels
- scikit-learn
- pmdarima

## Referências

- Box, G. E. P., Jenkins, G. M., & Reinsel, G. C. (2015). *Time Series Analysis: Forecasting and Control*. Wiley.
- Theil, H. (1966). *Applied Economic Forecasting*. North-Holland Publishing Company.
- Hyndman, R. J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice*. OTexts.

---

<p align="center">
  <sub>Projeto de pesquisa científica em Ciência de Dados aplicada à Saúde Pública — publicado no <strong>XX CBIS 2024</strong>.</sub>
</p>
