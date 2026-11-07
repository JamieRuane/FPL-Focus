# ⚽ FPL Guide

A web app that helps Fantasy Premier League managers pick players and plan transfers.
It uses live data from the official FPL API.

**Built with:** Python, Flask, Jinja2 templates, HTML/CSS, pytest

## Features
- **Gameweek picks:** the top players in each position, ranked by form, season average and upcoming fixture difficulty
- **Player finder:** filter by position and budget, and sort by score, value (score per £m), form or points
- **Differentials:** strong players that fewer than 10% of managers own
- **Transfer helper:** enter your squad and bank balance to see the best affordable upgrades

## Run it
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate      Mac/Linux: source .venv/bin/activate
pip install -r requirements.txt
python app.py          # open http://127.0.0.1:5000
python -m pytest       # run the tests
```
If the FPL API can't be reached, the app uses the made-up data in `sample_data/`.

## How the scoring works
`score = 0.5 × form + 0.3 × points-per-game + 0.8 × (5 − avg fixture difficulty over the next 3 games)`
The code is in `analysis.py`. It's deliberately simple, and improving it is the main goal of the roadmap below.

## Project structure
```
app.py          Flask routes (the web pages)
fpl_api.py