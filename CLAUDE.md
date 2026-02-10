# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a UBC Master of Applied Science thesis in LaTeX titled **"ExploTest, a Python Unit Test Carving Tool"** by Randy Zhu, targeting submission April 2026. The thesis documents research on automatically carving unit tests from system-level tests in Python programs.

## Building the Thesis

```bash
# Compile with latexmk (recommended — handles multiple passes automatically)
latexmk -pdf main.tex

# Or compile with pdflatex directly (may need multiple runs)
pdflatex -shell-escape main.tex
bibtex main
pdflatex -shell-escape main.tex
pdflatex -shell-escape main.tex

# Clean build artifacts
latexmk -c
```

The `-shell-escape` flag is required by the `minted` package used for code syntax highlighting (declared via `% !TEX enableShellEscape = yes` at the top of `main.tex`).

## Repository Structure

```
main.tex                    # Master document — entry point for all includes
sample_bib.bib              # Bibliography references
admin_chapters/             # Front matter (committee page, preface, abstract, etc.)
body_chapters/              # Thesis content chapters and appendices
  chap_1/                   # Introduction (research motivation, RQ1–RQ5)
  chap_2/                   # Background (unit test carving literature)
  chap_3/                   # (in progress)
  chap_4/                   # (in progress)
  chap_a1/, chap_a2/        # Appendices
ubcthesis.cls               # UBC thesis class — DO NOT MODIFY OR DELETE
genthesis.cls               # Generic thesis class — DO NOT MODIFY OR DELETE
ubcthesis.dtx               # Package documentation — DO NOT MODIFY OR DELETE
ubcthesis.ins               # Installation script — DO NOT MODIFY OR DELETE
```

Each chapter with figures keeps them in a `figs/` subdirectory (e.g., [body_chapters/chap_2/figs/](body_chapters/chap_2/figs/)).

## Important Constraints

- **Do not modify or delete** `ubcthesis.cls`, `genthesis.cls`, `ubcthesis.dtx`, `ubcthesis.ins`, or `ubcthesis.fdb_latexmk`. LaTeX is sensitive to class file locations and these are required.
- The document class is set in the first line of [main.tex](main.tex): `\documentclass[masc,oneside]{ubcthesis}`. Valid degree options: `phd`, `msc`, `masc`, `ma`, `meng`.
- The committee page at [admin_chapters/committee_page/committee_page.tex](admin_chapters/committee_page/committee_page.tex) must be edited manually.

## Thesis Architecture

The document is orchestrated from `main.tex` which `\input`s each chapter. Research questions RQ1–RQ5 are defined in Chapter 1 and drive the structure of the analysis chapters. The bibliography uses BibTeX (`sample_bib.bib`).

### Purpose

Your job is to help with LaTeX formatting, and sometimes, help with spellcheck/proof-reading, and rarely, insights. Never editorialize or add your own voice to the writing in here.
