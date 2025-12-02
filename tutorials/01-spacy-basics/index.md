---
title: "Unit 1: spaCy Basics"
subtitle: "Introduction to spaCy's Core Objects and Architecture"
---

## Learning Objectives

By the end of this unit, you will be able to:

- **Explain** spaCy's core architecture and pipeline concept
- **Identify** and work with spaCy's main objects (`nlp`, `Doc`, `Token`)
- **Perform** basic text tokenization and inspection
- **Understand** the relationship between documents, tokens, and linguistic annotations

---

## What is spaCy?

spaCy is an industrial-strength Natural Language Processing (NLP) library designed for production use. Unlike academic NLP toolkits, spaCy focuses on:

- **Speed and efficiency** - Optimized for real-world applications
- **Ease of use** - Intuitive API with sensible defaults
- **Production-ready** - Built for integration into applications
- **Modern architecture** - Deep learning models under the hood

---

## Interactive Slides

Work through the conceptual introduction with live code examples:

::: {.callout-note icon=false}
## 📊 Interactive Slides
[**Launch spaCy Basics Slides**](slides.html){.btn .btn-primary .btn-lg}

*Includes live Python code that runs directly in your browser*
:::

---

## Hands-on Assignment

Practice what you've learned with real spaCy code:

::: {.callout-tip icon=false}
## 🚀 Assignment Notebook

**Choose your preferred environment:**

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/egumasa/linguistic-data-analysis-with-Python-and-R/HEAD?labpath=notebooks%2F01_tokens_pos_assignment.ipynb){.btn .btn-outline-primary}
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/egumasa/linguistic-data-analysis-with-Python-and-R/blob/main/notebooks/01_tokens_pos_assignment.ipynb){.btn .btn-outline-primary}

**What you'll do:**
- Install and load spaCy models
- Process your first documents
- Explore token attributes
- Complete guided exercises with instant feedback
:::

---

## Key Concepts Covered

### 1. The spaCy Pipeline
```python
# This is what happens when you call nlp()
nlp = spacy.load("en_core_web_sm")
doc = nlp("Hello world!")  # Text → Doc object
```

### 2. Core Objects Hierarchy
```
nlp (Language)
 └── doc (Doc)              # Processed document
     └── token (Token)      # Individual word/punctuation
         └── attributes     # pos_, lemma_, ent_type_, etc.
```

### 3. Essential Token Attributes
- **`.text`** - Original text
- **`.lemma_`** - Root form of the word
- **`.pos_`** - Part-of-speech tag
- **`.is_punct`** - Is punctuation?
- **`.is_stop`** - Is stop word?

---

## Prerequisites

Before starting this unit, you should be comfortable with:

- Basic Python syntax (variables, functions, loops)
- Working with strings and lists
- Using Jupyter notebooks

---

## Next Steps

After completing this unit:

1. ✅ Complete the assignment notebook exercises
2. ➡️ Continue to [Unit 2: Tokens & POS](../02-tokens-pos/index.md)
3. 📚 Optional: Explore the [spaCy documentation](https://spacy.io/usage/spacy-101)

---

## Getting Help

**Stuck on something?** Here are some resources:

- 📖 [spaCy Usage Guides](https://spacy.io/usage)
- 💬 [spaCy Discussions](https://github.com/explosion/spaCy/discussions)
- 🎯 Review the slides for conceptual explanations
- 🔄 Try the interactive examples in the assignment notebook
