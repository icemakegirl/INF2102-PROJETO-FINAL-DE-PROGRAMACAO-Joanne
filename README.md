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
!pip install -U "transformers>=4.44.0" "huggingface_hub>=0.25.2"
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
You are an expert in classifying texts on diversity, equity, and inclusion using the following labels:

- gender: Statements related to women, men, non-binary people, gender equality, gender roles, or gender representation.
- race: Statements about ethnicity, racial minorities, discrimination based on race, or racial representation.
- LGBTQ+: Statements referring to sexual orientation, gender identity, same-sex relationships, or LGBTQ+ rights.
- inclusion: Statements about accessibility, disability inclusion, belonging, general DEIA practices, or inclusion that does not fit gender/race/LGBTQ+ specifically.
- none: Statements unrelated to DEIA or lacking any clear DEIA context.

Examples:
Input: "We need more women in leadership positions."
Output: gender

Input: "This policy supports minorities in the hiring process."
Output: race

Input: "The company is offering benefits for same-sex partners."
Output: LGBTQ+

Input: "We want a more inclusive workplace for everyone."
Output: inclusion

Input: "All employees must wear their ID badges."
Output: none

Classify the input using ONLY one of the following options: gender, race, LGBTQ+, inclusion, none.

Input: "{post}"
Output:
```

**Stance Classification:**
```
You are an expert in classifying texts on diversity, equity, and inclusion using the following labels:

- pro-DEIA: Supports, encourages, or speaks favorably about DEIA principles or actions.
- anti-DEIA: Opposes, criticizes, mocks, minimizes, or rejects DEIA principles.
- neutral: Unrelated, ambiguous, factual, or lacking any clear stance toward DEIA.
Examples:

Input: "We need more women and people of color in leadership roles."
Output: pro-DEIA

Input: "Hiring should be based on merit, not race or gender."
Output: anti-DEIA

Input: "Our company is hosting a webinar on leadership strategies."
Output: neutral

Input: "Quotas are a form of reverse discrimination."
Output: anti-DEIA

Input: "I don't see color, I treat everyone the same."
Output: anti-DEIA

Input: "Accessibility tools like screen readers help all users, not just those with disabilities."
Output: pro-DEIA

Input: "We should have more inclusive hiring practices."
Output: pro-DEIA


Input: "Hiring should be based on merit, not quotas."
Output: anti-DEIA

Classify the input using ONLY one of the following labels: pro-DEIA, anti-DEIA, neutral.

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
