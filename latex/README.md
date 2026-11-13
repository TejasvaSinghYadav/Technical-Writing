# LaTeX

LaTeX is a document-preparation system for technical and scientific writing. It is useful for structured reports, equations, tables, figures, references, and consistent page layout.

## 1. Basic document

```latex
\documentclass[12pt,a4paper]{article}
\usepackage{graphicx}
\title{Hello, World!}
\author{Your Name}
\date{\today}

\begin{document}
\maketitle
\begin{abstract}
A short summary.
\end{abstract}
\section{Introduction}
Write your content here.
\end{document}
```

- `\documentclass[options]{class}` selects the document type and options.
- Classes in the notes: `article`, `report`, `book`, `letter`, `exam`, `beamer`.
- Options include `12pt`, `11pt`, `a4paper`, `letterpaper`, `twocolumn`.
- `\usepackage{...}` loads extra features; `%` starts a comment.
- Compile with `pdflatex filename.tex` (the notes also show `pdflatex test`).

## 2. Title, text and structure

| Command | Purpose |
|---|---|
| `\title{...}` / `\author{...}` / `\date{...}` | Define title, author, date |
| `\today` / `\maketitle` | Today's date / print title |
| `\section{...}` / `\subsection{...}` / `\subsubsection{...}` | Headings |
| `\section*{...}` | Unnumbered section |
| `abstract` environment | Abstract |
| `\emph{...}` / `\textbf{...}` | Emphasis / bold |
| `\itshape` / `\bfseries` | Italic / bold font switches |
| `\noindent` / `\par` | No paragraph indent / end paragraph |
| `\\` / `\linebreak` | Line break |
| `\smallskip` / `\vspace{...}` / `\hspace{...}` | Add spacing |
| `\newpage` / `\pagebreak` | Start a new page |
| `\clearpage` | New page after pending floats are placed |
| `\mbox{...}` | Keep content together on one line |
| `\setcounter{section}{3}` | Set section counter; next section is 4 |

Text-size commands: `\tiny`, `\scriptsize`, `\footnotesize`, `\small`, `\normalsize`, `\large`, `\Large`, `\LARGE`, `\huge`, `\Huge`.

Alignment environments: `flushleft`, `center`, `flushright`.

List environments: `itemize` (bullets), `enumerate` (numbered), `description` (label-description). Use `\item` for each entry. The `enumitem` package and `\setlist[itemize]{label=\textbullet,leftmargin=*}` customize lists.

## 3. Mathematics

Use `$...$` or `\(...\)` for inline maths and `\[...\]` for centered, unnumbered display maths.

| Command / environment | Purpose |
|---|---|
| `\frac{a}{b}` / `\sqrt{x}` | Fraction / square root |
| `\sum_{i=1}^{n}x_i` / `\prod_{k=1}^{m}k` | Sum / product |
| `\int_0^1 x\,dx` | Integral |
| `\binom{n}{k}` | Binomial coefficient |
| `\alpha`, `\beta`, `\gamma`, `\delta`, `\lambda`, `\pi`, `\theta` | Greek letters |
| `\leq`, `\geq`, `\neq`, `\approx`, `\infty` | Comparison and special symbols |
| `\cup`, `\cap` | Set union / intersection |
| `\times`, `\otimes`, `\oplus` | Binary operators |
| `\left(`, `\right)` | Automatically sized delimiters |
| `\mathrm{}`, `\mathbf{}`, `\mathcal{}`, `\mathfrak{}` | Math font styles |
| `\quad` | Horizontal spacing |

Math environments shown: `equation`, `displaymath`, `align*`, `gather*`, `multline*`, `array`, `matrix`, `pmatrix`, `bmatrix`, `Bmatrix`, `vmatrix`, `Vmatrix`, `smallmatrix`. Many are provided by `amsmath`.

## 4. Tables

Use `tabular` for rows and columns. Column alignment: `l` (left), `c` (center), `r` (right).

```latex
\begin{tabular}{|c|c|}
\hline
Name & Marks \\
\hline
Bob & 85 \\
\hline
\end{tabular}
```

- `&` separates cells; `\\` ends a row; `\hline` draws a horizontal rule.
- `table` environment creates a floating table; `\centering` centers it.
- `\caption{...}` adds a caption; `\label{...}` creates a reference target.
- `\usepackage{colortbl}` enables coloured table cells/rows/columns.
- `\setlength{\arrayrulewidth}{0.5mm}` changes border thickness.
- `\setlength{\tabcolsep}{18pt}` changes horizontal cell padding.
- `\renewcommand{\arraystretch}{1.5}` increases row height.

## 5. Figures and images

Load `graphicx`, then use `\includegraphics`.

```latex
\usepackage{graphicx}
\begin{figure}[h]
  \centering
  \includegraphics[width=0.5\textwidth]{image.png}
  \caption{Sample figure}
  \label{fig:sample}
\end{figure}
See Figure~\ref{fig:sample}.
```

Other commands/options from the notes:
- `\includegraphics{file_name}` inserts an image.
- `\includegraphics[width=...]{file_name}` sets width.
- `\includegraphics[angle=30]{file_name}` rotates an image.
- `\scalebox{0.5}{...}` scales content.
- `\centering` centers the figure.
- `\label{...}` and `\ref{...}` label and refer to it.
- `sidewaysfigure` (with `rotating`) creates a rotated figure.
- `\subfigure` and `\epsfig` are also demonstrated in the slides as older methods for arranging EPS images.

Placement options such as `[h]`, `[t]`, and `[ht]` suggest where a floating figure/table should appear.

## 6. References and bibliography

- `\label{key}` defines a marker.
- `\ref{key}` prints the numbered reference.
- `\pageref{key}` prints the page number.
- `\cite{key}` inserts a citation.
- `thebibliography` with `\bibitem{key}` defines bibliography entries.
- `\bibliographystyle{...}` and `\bibliography{...}` are shown for BibTeX.

## 7. Colour, fonts and page layout

**Colour** (`xcolor`):
- `\textcolor{blue}{text}` colours text.
- `{\color{red} text}` changes colour within a group.
- `\colorbox{yellow}{text}` adds a background.
- `\fcolorbox{red}{yellow}{text}` adds a coloured frame and background.
- `\pagecolor{yellow!10}` changes page background.

**Fonts** (`fontspec`, normally with XeLaTeX or LuaLaTeX):
- `\setmainfont{Georgia}`, `\setsansfont{Arial}`, `\setmonofont{Courier New}`.
- `\textsf{...}` uses sans-serif; `\texttt{...}` uses monospaced text.

**Margins and headers:**
- `geometry` package with `\geometry{left=2.5cm,right=2.5cm,top=2.5cm}` sets margins.
- `\pagestyle{empty}`, `plain`, `headings`, or `fancy` selects page style.
- With `fancyhdr`: `\fancyhf{}` clears fields; `\fancyhead[L]{...}`, `\fancyhead[C]{...}`, `\fancyhead[R]{...}` set headers; `\fancyfoot[C]{\thepage}` sets a centered page number.
- `\thepage` inserts the current page number.
- Other layout commands shown: `\setlength`, `\parindent`, `\parskip`, `\sectionfont`, and `\subsectionfont` (with `sectsty`).

## 8. Picture environment and drawing

The `picture` environment draws simple diagrams. Coordinates and dimensions are based on `\unitlength`.

- `\setlength{\unitlength}{...}` sets drawing units.
- `\begin{picture}(width,height)(x_offset,y_offset)` starts a picture.
- `\put(x,y){...}` places an object.
- `\line(dx,dy){length}` draws a line; `\vector(dx,dy){length}` draws an arrow.
- `\circle{diameter}`, `\oval(width,height)`, `\framebox(width,height){text}`, `\makebox(width,height){text}` draw/place shapes or text.
- `\dashbox{dash_length}(width,height){text}` draws a dashed box.
- `\multiput(x,y)(dx,dy){number}{object}` repeats an object at regular offsets.
- `\linethickness{...}` and `\thicklines` change line thickness.
- `\fboxrule` and `\fboxsep` control frame thickness and padding.
- `\shortstack{...}` stacks lines of text.

## 9. Other

- `report` and `book` support chapters. In `book`, `\frontmatter`, `\mainmatter`, `\backmatter` separate front matter, main content, and back matter.
- `letter` uses `\address`, `\signature`, `letter`, `\opening`, and `\closing`.
- `exam` uses `questions`, `\question`, `choices`, and `\choice`.
- `beamer` uses `frame` environments for slides; see the Beamer README.

Keep the `.tex` source with its compiled PDF. Some commands require packages, and references may need another compilation pass.

go back:[Home](./README.md)
