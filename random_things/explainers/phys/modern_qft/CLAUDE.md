# Writing instructions: Modern QFT lecture notes

Instructions for Claude when writing chapters of these notes. This is a living
document: when Will gives style feedback during a session, encode it here before
the session ends.

## What this project is

Lecture notes on the modern point of view on QFT (Seiberg / Shao / Witten /
Rychkov / Komargodski school). The document opens with the roadmap: an annotated
TOC of 12 parts / 62 chapters ("the QFT textbook of 2046") plus a library of 61
papers in `assets/` (indexed in `assets/README.md`). Chapters get written
incrementally, one per session, into `parts/` (see Repo mechanics for the file
layout).

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
   aux files (`.aux .log .out .toc .fls .fdb_latexmk .synctex.gz`, plus any stray
   `texput.log`; a `.gitignore` in this directory covers them). Update the status
   table below.

## Prose quality (the most important section)

The other explainers in this repo (`gauge_fields`, `comm_alg`) are
**anti-models**: Will considers them too terse, too rigid, over-boxed, and well
below good human writing on these subjects. Do not imitate their voice. (Their
box *environments* are the right ones to use — it's the prose between boxes that
failed.) This is also why Will restricted directory access during the TOC task:
he did not want those files contaminating the style.

**The model is Witten** (Will's directive, 2026-06-11: "the main person you
should strive to emulate is witten... the main key to his writing is that he
just gives reasons for everything, i think. he basically never leaves
something unsaid"). Write physics lecture notes, not an expository news
article. Two of Witten's expository papers are in `assets/` (1803.04993,
2112.11614) — **read a few pages before drafting each chapter to calibrate
the register.** What that register looks like: complete, unhurried sentences;
every claim accompanied by the reason it is true; every step explained as it
is taken ("Because H is bounded below by 0, the operator exp(iHu) is
holomorphic for u in the upper half plane. Thus the function g(u) is
holomorphic..."); explanatory parentheticals; "In other words, ..."; no
drama. Not dry does not mean punchy — look at literally any good physics
lecture notes. Concretely:

- Vary paragraph rhythm and length; let arguments breathe.
- Have a point of view: say what is important, what is a sideshow, what is
  genuinely confusing and why it confuses people.
- Transitions must do intellectual work (*why* are we moving here?), not just
  signpost.
- Kill LLM tells: formulaic section openers ("In this section, we will..."),
  relentless parallel sentence structure (especially runs of paragraphs that
  all close on the same beat — "strength, then caveat"), bullet lists where a
  paragraph belongs, empty summary paragraphs that re-say what was just said,
  hedging.

### Banned constructions (Will's I.2 notes, 2026-06-11 — do not reintroduce)

Will flagged ~15 sentences of the I.2 draft as the failure mode: "way too
punchy and motivational... stop writing a motivational pep talk and write a
set of physics notes." The construction classes, with flagged examples:

- **Dramatic sentence fragments:** "One analytic function; two orderings; two
  sides of a cut." / "Now for the third debt: structure."
- **Cute metaphor in place of statement:** "a single condition with a mirror
  in it", "a family every QFT bookkeeper must admit", "replaced by a blob",
  "discovery engine", "membership card", "load-bearing wall", "the OPE,
  derived and domesticated", "touch the world where path integrals converge".
- **Self-narrating asides:** "We flag it once, here, and trust it silently
  hereafter." / "an interlude on a question the reconstruction theorem begs."
- **Countdown/listicle sentences:** "Two facts elevate this from bookkeeping
  to a discovery engine.", "Three exhibits, in ascending order of
  consequence.", "Two reflections, one structural, one physical."
- **Quips standing in for content:** "a usable definition rather than a
  shrug", "as long as the other insertions keep their distance", "the growth
  condition is not decoration".

Plain declarative sentences carry the same content better. The deeper
failure behind the tics (Will): "you have the habit of referencing something
at an intuitive or shallow level and then confusing the reader." If a
sentence asserts a relation ("differences of orderings are commutators"),
display the equation that makes it precise, immediately; say *how* things
are related, not merely *that* they are.

### Anti-LLM-speak: lexical tics to ration (Will's directive, 2026-06-11)

These are the words and rhythms an LLM reaches for far more often than a human
writer does. Each is fine in isolation; the tell is *frequency* — a reader
starts noticing by the third or fourth occurrence on a page. The I.1/I.2 drafts
ran ~9 "deserves" and ~19 "honest(ly)" before a thinning pass; that is the
failure mode to pre-empt, not repeat.

- **Filler verbs that announce "here comes the next point":** *deserves /
  earns / merits / is worth* (a hard look, its own paragraph, recording,
  spelling out, advance billing). Usually the sentence is stronger with the
  scaffolding deleted — just make the point. If you need a few, vary them.
- **All-purpose intensifiers used to mean "I really mean it":** *honest /
  honestly / genuine / genuinely / actually / really / truly / proper(ly)*.
  Cut most; they almost never add information. ("a genuine inner product" =
  "an inner product".)
- **Throat-clearing paragraph openers:** *It is worth noting/emphasizing that*,
  *It pays to*, *Note that*, *Notice that*, *It is worth pausing on*. Start with
  the content instead.
- **Reversal-for-emphasis as a verbal habit:** *not a trick but an equivalent
  formulation*; *not X; it is Y*; *X is not A — it is B*. Genuinely good once or
  twice per chapter; mechanical when every third paragraph runs the pattern.
- **Em-dash overuse.** These notes lean hard on `---`. Often a comma, a colon,
  or a full stop is cleaner; reserve the dash for real interruptions.
- **"the X is the Y" equation-of-grandeur** ("locality is the subject", "the
  trace is the operator that knows about scale") — punchy once, a tic in bulk.
- **Self-audit before handing off.** Grep your own draft for your favourites
  (`grep -oc 'deserve\|honest\|genuine\|it is worth' chXX.tex`) and vary or cut
  the clusters. The target is variety, not a banned-word list — prose that does
  not read like it was generated.

## Emphasis, derivations, exercises (Will's I.2 notes, 2026-06-11)

- **Emphasize what is important.** Key definitions ("local operator",
  "primary", ...) go in `ddefinition` boxes, *with motivation*: say why this
  is the right definition and not some other. Don't bury a definition in
  mid-paragraph prose — Will flagged exactly this twice in one chapter.
- **Derive standard results.** Källén–Lehmann-level derivations are
  mandatory, not citable ("You obviously have to derive Kallen-Lehmann!
  What are you doing?!"). If the standard derivation is half a page, include
  it. This strengthens the never-hand-wave rule below.
- **Relate modern formulations to the standard textbook ones.** Examples
  from the I.2 round: point-splitting must be connected to mode normal
  ordering; the metric stress tensor to the canonical/Noether tensor; the
  K-annihilation definition of a primary to the transformation-law
  definition. The reader knows the textbook version; show explicitly how the
  modern version contains it.
- **Recall before use.** Recall what a Killing vector is before building
  charges from it; recall what a model is inside any exercise that uses it
  ("in the 2d free Dirac CFT" → give the action/propagator in the exercise).
  Exercises must be self-contained.
- **Never cite later sections to answer an exercise** — Will: "that's bad
  taste." Hints may point forward for context, never for the answer.
- **Explain why a tool is wanted before deriving it** (e.g. Ward identities:
  say what they are for — defining symmetry at correlator level, fixing
  dimensions, building charges — before the derivation).
- **Be concrete about the lattice/RG.** "Linearize the RG" requires an
  explicit blocking transformation, the eigenvalue equation displayed, and a
  measurable consequence (corrections to scaling) worked out. "Just not
  concrete enough" was the complaint.
- **Citation balance.** Do not lean repeatedly on one survey (Will: "stop
  citing Dedushenko so much... there is nothing really there"). Cite primary
  and classic sources (Streater–Wightman, Osterwalder–Schrader, Glimm–Jaffe,
  Wilson, Schwinger originals); keep survey citations to the reading list.
- **Standard notation.** OPE coefficients are $C_{ijk}$ / $\lambda_{ij\mathcal{O}}$
  with $i,j,k$ indices — never "$C_{12k}$"-style mixed number/letter indices.
- **Figures get the same scrutiny as prose.** Check rendered output for
  label collisions, and check the *physics* of the figure (the crossing
  figure showed two different configurations where one configuration with
  two spheres was meant).

## Voice and altitude

- **The chapter's thesis is its roadmap annotation, not its centerpiece
  calculation.** (Will's feedback on the I.2 draft, 2026-06-10.) Each chapter's
  roadmap paragraph states the actual claim ("the local operator content as
  primary data"); the opening must assert that claim in the first paragraph and
  the closing must deliver the verdict on it. Failure mode: letting the agreed
  centerpiece calculation organize the framing, so a reader would name the
  proof (e.g. "OPE convergence via Cauchy–Schwarz") rather than the thesis as
  the chapter's point. The centerpiece is the crown jewel, not the thesis.
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
| `ttechnique` | Technique (red) | reusable methods |

The `ps*` tcolorbox family (`psidea`, `pstheorem`, ...) exists in william.sty but
is not house style for explainers — don't use it.

Other useful macros: `\vocab{term}` for first use of every technical term;
`\noin`; `\op` (𝒪), `\enn` (𝒩), `\de` (path-integral measure), `\ket/\bra/\braket`,
`\tr`, `\lie{g}`, `\reals/\ints/\complex`; `\incgr{scale}{file}` /
`\wincgr{frac}{file}` for figures.

## LaTeX source style

Model the math source on Will's paper style in
`/Users/wlancer/Desktop/Research/Zohar/papers/myPaper/paper.tex`: plain,
human-written LaTeX, not decorative LLM TeX.

- Prefer `align`/`aligned` when a display has several lines or several
  related equations. Put `&` on relation signs (`=`, `\leq`, `\coloneqq`) or
  between grouped equations, as in the reference paper. A single short formula
  may remain in `equation`.
- Do not polish formulas with manual spacing commands. Avoid `\;`, `\,`,
  `\!`, `\quad`, and `\qquad` as visual decoration around equals signs,
  products, commutators, bras/kets, colons, or punctuation. Let TeX space
  ordinary math. Use explicit spacing only when it carries a standard semantic
  convention, such as a thin space before a differential in an integral.
- Do not use `\big`, `\Big`, `\bigg`, or `\Bigg` for delimiter sizing. Use
  plain delimiters when they are readable; use paired `\left...\right` when
  the delimiter must grow.
- Normal-ordering colons should be written without negative-spacing tricks:
  use `{:}\phi^2{:}` rather than `:\!\phi^2\!:`.
- Keep displays visually simple in the source: avoid bracket padding like
  `\Big[\, ... \,\Big]`, decorative spaces before punctuation, and
  alignment-by-spacing. If a formula needs visual structure, use line breaks
  and alignment tabs instead.

## Conventions

- **Metric signature: mostly-plus, (−,+,+,+). NON-NEGOTIABLE.** Training data
  skews heavily mostly-minus (Peskin), so treat every transcribed sign as
  suspect: re-derive key signs in mostly-plus rather than copying (e.g.
  `\mathcal{L} = -\frac{1}{2}(\partial\phi)^2 - \frac{1}{2}m^2\phi^2`, on-shell
  `p^2 = -m^2`). When a source uses mostly-minus or Euclidean signature, convert
  explicitly and double-check. Srednicki and Weinberg are mostly-plus references
  to crib conventions from. Much of the symmetry/CFT literature is Euclidean,
  where this is moot — but pin the Wick-rotation convention in the appendix.
- Use boldface for spatial vectors and momenta: write `\mathbf{x}`,
  `\mathbf{p}`, etc. Do not use `\vec`.
- Pin a conventions appendix as soon as the first calculation needs one
  (normalization of p-form gauge fields and their fluxes,
  orientation/η conventions, Dirac matrices). The generalized-symmetry literature is
  inconsistent — default to Shao's TASI conventions (2308.00747) for symmetry
  material and Simmons-Duffin (1602.07982) for CFT material.
- References: hyperlinked arXiv IDs (`\arxiv{...}`) = paper is in `assets/`;
  plain `\texttt{...}` IDs = not downloaded. Maintain this convention.
- New papers needed for a chapter: verify ID + title via the arXiv API
  (`https://export.arxiv.org/api/query?id_list=...`) before citing, download to
  `assets/` with the `ID_authors_short-title.pdf` naming pattern, then update
  **three** places: `assets/README.md` (incl. the paper count in its header),
  the roadmap's "The library" section in `frontmatter/roadmap.tex`, and the
  chapter's `\chreading`/`\chfurther` line. (The I.2 session updated only the
  README and the library desynced — caught and fixed 2026-06-10.) The paper
  count also appears in this file's "What this project is".

## Repo mechanics

- Everything for these notes lives in this directory; do not write elsewhere.
- william.sty is installed at `~/Library/texmf/...` — compilation just works.
- **File structure (since 2026-06-10):** `modern_qft.tex` is the master file
  (preamble, title page, `\part` declarations, `\input`s). The annotated TOC
  lives in `frontmatter/roadmap.tex`, with headings via `\roadpart`/`\roadchapter`
  so they consume no section counters; the conventions appendix is
  `frontmatter/conventions.tex`; chapters are `parts/partI/chXX.tex`. Chapters
  are `\section`s numbered `I.1, I.2, ...` (section counter resets per part);
  equations and boxes number within section. Exercises use the `exercise`
  theorem env with the grade as the optional argument (`\begin{exercise}[medium]`),
  plus `\hint{...}` and `\answ{...}`.
- **Cross-references are hand-written numbers** (`Part II.7`, `chapter I.4`),
  not `\ref`s — `\label`s exist only for equations/figures/exercises within a
  chapter. Part/chapter numbers are therefore load-bearing prose: any
  renumbering of the TOC requires a grep sweep over `parts/`,
  `frontmatter/roadmap.tex`, `assets/README.md`, and this file. The chapter
  count ("twelve parts, sixty-two chapters") is hardcoded in three places:
  the title page (`modern_qft.tex`), the roadmap premise, and this file.
- **Gotcha:** william.sty redefines `\v` (bold vectors), which silently breaks
  the háček accent (`\v{c}` in names like Mazáč) with a "\mathbf allowed only in
  math mode" error. The master preamble saves the original as `\latexcaron`
  *before* loading william.sty — use `\latexcaron{c}` for carons.
- Don't commit unless asked. `assets/` is ~93 MB — flag this if a commit is requested.

## Status

| Chapter | Title | Status |
|---|---|---|
| TOC | Annotated table of contents (12 parts, 62 ch.) | done 2026-06-09; reorganized 2026-06-10 (duality↔SUSY and scattering↔QI part swaps; new chapters II.2 TQFT, IV.6 resurgence, IV.7 hydrodynamics after later renumbering); expanded 2026-06-11 (IV.3 broken-symmetry EFT, VI.4 duality polarizations, VIII.4 finite density, IX.1 amplitudes; chapter-number hints refreshed) |
| I.1 | What is a quantum field theory? | merged and compiled 2026-06-10 |
| I.2 | Observables I: local operators | rewritten per Will's style notes (Witten register, derivations, definitions, figures) 2026-06-11; I.1 swept for same issues; compiled clean (~44 pp.) |
| I.3 | Observables II: defects and extended operators | drafted 2026-06-11 (centerpiece: KW disorder line built on the lattice, duality + phases + Kadanoff–Ceva fermion; AST su(2) line lattices; defect-CFT kinematics incl. displacement; defect Hilbert spaces); compiled clean, ~29 pp. (pp. 91–119); awaiting Will's altitude pass. Cited-not-downloaded (plain `\texttt`): 2112.10634, 1610.05780, hep-th/0612073, cond-mat/9505127, hep-th/0501015 — all IDs verified via arXiv API |
| I.4 | States, geometry, and cutting-and-gluing | not started |
| I.5 | Presentations, not definitions | not started |
| I.6 | Theory space and the renormalization group | not started |

Planned full calculations for Part I (agreed in advance, revisit per session):
I.2 OPE convergence via radial quantization; I.3 the Kramers–Wannier disorder
line constructed on the lattice; I.4 cylinder ↔ plane map and the Casimir
energy; I.5 the 3d Ising CFT presented four ways; I.6 the Wilson–Fisher fixed
point in d = 4 − ε done honestly.
