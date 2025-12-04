# 🧠 LLM-DEIA Classifier --- Classificação de Postagens sobre Diversidade, Equidade, Inclusão e Acessibilidade

Este repositório contém um protótipo de classificador baseado em **Large
Language Models (LLMs)** capaz de analisar postagens de redes sociais e
determinar:

## 🔹 1. DEIA Subtopic Classification

-   **race** (Raça)
-   **gender** (Gênero)
-   **inclusion** (Inclusão)
-   **LGBTQIA+**
-   **none** (Nenhum)

## 🔹 2. Post Stance Classification

-   **pro-DEIA** (Pró-DEIA)
-   **anti-DEIA** (Anti-DEIA)
-   **neutral** (Neutro)

O objetivo do projeto é avaliar se modelos de linguagem generalistas
conseguem reconhecer corretamente temas sensíveis e suas nuances em
discursos sociais.

------------------------------------------------------------------------

## 📊 Dataset

O dataset utilizado foi coletado a partir de postagens do Reddit usando a seguinte query string:

```
"diversity" OR "lgbt" OR "inclusion" OR "DEI" OR "DEIA" OR "sexist" OR "sexism" OR "POC" OR "person of color"
```

O dataset está sendo rotulado manualmente para validar a classificação automática realizada pelos LLMs.

------------------------------------------------------------------------

## 🧱 Arquitetura da Solução

1.  Entrada: texto de redes sociais\
2.  Modelo carregado via HuggingFace (ex.: LLaMA 3 8B)\
3.  Prompt few-shot estruturado\
4.  Classificação dupla:
    -   Subtema\
    -   Posição\
5.  Saída padronizada

------------------------------------------------------------------------

## ▶️ Como Executar

### 1. Instalação

``` python
!pip install -U "huggingface-hub<1.0,>=0.34.0"
```

### 2. Autenticação

``` python
from huggingface_hub import login
login("SEU_TOKEN")
```

### 3. Definição do modelo

``` python
model_id = "meta-llama/Llama-3-8b"
```

### 4. Prompt Structure

**Subtopic Classification:**
```
You are an expert in classifying text about Diversity, Equity, Inclusion, and Accessibility (DEIA).

Examples:

Input: "We need more women in leadership positions."
Output: gender

Input: "This policy supports minorities in the hiring process."
Output: race

Input: "All employees must wear their ID badges."
Output: none

Classify the following sentence using only the subtopics: gender, race, LGBTQIA+, inclusion or none:

Input: "{post}"
Output:
```

**Stance Classification:**
```
You are a language model trained to classify comments based on their stance toward DEIA (Diversity, Equity, Inclusion, and Accessibility).

Examples:

Input: "We need more women and people of color in leadership roles."
Output: pro-DEIA

Input: "Hiring should be based on merit, not race or gender."
Output: anti-DEIA

Input: "Our company is hosting a webinar on leadership strategies."
Output: neutral

Rate the following comment using only the following rating options: pro-DEIA, anti-DEIA or neutral.

Input: "{post}"
Output:
```

------------------------------------------------------------------------

## 📚 Resultados Esperados

-   Avaliar sensibilidade dos modelos a temas sociais\
-   Detectar vieses\
-   Comparar modelos e estratégias de prompting

------------------------------------------------------------------------

## 📬 Contato

Projeto acadêmico desenvolvido para INF2102 -- PUC-Rio.
