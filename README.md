# Template repository for the manuscript portion of an overleaf project

## Setup

1. Create both an analysis and [manuscript](https://github.com/casey-cohort/template-overleaf-manuscript) repository from the templates. 
1. Go to [Overleaf](https://www.overleaf.com/project) click "New project" 
then "Import from Github". 
1. Update README file to reflect your project.

This template ships as a self-contained tutorial: it compiles as-is (a worked
wildfire/PSPS example) and walks through the LaTeX features you'll need. The
`sections/00_outline`, `00b_cheatsheet`, and `00c_exampletitle` files are the
tutorial scaffolding — delete them and clear out the example content once you
start your own manuscript.

## Usage

Once set up, you should be able to interact with your manuscript entirely through 
Overleaf. When you push changes to the `tables_figures` and `tex` directories
in your analysis repository, they will update in this repository automatically.

Pull those updates into Overleaf by clicking the Integrations tab on the left panel
and then "Sync with a Github repository". 

### Dynamic text

Values written to `tex/analysis-values.tex` in your analysis repo are synced here
to `tex_sync/analysis-values.tex` (already `\input` at the top of `main.tex`) and
can be invoked in the manuscript with `\nameOfItem`. A committed placeholder copy
lets the template compile before the first sync; it is overwritten on each sync.

If you wish to organize your dynamic values into multiple `.tex` files, make sure
to add the additional file names at the header of `main.tex`. 

E.g. if instead of writing out a single file `tex/analysis-values.tex` in your
analysis repo you choose to write out `tex/abstract_vals.tex`,
`tex/introduction_vals.tex`, etc., you'd need to include the following in `main.tex`. 

```
\input{tex_sync/abstract_vals.tex}
\input{tex_sync/introduction_vals.tex}
...
```

### Dynamic Tables and Figures

Graphics/figures and tex tables generated and written to `tables_figures` in your analysis repo
will appear in the `tables_figures_sync` in Overleaf once sync'ed. Static images you add by
hand (logos, photos, diagrams not produced by the analysis) go in `images/` instead — both
directories are on the `\graphicspath`, so `\includegraphics` finds figures in either.

Simply include figures as you would any image using the local path, e.g. 

```
\includegraphics[width=\linewidth]{tables_figures_sync/scatterplot.png}
```

If you generated a tex table in your analysis repo, include it inline in your tex manuscript 
using the `\input` command. 

```
\input{tables_figures_sync/table1.tex}
```
