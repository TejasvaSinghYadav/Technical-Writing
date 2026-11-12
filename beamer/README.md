# Beamer

Beamer is a LaTeX document class for creating presentation slides. 

## 1. Minimal presentation

```latex
\documentclass{beamer}

\title{My Presentation}
\author{Your Name}
\date{\today}

\begin{document}
\begin{frame}
  \titlepage
\end{frame}

\begin{frame}{Main Points}
  \begin{itemize}
    \item First point
    \item Second point
  \end{itemize}
\end{frame}
\end{document}
```

## 2. Commands and environments

| Command / environment | Purpose |
|---|---|
| `\documentclass{beamer}` | Selects Beamer presentation class |
| `\title{...}` | Sets presentation title |
| `\author{...}` | Sets author |
| `\date{...}` | Sets date |
| `\begin{document}` / `\end{document}` | Starts / ends presentation |
| `\begin{frame}...\end{frame}` | Creates one slide |
| `\begin{frame}{Title}` | Creates a titled slide |
| `\titlepage` | Displays title, author, and date |
| `\begin{itemize}...\end{itemize}` | Creates bullet list |
| `\item` | Adds a list item |

## 3. Useful Beamer features to practise

- **Themes:** `\usetheme{Madrid}` changes the slide design.
- **Blocks:** `\begin{block}{Heading} ... \end{block}` highlights content.
- **Columns:** `columns` and `column` environments arrange content side by side.
- **Images:** `\includegraphics` inserts images (from `graphicx`).
- **Overlays:** `\pause` reveals content in stages.

These are useful extensions to practise; they are not all demonstrated in the supplied course notes.

## 4. Compile and design tips

Save as `presentation.tex` and compile with `pdflatex presentation.tex` or use Overleaf. Keep one main idea per slide, use short bullets, readable text, consistent layouts, and visuals only when they help explain the point.

