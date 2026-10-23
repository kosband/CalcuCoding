# CalcuCoding — interactive calculus notebooks

JupyterLite notebooks exploring first-year calculus. Python runs in each student's browser, without an account or a Python server.

## Open Chapter 2, Section 1

When the GitHub Pages workflow succeeds, open:

https://kosband.github.io/CalcuCoding/notebooks/index.html?path=Ch2_Sec1.ipynb

The PowerPoint/iSpring link should be this same address. Future notebook edits at the same path do not require changing the link.

## Repository structure

- `files/Ch2_Sec1.ipynb`: browser-adapted notebook, using `ipycc` for Turtle graphics
- `originals/Ch2_Sec1.ipynb`: original notebook, preserved without code edits
- `requirements.txt`: site-builder and browser widget dependencies
- `.github/workflows/deploy.yml`: GitHub Pages deployment workflow

## Publish / verify

1. Under **Settings → Pages**, select **GitHub Actions** as the source.
2. Open **Actions → Publish CalcuCoding JupyterLite** to verify a successful build.
3. Open the student link in a private browser window, run the `%pip install -q ipycc==0.1.1` cell, then the graphical cells.
4. Check each Turtle drawing and the numerical examples before distributing links.

The install is only in this Turtle lesson. It is not automatically run for every notebook.
The `ipycanvas` frontend is installed at site-build time.

Student edits persist locally in their browser and never modify the published original. A previously edited browser copy may need resetting to see teacher updates.

**Status:** Pilot deployment; graphical compatibility and GitHub Pages activation require verification.
