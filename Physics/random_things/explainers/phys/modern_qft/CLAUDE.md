# Writing instructions: Modern QFT lecture notes

Instructions for Claude when writing chapters of these notes. This is a living
document: when Will gives style feedback during a session, encode it here before
the session ends.

## What this project is

Lecture notes on the modern point of view on QFT (Seiberg / Shao / Witten /
Rychkov / Komargodski school). `modern_qft.tex` currently contains the roadmap:
an annotated TOC of 12 parts / 55 chapters ("the QFT textbook of 2046") plus a
library of 46 papers in `assets/` (indexed in `assets/README.md`). Chapters get
written incrementally, one per session.

**Writing order (Will's decision):** Part I first, chapter by chapter (I.1 → I.6).
Reassess order after Part I.

**Target reader:** a graduate student who knows Peskin-level QFT (canonical
quantization, path integrals, perturbative renormalization, basic group theory).
Do NOT assume CFT, category theory, SUSY, or condensed-matter background —
build each from scratch when first needed. Build things from scratch, even if
the reader "should know them"--it is useful to see basically everything from the
modern perspective.

**Err on the side of explaining too much rather than too little.** Re-explaining
standard material in modern language is always welcome; terseness is the failure
mode here, not length. Re-prompting for more explanation after the fact is costly
and annoying — default to expansive.

## Session workflow (one chapter per session)

1. Read the chapter's key papers from `assets/` before drafting.
2. Agree with Will *before drafting*: the 3–5 worked examples, which derivations
   are done in full vs. cited, and a rough length expectation (err long —
   over-explaining beats re-prompting).
3. Draft motivation-first. Exercises woven in as the draft develops.
4. Self-review pass before handing off: reread the draft, fix altitude problems,
   check the box-policy rules below, verify citations against the PDFs. (Will has
   explicitly asked for review-and-improve-your-own-draft before.)
5. Will marks altitude errors (too terse / too encyclopedic). Encode the feedback here.
6. Compile (`pdflatex`, twice for refs), fix warnings and overfull boxes, delete
   aux files (`.aux .log .out .toc`). Update the status table below.

## Prose quality (the most important section)

The other explainers in this repo (`gauge_fields`, `comm_alg`) are
**anti-models**: Will considers them too terse, too rigid, over-boxed, and well
below good human writing on these subjects. Do not imitate their voice. (Their
box *environments* are the right ones to use — it's the prose between boxes that
failed.) This is also why Will restricted directory access during the TOC task:
he did not want those files contaminating the style.

Aspire instead to the best human lecture notes in theoretical physics — the
register of Tong's lecture notes, Witten's expository essays, the strongest TASI
write-ups: prose with narrative momentum and a visible author who makes choices
and explains why. Concretely:

- Vary paragraph rhythm and length; let arguments breathe.
- Have a point of view: say what is important, what is a sideshow, what is
  genuinely confusing and why it confuses people.
- Transitions must do intellectual work (*why* are we moving here?), not just
  signpost.
- Kill LLM tells: formulaic section openers ("In this section, we will..."),
  relentless parallel sentence structure, bullet lists where a paragraph
  belongs, empty summary paragraphs that re-say what was just said, hedging.

## Voice and altitude

- **Motivation first.** Every chapter opens with the question it answers and why
  the reader should care — before any formalism. Same rule for major sections.
- **Exposition is welcome, but it must have a point.** Introductory and
  conceptual sections may be mostly prose — that's fine — but their conceptual
  points should be made *with* equations, not around them. Calculations appear
  where they genuinely illuminate; no quota, but no chapter of pure words either.
- **Lighthouse examples** (recur throughout the notes; solve completely on first
  appearance, reference thereafter):
  1. 2d Ising model + Majorana chain (symmetry, Kramers–Wannier, the lattice)
  2. 3d Ising CFT (bootstrap, defects, fuzzy sphere)
  3. Maxwell and Yang–Mills in 4d (higher-form symmetry, θ, line operators)

  **Anti-over-indexing warning:** these are threads to reach for *when natural*,
  not a quota. LLMs over-use enumerated examples like these. If a different
  example serves a chapter better, use it — fresh examples are encouraged.
- **The new canon of examples.** A core selling point of these notes (Will's
  observation): modern QFT runs on a canon of simple, obvious examples that no
  textbook collects — the Schwinger model / QED₂ and its θ-dependence, the
  compact boson, Z_N lattice gauge theory, CP^{N−1}, adjoint QCD₂, Maxwell at θ
  in various dimensions, Villain-form models, the Majorana chain, the X-cube...
  These are often *easier* than the old canon (φ⁴ loops, tree-level QED
  scattering) — they just live only in papers. Prefer them, and when one
  appears, work it honestly: these notes should be among the first places this
  canon is assembled pedagogically.
- **Never hand-wave silently.** Either derive it, or say explicitly "we cite, not
  derive" with the reference. Flag any assertion taken on faith.
- **Exercises**: graded intra-text exercises (easy / classic / medium / thinker)
  at a steady pace through the chapter, plus an end-of-chapter set. Every
  exercise gets at least a hint; calculational ones get answers.
- **Citations**: inline source citations as footnotes pointing to specific
  papers/sections (footnotes work inside the mdframed boxes). Read the actual
  PDFs in `assets/` (`pdftotext` is at `/opt/homebrew/bin`) rather than citing
  from memory. Chapters end with an annotated reading list; flag book-length
  references separately (Will buys books; Claude pulls papers).

## Box policy (Will's explicit feedback — do not violate)

Boxes replace theorem environments and mark key ideas, but **prose carries the
document; boxes punctuate it**. The known failure mode is a chapter that is only
boxes with no connective tissue. Concrete rules:

1. Boxes must not substitute for prose. Adjacent boxes are occasionally fine when
   the flow is natural (a remark leading into an example, say); what is not fine
   is the `gauge_fields.tex` failure mode — stacked boxes carrying the whole
   argument with no connective tissue. When in doubt, write the connecting
   paragraph.
2. Budget ≈1 box per page on average; never more than 2 on a page.
3. A box must be *referenceable*: if the text would never later say "recall
   Definition 2.3" or "by the Idea above", it shouldn't be a box.
4. Derivations live in prose + display math, not in boxes. Exception:
   `eexample` may contain a self-contained worked calculation.
5. Delete-test: if all boxes were removed, the chapter should still read as a
   connected (if gappy) essay — not as orphaned fragments.

## Box environments (from william.sty — the mdframed family; house style)

Syntax: `\begin{eexample}[Optional Title] ... \end{eexample}`; numbered within section.

| Environment | Renders as | Use for |
|---|---|---|
| `eexample` | Example (red) | worked examples — the workhorse |
| `ddefinition` | Definition (blue) | crisp definitions of new objects |
| `iintuition` | Intuition (red) | the physical picture behind a formal statement |
| `iidea` | Idea (blue) | a key conceptual move, quotable |
| `ttheorem` | Theorem (blue) | sharp results with hypotheses |
| `pproposition` | Proposition (blue) | smaller sharp results |
| `eequation` | Equation (yellow) | a single central formula worth framing |
| `nnote` | Note (black sidebar) | caveats, scope warnings |
| `reemark` | Remark (purple sidebar) | asides, history, cross-references |
| `qquestion` | Question (green sidebar) | driving questions opening a section |
| `ppreview` | Preview (pink) | forward pointers to later parts |
| `iintuition`/`ttechnique` | Technique (red) | reusable methods |

The `ps*` tcolorbox family (`psidea`, `pstheorem`, ...) exists in william.sty but
is not house style for explainers — don't use it.

Other useful macros: `\vocab{term}` for first use of every technical term;
`\noin`; `\op` (𝒪), `\enn` (𝒩), `\de` (path-integral measure), `\ket/\bra/\braket`,
`\tr`, `\lie{g}`, `\reals/\ints/\complex`; `\incgr{scale}{file}` /
`\wincgr{frac}{file}` for figures.

## Conventions

- **Metric signature: mostly-plus, (−,+,+,+). NON-NEGOTIABLE.** Training data
  skews heavily mostly-minus (Peskin), so treat every transcribed sign as
  suspect: re-derive key signs in mostly-plus rather than copying (e.g.
  `\mathcal{L} = -\frac{1}{2}(\partial\phi)^2 - \frac{1}{2}m^2\phi^2`, on-shell
  `p^2 = -m^2`). When a source uses mostly-minus or Euclidean signature, convert
  explicitly and double-check. Srednicki and Weinberg are mostly-plus references
  to crib conventions from. Much of the symmetry/CFT literature is Euclidean,
  where this is moot — but pin the Wick-rotation convention in the appendix.
- Pin a conventions appendix as soon as the first calculation needs one
  (normalization of p-form gauge fields and their fluxes,
  orientation/η conventions, Dirac matrices). The generalized-symmetry literature is
  inconsistent — default to Shao's TASI conventions (2308.00747) for symmetry
  material and Simmons-Duffin (1602.07982) for CFT material.
- References: hyperlinked arXiv IDs (`\arxiv{...}`) = paper is in `assets/`;
  plain `\texttt{...}` IDs = not downloaded. Maintain this convention.
- New papers needed for a chapter: verify ID + title via the arXiv API
  (`https://export.arxiv.org/api/query?id_list=...`) before citing, download to
  `assets/` with the `ID_authors_short-title.pdf` naming pattern, update
  `assets/README.md`.

## Repo mechanics

- Everything for these notes lives in this directory; do not write elsewhere.
- william.sty is installed at `~/Library/texmf/...` — compilation just works.
- When chapters start accumulating, propose splitting into `parts/partI/chXX.tex`
  with `\input`; until then keep things simple.
- Don't commit unless asked. `assets/` is ~93 MB — flag this if a commit is requested.

## Status

| Chapter | Title | Status |
|---|---|---|
| TOC | Annotated table of contents (12 parts, 55 ch.) | done 2026-06-09 |
| I.1 | What is a quantum field theory? | not started |
| I.2 | Observables I: local operators | not started |
| I.3 | Observables II: defects and extended operators | not started |
| I.4 | States, geometry, and cutting-and-gluing | not started |
| I.5 | Presentations, not definitions | not started |
| I.6 | Theory space and the renormalization group | not started |

Planned full calculations for Part I (agreed in advance, revisit per session):
I.2 OPE convergence via radial quantization; I.3 the Kramers–Wannier disorder
line constructed on the lattice; I.4 cylinder ↔ plane map and the Casimir
energy; I.5 the 3d Ising CFT presented four ways; I.6 the Wilson–Fisher fixed
point in d = 4 − ε done honestly.
