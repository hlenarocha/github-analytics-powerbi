# 🔷 GitHub Analytics Dashboard: De "Hello World" a Software Engineer

Este projeto de Business Intelligence (BI) utiliza dados reais extraídos da **API do GitHub** para transformar um histórico técnico em uma narrativa visual de carreira[cite: 8, 117]. O dashboard analisa minha evolução como desenvolvedora entre janeiro de 2023 e fevereiro de 2026[cite: 9, 27].

## 🔹 Resumo do projeto
O objetivo foi aplicar técnicas de **Storytelling** e **Data Analytics** sobre o meu próprio fluxo de trabalho, convertendo registros brutos de commits em insights de produtividade[cite: 8, 118].

* **Total de Commits:** 592 
* **Total de Repositórios:** 27 
* **Data do 1º Commit:** 10/02/2023 (Initial commit).
* **Pico de Produtividade:** Ano de 2025, com 9 projetos simultâneos. 

## 🔹 Stack 
* **Data sourcing:** Extração de dados via REST API do GitHub (JSON)
* **ETL & Modelagem:** Power Query para tratamento de dados e estruturação de fatos/dimensões.
* **Visualização:** Power BI Desktop.
* **Linguagem de análise:** DAX (Data Analysis Expressions).

## 🔹 Insights de produtividade
* **Padrões Temporais:** Meu período de maior fluxo criativo ocorre nas **terças-feiras à tarde**.
* **Mês de Pico:** Agosto destaca-se como o mês com maior volume histórico de entregas.
* **Projetos de Impacto (2025):** Atuação em sistemas para o **MEC**, **PCPR** e agência de marketing.

## 🔹 Showcase de DAX
Abaixo, algumas das medidas personalizadas criadas para extrair inteligência dos dados deste dashboard:

### 1. Identificação do primeiro Repositório
Filtra o registro cronológico inicial para marcar o começo da jornada técnica.
```dax
Primeiro Repo = 
CALCULATE(
    SELECTEDVALUE(Commits[repo_name]),
    TOPN(1, Commits, Commits[commit_date], ASC)
)
```

### 2. Volume de projetos no ano de pico
Métrica de contagem distinta para validar a carga de trabalho simultânea em 2025.

```dax
Projetos 2025 = 
CALCULATE(
    DISTINCTCOUNT(Commits[repo_name]),
    Commits[year] = 2025
)
```

### 3. Análise de Mensagens de Commit
Busca a mensagem mais descritiva através do comprimento de caracteres, destacando a qualidade da documentação.

```dax
Mensagem Mais Longa = 
CALCULATE(
    SELECTEDVALUE(Commits[message]),
    TOPN(1, Commits, LEN(Commits[message]), DESC)
)
``` 

### 🔹 Sobre a autora | Helena Rocha

- Engenharia de Software (UEPG): Estudante do último ano focada em BI e Analytics.
- Virtwell: Coordenadora de Projetos com ênfase em análise de dados e performance.
- Conheça-me: Convido você a explorar este dashboard para me conhecer melhor através da minha jornada e dos meus padrões de produtividade. **:)**