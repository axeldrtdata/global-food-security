# Does the world produce enough food to feed everyone?

A public-health study for the FAO, built in Python on four FAO datasets: how many people are undernourished, how many people the world's food could feed, where that food goes, and what a second look at data coverage changes.

**Read the case study:** https://axeldrtdata.github.io/works/global-food-security/

## Context

The FAO wanted a first picture of world food security from its own data: the number of undernourished people, the theoretical number of people the food available could feed, how domestic supply is used, the countries most affected by hunger, and where food aid goes. Behind these questions sits one: is hunger a problem of production, or of distribution?

## Key results

| Question | Result (2017 unless stated) |
| -------- | --------------------------- |
| Undernourished people | 535.7 million, 7.1% of the world population (a floor, see below) |
| People the calories available could feed | about 8.8 billion, 117% of the world population |
| People plant products alone could feed | about 7.3 billion, 96% of the world population |
| Domestic supply eaten directly by people | 49.5% (processing 22.4%, animal feed 13.2%, losses 4.6%) |
| Cereals used for animal feed | 36% (43% eaten directly by people) |
| Countries below the 2,400 kcal daily need | 29 out of 174 |
| Thailand's cassava | 25.2 million tonnes exported, 83% of production, while about 9% of Thais were undernourished |

### A second look at the data

When I came back to this project for my portfolio, I checked what the data covers before trusting what it says:

- **Units.** The food balance sheets are in thousands of tonnes: multiplied by 1,000, they are in tonnes, not kilograms. The first version understated losses and Thailand's cassava exports by a factor of 1,000.
- **Joins.** Three countries had different names from one file to another (United Kingdom, Czechia, Eswatini) and were silently dropped. With the names harmonised, the world's food could feed 8.8 billion people instead of 8.7.
- **Missing estimates.** 116 countries, home to more than 3.3 billion people, have no undernourishment estimate, including the Democratic Republic of the Congo, Yemen, Somalia, South Sudan and Syria. The 535.7 million is a floor.
- **Food aid.** Six of the ten largest aid recipients have no undernourishment estimate. Among the 48 recipients that do, aid follows the number of undernourished people (Spearman ρ = 0.54, p < 0.001) but not their share (ρ = 0.25, not significant). The −82% drop in recorded aid between 2013 and 2016 comes mostly from countries that stop reporting (72 in 2013, 26 in 2016); on the same 25 countries, aid fell by about half.

## Repository structure

```
global-food-security/
├── data/
│   ├── aide_alimentaire.csv      # food aid received, tonnes, 2013–2016
│   ├── dispo_alimentaire.csv     # food balance sheets, 2017
│   ├── population.csv            # population, thousands, 2013–2018
│   └── sous_nutrition.csv        # undernourished people, millions, three-year averages
├── notebooks/
│   └── 01_food_security_analysis.ipynb
├── requirements.txt
└── README.md
```

## How to run it

1. Clone the repository and open the folder in VS Code.
2. Create a virtual environment and install the dependencies:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```
3. Open `notebooks/01_food_security_analysis.ipynb`, select the `.venv` kernel and run all cells. The notebook reads the data with relative paths (`../data/…`).

## Limits

- Undernourishment estimates are missing for 44% of the world population, so every total and ranking based on them is incomplete.
- Food availability is not consumption: it includes what is wasted in shops and at home.
- The theoretical number of people fed uses a single 2,400 kcal average and leaves aside transport, storage, prices and politics.

## Stack

Python · Pandas · Matplotlib · SciPy · VS Code

## Data sources

Four extracts from the FAO (Food and Agriculture Organization of the United Nations) statistics, provided by OpenClassrooms for the Data Analyst path. The daily need of 2,400 kcal is the midpoint of the 2,300 to 2,500 kcal range given in an FAO publication: https://www.fao.org/4/x5643f/x5643f00.htm

## Note on the translation

This project was first written in French in December 2025 as part of my OpenClassrooms Data Analyst training. The notebook was translated into English, corrected where marked, and re-run for my portfolio in October 2026. The FAO files are in French, so country, product and column names stay in French.

---

Axel Derobert · Data Analyst · Lyon · [Portfolio](https://axeldrtdata.github.io) · [LinkedIn](https://www.linkedin.com/in/axel-derobert-5717463b1/)
