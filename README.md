# Enough LaTex To get your report done

LaTex is perfect for creating proffesional reports with proffessional and good layouts. However, it can be intimadating either in terms of usage or learning. Here I am going to use a practical approach.

You are not learning LaTex in the void but rather in a very specific context which is writting reports. In my case, I am using it for writting end of year project report.

I am trying to make it a quick guide made by a begineer for fellow begineers.

***NOTE:*** If you have any suggestions, notes, or spotted mistakes, I would truly appreciate it if you note them out.

## Table of Contents

## What is Latex

Checking Latex Official website, we find this definition:

"*LaTeX is a high-quality typesetting system; it includes features designed for the production of technical and scientific documentation. LaTeX is the de facto standard for the communication and publication of scientific documents.*"

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

    - **Back Matter: Finishing the Document** d

The back matter usually consists of three main components: Appendices, the Bibliography, and (optionally) an Index.

#### **1. Appendices**

The appendix is for content that is too long or detailed for the main chapters, such as raw data, large code snippets, or survey questions.
In LaTeX, you simply use the `\appendix` command. This tells LaTeX to switch the numbering from numbers (Chapter 1, 2, 3) to letters (Appendix A, B, C).

```latex
\appendix
\chapter{Raw Data Tables}
\chapter{Source Code}

```

#### **2. Bibliography (References)**

This is perhaps the most important part of the back matter. Using a package like `biblatex`, you don't have to manually type your references. You just tell LaTeX where your `.bib` file is and where to print the list.

- **In the Preamble:**

```latex
\usepackage[style=authoryear]{biblatex} % Or style=numeric
\addbibresource{references.bib}

```

- **In the Back Matter:**

```latex
\printbibliography[heading=bibintoc, title={References}]

```

*(Note: `heading=bibintoc` ensures the References section appears in your Table of Contents.)*

#### **3. The Back Matter Structure**

Here is how the end of your `main.tex` file should look:

    ```latex
    % --- End of Main Chapters ---
    \appendix
    \include{appendices/appendix_A}
    \include{appendices/appendix_B}

    \backmatter % If using book class; otherwise just use a \clearpage
    \printbibliography[heading=bibintoc]

    \end{document}
    ```
4. ***Special Types of Pages***

## Explaining Latex Document types

## Why use `report` document type

## Typical Preamble explained in details

## List of Commands that you will need 90% of the time

## List of Libraries that you will need 90% of the time
