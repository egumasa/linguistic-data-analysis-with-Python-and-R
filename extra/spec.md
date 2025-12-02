
1. Project overview

Working title: linguistic-data-analysis-with-Python-and-R
Goal:
Create a self-paced spaCy tutorial with:
	•	Interactive concept slides built with Quarto + Reveal.js + Pyodide (code runs in the browser).  ￼
	•	Hands-on assignments in Jupyter notebooks using “real” spaCy, launched via MyBinder from the same GitHub repo.  ￼

Learners:
	1.	Work through interactive slides in their browser (GitHub Pages).
	2.	When prompted, click a button that opens a corresponding notebook in Binder.
	3.	Complete and run the assignment there, optionally with nbgrader-style tests.  ￼

⸻

2. Target audience & learning outcomes

Audience
	•	Students or practitioners with basic Python experience (lists, functions, control flow).
	•	New to NLP/spaCy or coming from regex/NLTK-style tooling.

By the end, learners should be able to:
	•	Explain spaCy’s core objects (nlp, Doc, Token).
	•	Use spaCy to:
	•	Tokenize text and inspect basic attributes,
	•	Access POS tags, lemmas, and morphological info,
	•	Work with dependency parses and named entities,
	•	Build simple processing pipelines.
	•	Complete small spaCy coding tasks independently in notebooks.

⸻

3. Tech stack

3.1 Frontend: slides + light interactivity
	•	Quarto with format: revealjs for slides.  ￼
	•	Pyodide integration for on-slide Python execution:
	•	Use the Quarto Pyodide engine (e.g. coatless-quarto/pyodide or Quarto Live’s live-revealjs / pyodide engine) so Python chunks run in the browser.  ￼
	•	Typical chunk:

```{pyodide}
text = "Hello spaCy learners!"
print(text)
```


	•	Slides and assets compiled to a static site and hosted on GitHub Pages (as in learning-statistics-with-python, which is a Quarto revealjs + Pyodide site on gh-pages).  ￼

On-slide interactivity goal:
Use Pyodide for small, focused exercises (toy tokenisation, list operations, small helper functions), not full spaCy. That keeps the browser environment simple and avoids heavy spaCy-in-WASM issues.

⸻

3.2 Assignments: full spaCy in Jupyter notebooks
	•	Jupyter notebooks in a notebooks/ directory for each assignment.
	•	Hosted in the same GitHub repo, launched via MyBinder:
	•	Repo contains a binder/requirements.txt with spaCy + dependencies.  ￼
	•	Binder URL embedded in slides, e.g.:
https://mybinder.org/v2/gh/<user>/spacy-course/HEAD?labpath=notebooks/01_tokens_pos.ipynb
	•	Optionally integrate nbgrader for auto-grading:
	•	Use nbgrader’s “assignment” and “autograde” tooling so notebooks include test cells and instructor cells.  ￼

Assignment notebooks will:
	•	import spacy normally (no Pyodide here).
	•	Load models like en_core_web_sm.
	•	Include scaffolded code cells with TODOs and hidden tests.

⸻

4. Repository structure

Proposed layout:

spacy-course/
  _quarto.yml
  slides/
    01_intro_spacy.qmd
    02_tokens_pos.qmd
    03_deps_ner.qmd
    04_pipelines.qmd
  notebooks/
    01_tokens_pos_assignment.ipynb
    02_ner_assignment.ipynb
    03_parsing_assignment.ipynb
  binder/
    requirements.txt      # spaCy + numpy, pandas, etc.
  .github/
    workflows/            # (optional) CI to render slides on push
  docs/                   # built Quarto site for GitHub Pages

	•	Quarto renders slides/*.qmd into docs/slides/*.html for GitHub Pages.
	•	binder/requirements.txt used by Binder to prepare the environment.  ￼

⸻

5. Content design

5.1 Slide modules (Reveal.js + Pyodide)

Each module is a .qmd file with:
	1.	Concept slides (theory, diagrams, short examples).
	2.	Micro-interactions:
	•	Pyodide cells for small Python snippets:
	•	string slicing, token splitting,
	•	simple tagging examples using pre-baked data,
	•	small “check your understanding” tasks.
	3.	Transition slide linking to the assignment notebook:
	•	A clear call-to-action:
“Now open the assignment notebook to practice this with real spaCy.”
	•	Binder button + GitHub link.

Example module breakdown:
	•	Module 1: Introduction & core objects
	•	spaCy overview, nlp pipelines, Doc and Token concepts.  ￼
	•	Pyodide cell: mimic tokenisation with text.split() and simple data structures.
	•	Link to 01_tokens_pos_assignment.ipynb.
	•	Module 2: Tokens, POS, lemmas
	•	Explain POS tagging, lemmas, and how spaCy handles them.
	•	Pyodide cell: a small dictionary mapping raw tokens to fake POS tags, used to illustrate the idea.
	•	Link to 01_tokens_pos_assignment.ipynb (same assignment, deeper tasks).
	•	Module 3: Dependencies & NER
	•	Introduction to dependency parse trees and entities.
	•	Visual diagrams on slides; optional embedded iframes to spaCy visualisations (server-hosted or pre-rendered).
	•	Link to 02_ner_assignment.ipynb and 03_parsing_assignment.ipynb.
	•	Module 4: Pipelines & custom components
	•	Conceptual explanation of nlp.pipe_names, pipeline order, custom components.
	•	Pyodide cell: illustrate a pipeline as a list of functions transforming text → tokens → features.
	•	Link to a “build a simple pipeline” notebook.

⸻

5.2 Assignment notebooks (Binder + spaCy)

Each assignment notebook should include:
	•	A header cell explaining the learning goals.
	•	Setup cell:

import spacy
nlp = spacy.load("en_core_web_sm")


	•	Scaffolded tasks (e.g.):
	1.	Tokenisation & basic attributes
	•	Write code to print text, lemma_, pos_ for each token.
	2.	Filtering tokens
	•	Extract only content words, or only named entities.
	3.	Mini analysis task
	•	Given a small corpus, count POS patterns or entity types.
	•	Test cells (for nbgrader) with assert checks on expected behaviour.  ￼

Later, you can wire nbgrader for auto-grading or just rely on these tests as self-check feedback.

⸻

6. Hosting & deployment

6.1 Slides via GitHub Pages
	•	Configure Quarto project to render slides to docs/ and add:

project:
  type: website
  output-dir: docs

format:
  revealjs:
    slide-number: true


	•	Enable GitHub Pages → serve from /docs branch/folder.
	•	This matches patterns like learning-statistics-with-python, which uses Quarto revealjs + Pyodide and is published as a gh-pages-site.  ￼

6.2 Notebooks via Binder
	•	Ensure binder/requirements.txt lists spacy and any other packages.
	•	Go to mybinder.org, paste the GitHub repo URL, configure labpath = selected notebook, and copy the generated launch URL.  ￼
	•	Put that URL in the appropriate slide as a “Launch Assignment” button.

⸻

7. Student workflow
	1.	Open the course homepage (GitHub Pages).
	2.	Choose a module (e.g., “01 – spaCy Basics”).
	3.	Work through slides; run Pyodide code to see examples.
	4.	Reach “Hands-on assignment” slide → click Binder button.
	5.	Complete notebook tasks on Binder:
	•	Run tests / see pass/fail feedback.
	•	Optionally download notebook to submit via LMS or email.

⸻

8. Instructor workflow
	1.	Author slides in Quarto:
	•	Add or adjust Pyodide code cells.
	•	Re-render site (quarto render).
	2.	Author notebooks in Jupyter:
	•	Add tasks, tests, nbgrader metadata if desired.
	•	Push to GitHub.
	3.	Update Binder config as dependencies change.
	4.	(Optional) Use nbgrader locally or on a teaching platform to:
	•	Release assignment notebooks,
	•	Autograde returned notebooks,
	•	Inspect individual submissions.  ￼

⸻

9. Development phases

To keep it manageable:
	1.	Phase 1 — Skeleton
	•	Create repo structure.
	•	Add one Quarto slide deck (01_intro_spacy.qmd) with 1–2 Pyodide cells.
	•	Add one assignment notebook with simple spaCy tasks.
	•	Hook up Binder and GitHub Pages.
	2.	Phase 2 — Expand modules
	•	Add POS, NER, parsing modules.
	•	Standardise assignment structure and tests.
	3.	Phase 3 — Refine & research
	•	Improve interactivity (more Pyodide cells, hints).
	•	Add nbgrader and/or logging if you want research data on learner behaviour.

