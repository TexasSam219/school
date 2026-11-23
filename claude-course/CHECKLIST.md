# My Claude Learning Checklist

Tick a box by changing `[ ]` to `[x]` (edit this file on GitHub with the ✏️ pencil icon).

**API credit:** $100 promo credit, **expires Dec 24, 2026** — do the hands-on lessons first.

---

## My setup cell (API Fundamentals, Real World Prompting, Tool Use)

Paste this in place of the lesson's setup cell (the one with `load_dotenv`), then run it first:

```python
%pip install anthropic
from google.colab import userdata
from anthropic import Anthropic

client = Anthropic(api_key=userdata.get('ANTHROPIC_API_KEY'))
```

## Every lesson: the 2 changes to make in Colab

1. **Load the key** — replace any `load_dotenv` / `os.getenv` cell (or `API_KEY = "your_api_key_here"`) with:
   ```python
   from google.colab import userdata
   my_api_key = userdata.get('ANTHROPIC_API_KEY')
   ```
   (In the Prompt Engineering tutorial the variable is called `API_KEY` instead of `my_api_key`.)
2. **Update the model** — change any old model name (like `claude-3-haiku-20240307`) to:
   ```python
   "claude-haiku-5-5"
   ```

Also: click **Run anyway** on the warning, then **Copy to Drive** to save your own copy, and turn on
**Notebook access** for your secret in the 🔑 panel for each new notebook.

## Reading errors

| Error | What it means |
|---|---|
| `SyntaxError` | Typo or layout problem — check the line number and the `^` arrow |
| `NotFoundError` | The thing you asked for doesn't exist (usually an old model name) |
| `BadRequestError` | The request is set up wrong (e.g. a label like `"content"` was changed) |
| `ModuleNotFoundError` | Package not installed in this notebook — run `%pip install anthropic` (each notebook starts empty) |
| `NameError: ... is not defined` | A setup cell wasn't run yet (Colab forgets after you close the tab) — run the cells from the top |
| `AttributeError: 'ThinkingBlock' ... no attribute 'text'` | Newer models put their thinking first — use `response.content[-1].text` instead of `[0]` |
| `TimeoutException: Requesting secret ... timed out` | Turn on Notebook access in the 🔑 panel and click Grant access when asked |
| `AuthenticationError` | API key missing or wrong — check the 🔑 secret name and Notebook access |

---

## Course 1 — API Fundamentals

- [x] 1. Getting Started — [open](https://githubtocolab.com/anthropics/courses/blob/master/anthropic_api_fundamentals/01_getting_started.ipynb) — *done Nov 22, 2026, plus exercise (chicken joke!)*
- [ ] 2. Messages Format — [open](https://githubtocolab.com/anthropics/courses/blob/master/anthropic_api_fundamentals/02_messages_format.ipynb)
- [ ] 3. Models — [open](https://githubtocolab.com/anthropics/courses/blob/master/anthropic_api_fundamentals/03_models.ipynb)
- [ ] 4. Parameters — [open](https://githubtocolab.com/anthropics/courses/blob/master/anthropic_api_fundamentals/04_parameters.ipynb)
- [ ] 5. Streaming — [open](https://githubtocolab.com/anthropics/courses/blob/master/anthropic_api_fundamentals/05_Streaming.ipynb)
- [ ] 6. Vision (images) — [open](https://githubtocolab.com/anthropics/courses/blob/master/anthropic_api_fundamentals/06_vision.ipynb)

## Course 2 — Prompt Engineering Interactive Tutorial

- [ ] 0. Tutorial How-To — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/00_Tutorial_How-To.ipynb)
- [ ] 1. Basic Prompt Structure — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/01_Basic_Prompt_Structure.ipynb)
- [ ] 2. Being Clear and Direct — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/02_Being_Clear_and_Direct.ipynb)
- [ ] 3. Assigning Roles — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/03_Assigning_Roles_Role_Prompting.ipynb)
- [ ] 4. Separating Data and Instructions — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/04_Separating_Data_and_Instructions.ipynb)
- [ ] 5. Formatting Output — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/05_Formatting_Output_and_Speaking_for_Claude.ipynb)
- [ ] 6. Thinking Step by Step — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/06_Precognition_Thinking_Step_by_Step.ipynb)
- [ ] 7. Using Examples — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/07_Using_Examples_Few-Shot_Prompting.ipynb)
- [ ] 8. Avoiding Hallucinations — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/08_Avoiding_Hallucinations.ipynb)
- [ ] 9. Complex Prompts from Scratch — [open](https://githubtocolab.com/anthropics/courses/blob/master/prompt_engineering_interactive_tutorial/Anthropic%201P/09_Complex_Prompts_from_Scratch.ipynb)

## Course 3 — Real World Prompting

- [ ] 1. Prompting Recap
- [ ] 2. Medical Prompt
- [ ] 3. Prompt Engineering
- [ ] 4. Call Summarizer
- [ ] 5. Customer Support AI

Folder: https://github.com/anthropics/courses/tree/master/real_world_prompting

## Course 4 — Tool Use

- [ ] 1. Tool Use Overview
- [ ] 2. Your First Simple Tool
- [ ] 3. Structured Outputs
- [ ] 4. Complete Workflow
- [ ] 5. Tool Choice
- [ ] 6. Chatbot with Multiple Tools

Folder: https://github.com/anthropics/courses/tree/master/tool_use

## Course 5 — Prompt Evaluations (optional, more advanced)

Folder: https://github.com/anthropics/courses/tree/master/prompt_evaluations

---

## Extras to try before the credit expires

- [ ] Workbench in the Console — compare Haiku 5.5, Sonnet 5.5 and Opus 5.5 on the same prompt
- [ ] Install Claude Code on my PC (then `/plugin marketplace add anthropics/skills` works there)
- [ ] Try "Build an agent" in the Console
- [ ] Free video courses: https://anthropic.skilljar.com

## Notes

- Lesson 1: Claude doesn't remember between calls — you send the whole conversation each time.
- Lesson 1: Be specific. "ask for a joke" → Claude asked *me* a joke. "tell me a joke about a chicken" → got a joke.
