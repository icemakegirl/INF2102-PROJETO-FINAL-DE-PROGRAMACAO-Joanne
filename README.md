# INF2102-PROJETO-FINAL-DE-PROGRAMACAO-Joanne
# 🧠 LLM-DEIA Classifier --- Classificação de Postagens sobre Diversidade, Equidade, Inclusão e Acessibilidade

Este repositório contém um protótipo de classificador baseado em **Large
Language Models (LLMs)** capaz de analisar postagens de redes sociais e
determinar:

## 🔹 1. Subtema DEIA abordado

-   Raça\
-   Gênero\
-   Inclusão\
-   LGBTQIA+

## 🔹 2. Posição do Post

-   **Pro-DEIA**\
-   **Anti-DEIA**\
-   **Neutro**

O objetivo do projeto é avaliar se modelos de linguagem generalistas
conseguem reconhecer corretamente temas sensíveis e suas nuances em
discursos sociais.

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

### 4. Estrutura do Prompt

    Texto: "Precisamos de mais políticas de inclusão para PCDs."
    Subtema: inclusão
    Posição: pro

    Texto: {seu_texto}
    Subtema:
    Posição:

------------------------------------------------------------------------

## 📚 Resultados Esperados

-   Avaliar sensibilidade dos modelos a temas sociais\
-   Detectar vieses\
-   Comparar modelos e estratégias de prompting

------------------------------------------------------------------------

## 📬 Contato

Projeto acadêmico desenvolvido para INF2102 -- PUC-Rio.
