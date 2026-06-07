# How to write the commutative algebra explainer

Instructions for a Claude model writing notes in this directory. The subject is
**commutative algebra**, but the *style* is the same one used for the gauge-fields
explainer at `../gauge_fields/gauge_fields.tex` — read that file first; it is the worked
exemplar of everything below. Your job is to produce a standalone, compilable
`comm_alg.tex` that teaches like that one.

The single most important instruction: **explain things fully. Do not skip the
load-bearing steps.** Most first drafts fail by giving an important idea one definition,
one sentence of intuition, and one example, then moving on. That is not enough. Give the
important parts their due.

---

## Who the reader is

A strong student (think: comfortable with groups/rings/fields from a first abstract
algebra course, linear algebra, basic topology) who wants to *actually understand*
commutative algebra in its natural setting — not just manipulate it. They learn by asking
basic questions and seeing ideas in the setting where they're inevitable. Write for that
person. Assume maturity, not prior exposure to the specific topic.

---

## The non-negotiables (philosophy)

1. **Motivation first.** Before any definition, answer: *why should I care, and how does
   this connect to what I already know?* Open each major topic with the problem it solves.
2. **Intuition alongside rigor.** Every precise definition gets a plain-language gloss:
   what is this really, how does a practitioner picture it, why is *this* the right
   definition (and not a nearby alternative).
3. **LOTS of examples.** This is not optional and not a garnish. Every definition gets
   multiple worked examples — including degenerate/edge cases and at least one
   non-example. When in doubt, add another example.
4. **Connect outward constantly.** Tie each idea to algebraic geometry, number theory,
   linear algebra, topology — whatever the reader already knows.
5. **Don't skip steps.** If a computation, sign, or "it follows that" matters, show it.
   If you assert something ("this is well-defined", "the map descends to the quotient"),
   either prove it inline or make it a tagged exercise — don't leave it dangling. It usually
   takes less than a sentence to say why something is true - just say it, e.g. "this follows
   because of [X]", or "this is well-defined because of [Y]".

---

## Document structure (the arc)

Mirror the gauge-fields notes:

1. **Big-picture opening section.** Heavy motivation. What is commutative algebra, why it
   exists (it *is* the local algebra of geometry and the arithmetic of numbers), and a
   one-paragraph "if you remember one thing" summary. A map of the notes.
2. **Main development**, in sections that build. Precise definitions, generous intuition,
   many examples, the "why this is the right definition" discussion, and connections.
3. **Intra-text exercises** sprinkled throughout at a steady pace (see below).
4. **End-of-chapter exercises** as a dedicated final section.
5. **Annotated references** (see Sourcing).

---

## The hard-won pedagogical rules (these come from direct feedback — obey them)

- **One def + one intuition + one example is too little for an important topic.** Localize,
  Spec, tensor products, integral extensions, completion, dimension — each deserves
  *pages*: motivation, the definition built up in stages, the universal property *and* the
  concrete construction, several examples, the pitfalls, and how to compute.
- **Explain notation the moment you introduce it.** Never use a symbol, operator, or
  construction you haven't defined earlier in the text. If you write $\Spec R$, $R_\mathfrak{p}$,
  $M \otimes_R N$, $\operatorname{Ann}(M)$, $\sqrt{I}$, $\varinjlim$, $V(I)$ — define it on
  first use.
- **If you present something in a non-standard or abstract way first, connect it to the
  standard way.** Universal properties are powerful but alien at first: always pair the
  universal-property definition with the explicit construction and say *why they're the
  same object*. (Compare how the gauge notes pair the Ehresmann connection $\omega$ on the
  total space with the physicist's $A_\mu$ via pullback.)
- **Write in flowing prose, not just boxes.** The colorbox environments are for landmarks
  (definitions, key results, intuition nuggets). The connective tissue — derivations,
  motivation, "here's what just happened" — should be ordinary paragraphs *between* and
  *around* the boxes. A page that is all boxes is a failure.
- **Plan to do a second pass.** After a complete draft, re-read critically for skipped
  steps, undefined notation, and unmotivated definitions, and fix them. Verify correctness
  against the references; if you find an error, fix it and say so.

---

## Examples discipline

For each core concept, aim to include:

- A **canonical example** the reader already half-knows ($\mathbb{Z}$, $k[x]$, $k[x,y]$).
- A **geometric example** (coordinate rings, $\operatorname{Spec}$, varieties).
- A **number-theoretic example** ($\mathbb{Z}_{(p)}$, $\mathbb{Z}_p$, $\mathbb{Z}[i]$, rings of integers).
- A **degenerate/edge case** ($k[x]/(x^2)$, the zero ring, non-reduced or non-domain rings).
- A **non-example** that shows what goes wrong when a hypothesis is dropped.

A running stock of objects to reuse: $\mathbb{Z}$; $k$, $k[x]$, $k[x,y]$, $k[x_1,\dots,x_n]$;
$k[x]/(x^2)$ (dual numbers) and other quotients; localizations $S^{-1}R$, $R_\mathfrak{p}$,
$R_f$; $\mathbb{Z}_{(p)}$ and the $p$-adics $\mathbb{Z}_p$; $\mathbb{Z}[i]$ and $\mathbb{Z}[\sqrt{-5}]$;
coordinate rings $k[V]=k[x_1,\dots,x_n]/I(V)$; power series $k[[x]]$. Reuse the same objects
across topics so the reader watches one object reveal new structure.

Topics where intuition is the whole battle (spend extra care): **localization** (inverting
elements = zooming into part of $\operatorname{Spec}$); **prime vs. maximal ideals** and
why primes are the "points"; the **Nullstellensatz** (the algebra–geometry dictionary);
**tensor products of modules** (universal property *and* generators-and-relations
construction, plus why it's right-exact); **exact sequences and $\operatorname{Tor}/\operatorname{Ext}$**;
**Nakayama's lemma**; **integral extensions** and going-up/going-down; **completion**;
**Krull dimension**. For each, lead with the picture, then the definition, then examples,
then computation.

---

## Exercises

- **Intra-text exercises**, steady pace, each tagged with difficulty:
  **(easy)**, **(classic)**, **(medium)**, **(thinker)**. Mix routine checks, the standard
  must-do problems, and a few that genuinely make the reader think. Offload "verify this is
  well-defined"-type gaps into exercises rather than skipping them silently.
- **End-of-chapter exercises** in a dedicated final section; a few open-ended ones that
  push toward the references are good.
- Use the green `xca` environment (see LaTeX setup) so exercises stand out and are easy to
  find.

---

## LaTeX setup and mechanics

- Start from the existing stub `comm_alg.tex` and match the `../gauge_fields/gauge_fields.tex`
  preamble: `\documentclass[11pt]{article}`, `geometry`, `amsmath,amssymb,amsthm`,
  `\usepackage{william}`, `fancyhdr`, `\microtoc` for the TOC. The `william` package is
  installed in the user's texmf tree, so `\usepackage{william}` works from here.
- **Add an exercise environment** to the preamble (it lives in the doc, not in
  `william.sty`):
  ```latex
  \declaretheorem[style=thmgreenbox,name=Exercise,numberwithin=section]{xca}
  ```
- **Box environments available from `william.sty`** (each `declaretheorem`, takes an
  optional `[title]`): `ddefinition`, `pproposition`, `ttheorem`, `iidea` (blue);
  `iintuition`, `ttechnique`, `eexample` (red); `eequation` (yellow, for a headline
  result); `reemark` (purple); `nnote` (black); `ppreview` (pink). Use `eexample` for most
  worked examples, `ddefinition`/`ttheorem` for the load-bearing statements,
  `iintuition`/`nnote` for commentary, `eequation` for a "carry this in your head" box.
- **Highlight first-use terms** with `\vocab{...}`.
- Useful macros already defined: `\reals \ints \complex \natty \eff`, `\Hom \End \coker
  \im \id \tr`, `\cat{...}` (category names), `\defeq`, `\noin`, `\lie{...}`. **Define your
  own** CA shortcuts in the preamble as needed, e.g.
  ```latex
  \DeclareMathOperator{\Spec}{Spec}   \DeclareMathOperator{\Ann}{Ann}
  \DeclareMathOperator{\Frac}{Frac}   \DeclareMathOperator{\ht}{ht}
  \DeclareMathOperator{\Nil}{Nil}     \newcommand{\mfp}{\mathfrak{p}}
  \newcommand{\mfm}{\mathfrak{m}}     \newcommand{\mfq}{\mathfrak{q}}
  \newcommand{\mfa}{\mathfrak{a}}
  ```
- Footnotes **work inside** the mdframed colorboxes (they tuck at the box bottom) — use
  them for inline source citations.
- **Compile and verify**: run `pdflatex` twice (TOC/refs), then fix problems until clean:
  ```
  pdflatex -interaction=nonstopmode -halt-on-error comm_alg.tex
  ```
  Check the log for errors, `LaTeX Warning: Reference ... undefined`, and
  `Overfull \hbox` (long `\texttt{}`/URLs are the usual culprit — wrap URLs in `\url{}`
  and/or `\sloppy` the bibliography). The target is **0 errors, 0 overfull boxes, no
  undefined references.** Then spot-check a few rendered pages.

---

## Sourcing: ground the notes in the references

The `assets/` folder contains the primary sources — read the relevant sections before
writing each topic and add **inline footnote pointers** to specific chapters/sections, so
the notes double as a guided reading plan.

- `assets/atiyah_macdonald.pdf` — Atiyah & Macdonald, *Introduction to Commutative
  Algebra*. The standard concise reference; cite by chapter (e.g. "A–M Ch. 3" for
  localization).
- `assets/altman_kleiman.pdf` — Altman & Kleiman, *A Term of Commutative Algebra*. Free,
  modern, exercise-driven; great for worked examples and problems.
- `assets/aluffi.pdf` — Aluffi, *Algebra: Chapter 0*. Categorical and readable; good for
  universal properties and the module/linear-algebra perspective.

Use `pdftotext` (at `/opt/homebrew/bin/pdftotext`) to navigate the PDFs. End the notes
with an annotated reference list and a short "what to read next / books to own" list, the
way the gauge-fields notes do.

---

## Quick workflow checklist

1. Read `../gauge_fields/gauge_fields.tex` (the exemplar) and skim the `assets/` sources.
2. Outline the sections (motivation → development → exercises → references).
3. Draft, obeying the non-negotiables: motivation, intuition, **many** examples, defined
   notation, no skipped steps, prose between boxes.
4. Add graded intra-text exercises throughout + an end-of-chapter set.
5. Add inline footnote citations to the `assets/` sources; write the reference list.
6. Compile to a clean PDF (0 errors / 0 overfull / no undefined refs); spot-check pages.
7. **Second pass**: hunt for skipped steps, undefined notation, unmotivated definitions,
   too-few examples; fix them. Verify correctness against the references.

---

## Anti-patterns (do NOT do these)

- A definition with no motivation, or no example.
- Notation used before it's defined.
- An abstract/slick presentation with no bridge to the concrete, standard version.
- A wall of colorboxes with no connecting prose.
- "It is easy to see / clearly / one checks" covering a step that actually matters.
- One example where three were needed.
- Stopping at a first draft without the critical second pass.

## Some stylistic notes

Emphasize the categorical perspective on commutative algebra,
and aim to connect the subject to other areas of mathematics
while writing the notes, e.g. to algebraic geometry, number
theory, Geometric Langlands, normal Langlands, local Langlands,
etc. Introduce things from the start, though--do not assume the
reader knows category theory to begin with.
