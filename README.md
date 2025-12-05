#  LaTeX Scientific Writing Sessions

This repository contains all the source files and examples used in our ***LaTeX*** code-along sessions for **scientific document preparation**. These sessions are designed to help users master the tools and techniques necessary to create professional, publication-ready manuscripts, reports, and theses.

---

##  Prerequisites and Setup

To effectively use and compile the files in this repository, you need a complete ***LaTeX*** distribution installed on your system. We recommend **MiKTeX** for Windows, and it is also available for macOS and Linux.

### 1. Install LaTeX Distribution

* **MiKTeX (Recommended):** Download and install the **MiKTeX Console**.
    * *Ensure you install the **Complete** distribution* if given the option, or select the **"Always install missing packages on the fly"** option during setup. This is crucial for handling the various packages used in scientific writing.
* **Alternative for macOS/Linux:** **TeX Live** is the standard distribution.
    * *Note:* Ensure your TeX Live installation is up-to-date, as older versions may lack necessary packages.

### 2. Install a ***LaTeX*** Editor (Optional but Recommended)

While you can edit the files in any text editor, a dedicated \LaTeX{} editor enhances the experience with features like syntax highlighting, structure view, and integrated compilation.

* **Recommended Editors:**
    * **VS Code** with the ***LaTeX*** Workshop extension.
    * **TeXstudio** (Cross-platform).
    * **Overleaf** (Online editor, excellent for collaboration).

---

##  Compiling the ***LaTeX*** Code

The files in this repository are compiled using the ***PDF-LaTeX*** engine, which is part of the MiKTeX distribution.

### A. Command Line Compilation (Recommended Method)

For the most control, you can compile the documents directly from your terminal or command prompt.

1.  **Navigate to the Directory:** Open your terminal and change the directory to the folder containing the `.tex` file you want to compile (e.g., `cd path/to/session1`).
2.  **Run ***LaTeX:*** Execute the following command:

    ```bash
    pdflatex your_document_name.tex
    ```

3.  **Required Passes:** For documents that contain **bibliographies (with BibTeX/Biber)**, **tables of contents**, or **cross-references**, you typically need to run the compiler multiple times in a specific sequence:

| Step | Command | Purpose |
| :--- | :--- | :--- |
| **1** | `pdflatex your_document_name.tex` | Generates auxiliary files (`.aux`, `.toc`, etc.) |
| **2** | `biber your_document_name` **OR** `bibtex your_document_name` | Processes the bibliography and citation data |
| **3** | `pdflatex your_document_name.tex` | Incorporates the citation list and resolves references |
| **4** | `pdflatex your_document_name.tex` | Resolves all final references (ToC, page numbers, etc.) |

***Example for a typical scientific paper:***
```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
