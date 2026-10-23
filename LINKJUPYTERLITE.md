# CalcuCoding: browser-based Python notebooks

A small, free JupyterLite site intended to be linked from PowerPoint/iSpring.
Students run Python 3, NumPy, matplotlib, and compatible Turtle graphics in their browsers.
No student accounts or Python computation server are required.

## One-time GitHub setup

1. Create a **public** GitHub repository named exactly `CalcuCoding`.
2. Put all of the files from this starter project into the repository **at its root**,
   including the hidden `.github/workflows/deploy.yml` file. Do not upload this ZIP
   as one ZIP file: extract it first. GitHub Desktop or git can preserve the directories.
3. On GitHub, open **Settings → Pages → Build and deployment → Source**, and select
   **GitHub Actions**.
4. In **Actions**, watch the workflow **Publish CalcuCoding JupyterLite**.
   If Actions are disabled, enable them. A commit to `main` triggers publication.
5. Open `https://YOUR_USERNAME.github.io/CalcuCoding/` after the deploy job succeeds.

No GitHub-hosted JupyterLite site has been deployed automatically by providing this ZIP.
The build workflow is based on stable JupyterLite 0.8.x and must run on GitHub once.

## PowerPoint/iSpring links

Link students **directly to individual notebooks** in the simple Notebook UI:

`https://YOUR_USERNAME.github.io/CalcuCoding/notebooks/index.html?path=01_Turtle_Test.ipynb`

Additional pilot URLs:

- `?path=00_Start_Here.ipynb`
- `?path=02_NumPy_and_Matplotlib.ipynb`
- `?path=03_Turtle_and_NumPy.ipynb`
- `?path=04_Separate_Turtle_Cells.ipynb`

Replace YOUR_USERNAME with your actual GitHub username. These are example addresses,
not live websites yet. The repository name is case-sensitive in the URL.

Run `python tools/list_links.py YOUR_USERNAME` locally to create a CSV for
all notebooks under `files/` (including chapter subfolders).

## How to add your own notebooks

Upload any `.ipynb` files into `files/` (or chapter subfolders under it), commit
and push. The workflow republishes the site. For example, a notebook at
`files/Level4/CircularMotion.ipynb` opens with:

`https://YOUR_USERNAME.github.io/CalcuCoding/notebooks/index.html?path=Level4/CircularMotion.ipynb`

Avoid renaming files once you've linked them in PowerPoint.

## What gets installed, and when?

- `requirements.txt` installs the JupyterLite **site builder and browser widget
  frontends** on the GitHub Actions builder. It does **not** preinstall `ipycc`
  into every notebook kernel.
- `01_Turtle_Test.ipynb` includes `%pip install -q ipycc==0.1.1` as a **manual,
  visible setup cell**. Only notebooks which use `ipycc` need it for this test.
- This uses the **Pyodide** kernel, with `%pip` routed through `piplite`.
- Once we confirm the pilot, we can improve convenience by packaging the required
  runtime libraries at build time, without running an install command in every
  student's notebook. This is not configured in the starter.

## Troubleshooting

- If a notebook opens but the Python kernel is missing, inspect the GitHub
  Actions build log, especially the `requirements.txt` install step.
- If `%pip install ipycc` fails, note whether it's a network, dependency,
  Python-version, or wheel error and keep the full output. `ipycc==0.1.1`
  requires Python 3.12+, supported by the current Pyodide kernel.
- If Turtle code executes with no image, inspect the browser's widget output
  errors; the site intentionally installs `ipycanvas` and `ipywidgets` frontend
  extensions at build time.
- If students have previously edited a notebook, their local browser copy may
  hide subsequent teacher updates. Use JupyterLite's file reset/remove facility
  or a fresh browser profile to compare the published copy.
- Notebook Python packages and helpers should be tested before putting dozens
  of PowerPoint links into production.

## Authoring notes

Keep your originals under version control. All students' edits stay in their
own browsers unless they explicitly download and send them elsewhere. There is
no grading or server-side code execution.
