# Day 2 Progress: From Script to Deployed Web App

## What I accomplished:
- Built a Python script that generates custom cold emails using the DeepSeek API.
- Created an interactive UI inside Google Colab using built-in forms.
- Wrote a prototype script that scrapes website content and asks the AI to analyze the audience.
- Transformed the Colab prototype into a real web app using Streamlit.
- Deployed the app to the public internet via Streamlit Cloud.

## Live Demo:
https://ai-email-generator-420yolomcswaggerpants.streamlit.app

## GitHub Repository:
https://github.com/420yolomcswaggerpants/ai-email-generator

---

## Skills learned today:
- API chaining
- Prompt engineering (System prompts vs User prompts)
- Passing variables into prompts (f-strings)
- Basic web scraping with the `requests` library
- Using `temperature` and `max_tokens` to control AI output
- Building a web app with Streamlit
- Version control with Git and GitHub
- Deploying to Streamlit Cloud
- Protecting API keys with .gitignore and secrets.toml

---

## Errors I hit and fixed:
- Git not recognized (fixed by installing Git)
- Author identity unknown (fixed by configuring git user)
- GitHub push protection blocked my API key (fixed with .gitignore)
- Streamlit ModuleNotFoundError (fixed with requirements.txt)
- Frozen terminal during git push (fixed with direct URL push)

---

## Next steps:
- Build a more specialized AI tool (not just generic email generation)
- Add web scraping to pull real data
- Implement memory/state management
- Fine-tune a model on custom data
- Monetize or showcase for job applications
