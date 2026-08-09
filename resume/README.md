# Resume

Single-page LaTeX resume for Anuj Joshi (AI/ML Engineer). Source lives in
`src/*.tex` (heading, experience, projects, skills, education, achievements)
wired together by `main.tex`.

## Prerequisites

- MiKTeX (or any TeX distribution providing `pdflatex`)

## Build to the Quartz content folder

Compiles to `build/` (keeps `content/` clean of `.aux`/`.log`) and copies the
final PDF directly into `content/Anuj-Joshi-Resume.pdf`, where the Quartz
Assets plugin serves it at `/Anuj-Joshi-Resume.pdf`.

```powershell
# from the resume/ folder
pdflatex -interaction=nonstopmode -halt-on-error -output-directory=build -jobname=Anuj-Joshi-Resume main.tex
pdflatex -interaction=nonstopmode -halt-on-error -output-directory=build -jobname=Anuj-Joshi-Resume main.tex
Copy-Item build\Anuj-Joshi-Resume.pdf ..\content\Anuj-Joshi-Resume.pdf -Force
```

## Checks

- Must stay **one page** — after editing, confirm with
  `pdftotext build\Anuj-Joshi-Resume.pdf - | Measure-Object -Line` (no page 2).
- The site links to the PDF from `content/index.md` and `content/Contact.md`.
