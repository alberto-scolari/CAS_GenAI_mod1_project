# Slide Analyzer

You got a slide deck from the course and are in front of a slide, staring at a sentence you don't fully grasp... or of which you want to know more!

This app is for you! It analyzes a slide, identifies relevant topics and gives you more information. You can then save it to your computer.

---

This app consists of a Jupyter notebook with a Gradio web app that analyzes presentation slides. It uses OpenAI models in the background to extract and add information.

## How it works

1. Upload a slide deck (PDF) or a single slide image and pick a slide.
2. **Analyze slide**: the model finds the title and the content areas, their topics and how they relate; the areas are drawn as boxes on the slide.
3. Click on a box to get more information about it (an explanation, additional resources, or the answer to your own question).
4. **Download** all the results as a single HTML report (print it to PDF from the browser if needed).

Every model call returns structured JSON (OpenAI Structured Outputs). The models used for each step are set in `STEP_CONFIG` in the notebook.

## Requirements
The software dependencies are listed in the `pyproject.toml` or installed directly within the notebook, so the only information you must provide is an **OpenAI API key**. If you run the notebook in your computer, you can set it as an environment variable before starting Jupyter (otherwise the notebook asks for it):

  ```bash
  export OPENAI_API_KEY="sk-..."
  ```

If you instead import the notebook to a Google Colab environment, it reads it directly from your Colab secrets.

## How to run
You can directly run the notebook in your jupyter environment, in which case it will install the dependencies within the notebook itself via a usual `pip install ...` command. If you choose this option, you need no setup but you must reinstall the dependencies every time you run the notebook.

If, instead, you want to store the dependencies to a persistent environment and speed up subsequent runs, the project has a standard `pyproject.toml` file listing the needed dependencies. The easiest way to run the notebook (and install the dependencies in one go) is via [pixi](https://pixi.prefix.dev/latest/#installation):

```bash
pixi run lab
```

Alternatively, you can use a tool like [uv](https://docs.astral.sh/uv/getting-started/installation/)

```bash
uv sync
uv run jupyter lab slide_analyzer.ipynb
```

## Use the app

If you run jupyter locally, jupyter should show you an URL (e.g., `http://127.0.0.1:8888/lab?token=06aa9793e7e671ce924eec78d91aaa02483eb16efe40c89b`) and automatically open a browser instance. Within the notebook, just run all cells (*Run → Run All Cells*). The app appears below the last cell.
