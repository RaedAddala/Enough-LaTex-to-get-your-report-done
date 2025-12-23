# Enough LaTex To get your report done

LaTex is perfect for creating proffesional reports with proffessional and good layouts. However, it can be intimadating either in terms of usage or learning. Here I am going to use a practical approach.

You are not learning LaTex in the void but rather in a very specific context which is writting reports. In my case, I am using it for writting end of year project report.

I am trying to make it a quick guide made by a begineer for fellow begineers.

***NOTE:*** If you have any suggestions, notes, or spotted mistakes, I would truly appreciate it if you note them out.

## Table of Contents

## What is Latex

Checking Latex Official website, we find this definition:

> "*LaTeX is a high-quality typesetting system; it includes features designed for the production of technical and scientific documentation. LaTeX is the de facto standard for the communication and publication of scientific documents.*"

As it is clear from this definition, LaTeX is a *document preparation system* used in **STEM** fields whether in reports, research papers, or technical books.

It is widely spread due to many factors, mainly:

- It is open source.
- It has a huge community.
- It proved its worth and quality.

## Why Latex for reports

Reports usually contain multiple chapters, equations, figures, references and bibliography. Latex handles these for you automatically, making writing reports smoother.

With LaTeX, you can divide reports into multiple files making it easier to manage long reports without making it more complex.

LaTeX automatically handles figures, tables, equations, and citations. So, you don’t need to worry about numbering or updating references manually.

Also it handles equations better than any other available option.

So, what you get with using LaTeX is a mature tooling that automates much of the work needed while producing high quality documents.

This is more than enough to consider LaTeX for any reports writing.

## Latex Project Overall structure

All LaTeX projects follow this structure

1. ***Document Class Declaration:*** Here we declare the type of document we will be using. This affects the overall structure and expectations, like default formatting and features:

    ```latex
    \documentclass[a4paper]{report}
    ```

2. ***Preamble (Definitions & Setup):*** Here we import all packages we need and define the metadata for our project. This section defines logical rules, tools, and configurations we'll use in the document. It includes:
    - Packages (capabilities you want, e.g., amsmath, graphicx)
    - Custom commands (macros)
    - Document metadata (title, author, date)

    ```latex
    \usepackage{graphicx}
    \title{My Report}
    \author{Jane Doe}
    ```

3. ***Document Body***: Everything inside `\begin{document} ... \end{document}` is where logical document components are declared. This includes different parts:
    - **`\frontmatter`:** Used at the beginning to *set up preliminary pages* like abstract, acknowledgments, table of contents with Roman numeral numbering. This is crucial for formal reports to distinguish front matter from the main body.
    - **`\mainmatter`:** Switches to Arabic numerals for the main body, starting from chapter 1. This ensures consistent numbering for the core content. It can be divided into several parts too, mainly:
        - **Sectioning Hierarchy:** LaTeX structures the content using hierarchical declarations. It defines the logical structure of your document’s content. It helps organize the material into nested levels of importance. Each level gets an automatic number (unless suppressed) and appears in the Table of Contents if desired. Here are the list commands related to Sectioning depending on the document class:

            | Command          | Purpose                                  | Available In Class    |
            | ---------------- | ---------------------------------------- | --------------------- |
            | `\part`          | Highest-level division                   | All classes           |
            | `\chapter`       | Major division (e.g., chapters in books) | `book`, `report` only |
            | `\section`       | Primary section within a chapter or part | All classes           |
            | `\subsection`    | Subdivision of a section                 | All classes           |
            | `\subsubsection` | Subdivision of a subsection              | All classes           |
            | `\paragraph`     | Minor subdivision (inline heading)       | All classes           |
            | `\subparagraph`  | Even finer subdivision                   | All classes           |

            Here is an example:

            ```latex
            \part{Fundamentals}
            \chapter{Introduction}
            \section{Problem Statement}
            \subsection{Scope}
            \subsubsection{Limitations}
            \paragraph{Historical Notes} This method was first...
            \subparagraph{Footnote} Further detail appears in...
            ```

            Here is its output:

            ```plaintext
            Part I     Fundamentals
            Chapter 1  Introduction
            1.1        Problem Statement
            1.1.1      Scope
            1.1.1.1    Limitations
                    Historical Notes. This method was first...
                    Footnote. Further detail appears in...
            ```

            While writing text, prefer using **`\paragraph` and `\subparagraph`** sparingly as they’re inline and often better handled with text formatting or lists. Also we should use **`\clearpage`** or **`\newpage`** after chapters to control layout and add separation.
        - **Floating Elements:** these are objects like *figures* and *tables* that are not locked to the exact position where you write them in the source code. Instead, LaTeX decides their final position based on layout rules to make your document look good and avoid awkward page breaks or spacing issues: ***They “float” to a position LaTeX deems optimal.***. They have a caption and a label. They are automatically numbered and can be included in a list of figures/tables.
        - **Environments:** are *functional blocks* that define the behavior and formatting of specific portions of your document. An environment is a pair of commands:

            ```latex
            \begin{environment_name}
            ... your content ...
            \end{environment_name}
            ```

            For example:

             ```latex
            \begin{itemize}
                \item First point
            \end{itemize}
            ```

            Types of Environments will be discussed further in the commands sections.

        - **Cross-referencing:** is a powerful LaTeX feature that enhances document structure, readability, and navigability, especially in long or technical documents like theses, articles, or reports. It allows you to **refer to numbered elements**. The process involves 2 steps: *Labeling* using `\label` and *Referencing* using `\ref`, `\pageref`, and `\nameref`.
        - **tables**
        - **Starred Versions, Unnumbered Headings**

    - In a professional report or thesis, the **Back Matter** is the section at the very end of your document. While the `\frontmatter` and `\mainmatter` commands are technically specific to the `book` class, the **concept** of Back Matter applies to all reports. It is where you put supplemental information that would clutter the main narrative.

    Here is how you handle it in a `report` document:

    - **Back Matter: Finishing the Document**: The back matter usually consists of three main components: Appendices, the Bibliography, and an Index:

        - **1. Appendices:** The appendix is for content that is too long or detailed for the main chapters, such as raw data, large code snippets, or survey questions. In LaTeX, you simply use the `\appendix` command. This tells LaTeX to switch the numbering from numbers (Chapter 1, 2, 3) to letters (Appendix A, B, C).

            ```latex
            \appendix
            \chapter{Raw Data Tables}
            \chapter{Source Code}
            ```

        - **2. Bibliography (References):** This is perhaps the most important part of the back matter. Using a package like `biblatex`, you don't have to manually type your references. You just tell LaTeX where your `.bib` file is and where to print the list:
        - *In the Preamble:*

            ```latex
            \usepackage[style=authoryear]{biblatex} % Or style=numeric
            \addbibresource{references.bib}
            ```

        - *In the Back Matter:*

            ```latex
            \printbibliography[heading=bibintoc, title={References}]
            ```

            *(Note: `heading=bibintoc` ensures the References section appears in your Table of Contents.)*

        - **3. The Back Matter Structure:** Here is how the end of your `main.tex` file should look:

            ```latex
            % --- End of Main Chapters ---
            \appendix
            \include{appendices/appendix_A}
            \include{appendices/appendix_B}

            \backmatter % If using book class; otherwise just use a \clearpage
            \printbibliography[heading=bibintoc]

            \end{document}
            ```

4. ***Special Types of Pages:***

In formal reports using the `report` class, certain pages are treated specially-often unnumbered, with Roman numeral paging, or formatted differently from the main content. These are typically part of the **front matter** (preliminary pages before the main chapters).

Unlike the `book` class, `report` does not have built-in `\frontmatter` and `\mainmatter` commands, but you can achieve similar behavior manually with `\pagenumbering{roman}` for front matter and `\pagenumbering{arabic}` for the main body.

Common special pages include:

- **Title Page**: Generated automatically with `\maketitle`. It is unnumbered and uses the `empty` page style by default.

    ```latex
    \title{Your Report Title}
    \author{Your Name}
    \date{\today}  % Or leave empty for no date
    \begin{document}
    \maketitle
    ```

- **Abstract**: A dedicated environment that places the content on its own page (due to the default `titlepage` behavior in `report`).

    ```latex
    \begin{abstract}
    Your summary of the report goes here. This is a concise overview of the purpose, methods, results, and conclusions.
    \end{abstract}
    ```

    To add it to the Table of Contents (optional):

    ```latex
    \addcontentsline{toc}{chapter}{Abstract}
    ```

- **Acknowledgments / Dedication**: These are not built-in but commonly added as unnumbered chapters.

    ```latex
    \chapter*{Acknowledgments} % unnumbered chapter
    \addcontentsline{toc}{chapter}{Acknowledgments}  % Optional: add to TOC
    I would like to thank...
    % Or for a dedication (centered, short):
    \clearpage
    \thispagestyle{empty}
    \vspace*{\fill}
    \begin{center}
    Dedicated to...
    \end{center}
    \vspace*{\fill}
    \clearpage
    ```

- **Table of Contents, List of Figures, List of Tables**: Automatically generated.

    ```latex
    \tableofcontents
    \listoffigures
    \listoftables
    ```

Typical front matter structure (with Roman numerals):

```latex

\begin{document}

\maketitle

\pagenumbering{roman}  % Start Roman numerals

\begin{abstract}

...

\end{abstract}

\addcontentsline{toc}{chapter}{Abstract}

\chapter*{Acknowledgments}

\addcontentsline{toc}{chapter}{Acknowledgments}

...

\tableofcontents

\listoffigures

\listoftables

\clearpage

\pagenumbering{arabic}  % Switch to Arabic for main content

```

These pages ensure your report has a professional, standardized layout while keeping the main body clean and consistently numbered.

You can use `\thispagestyle{empty}` or `\pagestyle{plain}` to control headers/footers on individual pages if needed.

## Explaining LaTeX Document Types

The first line of any LaTeX document is the **document class declaration**, which tells LaTeX what kind of document you're creating. This sets the overall layout, default formatting, available commands, and structure expectations.

```latex
\documentclass[options]{class}
```

Here, `class` is the type (e.g., `report`), and `[options]` are comma-separated settings like font size or paper type.

LaTeX provides several built-in classes, but the most common for technical and academic writing are `article`, `report`, and `book`. Since this guide focuses on writing reports (like project or thesis reports), we'll emphasize the `report` class while comparing it to the others.

### Comparison of Main Document Classes

| Class     | Description                                   |
|-----------|-----------------------------------------------|
| **article** | Short documents: journal articles, essays, homework, short reports |
| **report**  | Longer reports with chapters: theses, project reports, technical documents |
| **book**    | Full books, with front/back matter             |
| **memoir**  | Highly customizable class for books and complex documents, extending the book class with more built-in features |
| **moderncv**| Elegant class specifically designed for creating modern résumés (CVs) with various professional themes and layouts |

### Why `report` for Reports?

- It allows **chapters** (`\chapter{}`), perfect for dividing a long report into logical parts.
- Automatic **separate title page** and proper handling of abstracts.
- Single-sided by default (good for digital or one-sided printing), but you can add `twoside` if needed.
- No complex book features like automatic right-page chapter starts or built-in front/back matter switches, keeps things straightforward.

Example for a typical report:

```latex
\documentclass[12pt,a4paper]{report}
```

### Common Options (Applicable to article, report, book unless noted)

| Option          | Effect                                                                 | Default (varies by class) |
|-----------------|------------------------------------------------------------------------|---------------------------|
| `10pt`, `11pt`, `12pt` | Base font size                                                        | 10pt                     |
| `a4paper`, `letterpaper` | Paper size                                                            | letterpaper              |
| `oneside`, `twoside`    | Single- or double-sided layout (margins, headers)                     | oneside (article/report), twoside (book) |
| `onecolumn`, `twocolumn`| One or two columns                                                    | onecolumn                |
| `draft`, `final`        | Draft shows overfull boxes; final is clean                            | final                    |
| `openany`, `openright`  | Chapters start on next page or right-hand page (report/book only)     | openany (report), openright (book) |
| `titlepage`, `notitlepage` | Separate title page or not (article defaults to notitlepage)         | titlepage (report/book), notitlepage (article) |

Example with options:

```latex
\documentclass[11pt,a4paper,oneside,draft]{report}
```

For most beginner reports, start simple:

```latex
\documentclass[a4paper,12pt]{report}
```

You can always add options later. The class choice affects structure more than appearance, packages in the preamble can customize looks further.

If your report is very short (no chapters needed), `article` works fine. For a full thesis resembling a book, consider `book`. But for standard project/end-of-year reports, choose `report.

## Typical Preamble explained in details

The **preamble** is everything between the `\documentclass{}` line and `\begin{document}`. This is where you set up your document: load packages (extensions), define custom commands, and specify metadata like title, author, and date.

A well-organized preamble makes your project cleaner, more maintainable, and professional-looking.

Here is a realistic, beginner-friendly preamble for a typical report, followed by explanations:

```latex
\documentclass[a4paper,12pt,oneside]{report}

% === Page Layout & Typography ===
\usepackage[margin=1in]{geometry}        % Set consistent margins
\usepackage{parskip}                     % Add vertical space between paragraphs, removes indentation
\usepackage{microtype}                   % Improves typography: better kerning, hyphenation, and justification
\usepackage{setspace}                    % For line spacing control
\onehalfspacing                          % Or \doublespacing if required

% === Language & Encoding ===
\usepackage[utf8]{inputenc}              % Allow UTF-8 characters
\usepackage[T1]{fontenc}                 % Better font encoding
\usepackage[english]{babel}              % Language-specific hyphenation

% === Mathematics ===
\usepackage{amsmath}                     % Enhanced math environments
\usepackage{amssymb}                     % Extra math symbols
\usepackage{amsthm}                      % Theorem-like environments (optional)

% === Figures & Tables ===
\usepackage{graphicx}                    % Include images
\usepackage{float}                       % Better float control (e.g., [H])
\usepackage{caption}                     % Better caption styling
\usepackage{subcaption}                  % Subfigures and subtables
\usepackage{booktabs}                    % Professional tables (toprule, midrule, etc.)
\usepackage{array}                       % Enhanced column types in tables (e.g., >{\centering\arraybackslash}p{3cm})

% === References & Citations ===
\usepackage[style=numeric, sorting=none]{biblatex}
\addbibresource{references.bib}          % Your .bib file

% === Hyperlinks & PDF Features ===
\usepackage[hidelinks]{hyperref}         % Clickable links, removes red boxes
\usepackage{cleveref}                    % Smart referencing (e.g., "Figure 1" instead of just "1")

% === Miscellaneous ===
\usepackage{todonotes}                   % For \todo{} notes during drafting
\usepackage{lipsum}                      % Dummy text (remove in final version)

% === Document Metadata ===
\title{Your Project Report Title}
\author{Your Full Name}
\date{\today}                            % Or specify manually, e.g., December 2025

\begin{document}
```

### Key Sections Explained

- **Page Layout**: `geometry` gives you full control over margins. 1-inch margins are standard for many institutions.
- **Typography Improvements**:
  - `parskip`: Adds space between paragraphs and removes first-line indentation—gives a cleaner, modern look (common in reports and theses).
  - `microtype`: Subtly improves text justification, hyphenation, and character spacing. It makes your document look more professional without any extra effort.
- **Line Spacing**: Many universities require 1.5 or double spacing—`setspace` handles this easily.
- **Mathematics**: `amsmath` is essential for aligned equations, cases, etc. `amssymb` adds symbols like `\mathbb`, `\mathcal`.
- **Figures & Tables**: `graphicx` for images, `booktabs` for clean tables, `subcaption` for side-by-side figures, `array` for advanced column formatting in tables.
- **Bibliography**: `biblatex` + a `.bib` file is the modern, powerful way to manage references.
- **Hyperlinks**: `hyperref` makes your PDF interactive (clickable TOC, references, URLs). Load it near the end (except for `cleveref`, which should come after).
- **Metadata**: Always define `\title`, `\author`, and `\date` before `\maketitle`.

**Tip**: Comment your preamble generously (using `%`) so you remember why each package is there. You can remove unused packages later to keep the document clean.

## List of Commands that you will need 90% of the time

These are the core LaTeX commands you’ll use constantly in a report.

| Category              | Command                          | Usage Example                                      | Purpose |
|-----------------------|----------------------------------|----------------------------------------------------|---------|
| **Sectioning**        | `\chapter{}`                     | `\chapter{Introduction}`                           | Starts a new chapter |
|                       | `\section{}`                     | `\section{Methodology}`                            | Major section |
|                       | `\subsection{}`                  | `\subsection{Data Collection}`                     | Sub-section |
|                       | `\subsubsection{}`               | `\subsubsection{Analysis Tools}`                   | Deeper level |
| **Text Formatting**   | `\textbf{}`                      | `\textbf{bold text}`                               | Bold |
|                       | `\textit{}`                      | `\textit{italic text}`                             | Italic |
|                       | `\emph{}`                        | `\emph{emphasized text}`                           | Semantic emphasis (usually italic) |
| **Lists**             | `\begin{itemize}` / `\item`       | Bullet points                                      | Unordered list |
|                       | `\begin{enumerate}` / `\item`    | Numbered list                                      | Ordered list |
|                       | `\begin{description}` / `\item[]`| Definition-style list                              | Key-value list |
| **Math (Inline)**     | `$...$`                          | `$E = mc^2$`                                       | Inline math |
| **Math (Display)**    | `\[ ... \]` or `\begin{equation}` | Displayed, numbered equation                       | Centered math |
| **Figures**           | `\includegraphics[]{}`          | `\includegraphics[width=0.8\textwidth]{fig.png}`   | Insert image |
|                       | `\caption{}`                     | Caption for figure/table                            | |
|                       | `\label{}`                       | `\label{fig:setup}`                                | For cross-referencing |
|                       | `\ref{}`                         | See Figure `\ref{fig:setup}`                       | Reference |
| **Tables**            | `\begin{tabular}{}`              | Create table grid                                  | |
|                       | `\toprule`, `\midrule`, `\bottomrule` | From `booktabs` for clean lines                | Professional lines |
| **Other**             | `\maketitle`                     | Generates title page                               | |
|                       | `\tableofcontents`               | Auto-generates TOC                                 | |
|                       | `\listoffigures`                 | List of figures                                    | |
|                       | `\listoftables`                  | List of tables                                     | |
|                       | `\clearpage` or `\newpage`       | Force page break                                   | |
|                       | `\todo{}`                        | `\todo{Fix this section}`                          | Draft note (with todonotes) |

**Pro Tip**: Always pair `\label{}` with the element you want to reference, and place it *after* `\caption{}` inside figures/tables.

## List of Libraries that you will need 90% of the time

These packages cover the vast majority of report needs.

| Package          | Purpose                                           | Why You Need It |
|------------------|---------------------------------------------------|----------------|
| `geometry`       | Control margins and page layout                   | Consistent, professional margins |
| `parskip`        | Space between paragraphs, no indent               | Modern, clean paragraph separation |
| `microtype`      | Better typography (kerning, justification)        | Makes text look noticeably more polished |
| `setspace`       | Set line spacing (1.5 or double)                  | Often required by guidelines |
| `graphicx`       | Include and scale images                          | Essential for figures |
| `float`          | Add `[H]` placement specifier for floats          | Keep figures/tables exactly where you want |
| `caption` & `subcaption` | Better captions and subfigures                    | Professional figure layouts |
| `booktabs`       | Clean, publication-quality tables                  | Replaces ugly `\hline` |
| `array`          | Advanced table column types (centered p-columns, etc.) | More control over table formatting |
| `amsmath`, `amssymb` | Advanced math environments and symbols         | Proper equation formatting |
| `biblatex`       | Modern bibliography management                    | Automatic references and citations |
| `hyperref`       | Clickable links in PDF                            | Interactive document |
| `cleveref`       | Smart cross-references (e.g., "Section 2" automatically) | Cleaner writing |
| `todonotes`      | Inline todo notes during drafting                 | Great for revisions |

**Beginner Recommendation**: Start with these packages. Only add more when you hit a specific need (e.g., `listings` for code, `siunitx` for units, `glossaries` for acronyms).

With this setup, you can produce a clean, professional, fully-featured report without getting overwhelmed!
