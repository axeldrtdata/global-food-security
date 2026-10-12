# Does the world produce enough food to feed everyone?

A public-health study for the FAO, built in Python on four FAO datasets: how many people are undernourished, how many people the world's food could feed, and where that food goes.

**Read the case study:** https://axeldrtdata.github.io/works/global-food-security/

## Context

The FAO wanted a first picture of world food security from its own data: the number of undernourished people, the theoretical number of people the food available could feed, how domestic supply is used, the countries most affected by hunger, and where food aid goes. Behind these questions sits one: is hunger a problem of production, or of distribution?

## Key results

| Question | Result (2017 unless stated) |
| -------- | --------------------------- |
| Undernourished people | 535.7 million, 7.1% of the world population |
| People the calories available could feed | about 8.8 billion, 117% of the world population |
| People plant products alone could feed | about 7.3 billion, 96% of the world population |
| Domestic supply eaten directly by people | 49.5% (processing 22.4%, animal feed 13.2%, losses 4.6%) |
| Cereals used for animal feed | 36% (43% eaten directly by people) |
| Countries below the 2,400 kcal daily need | 29 out of 174 |
| Thailand's cassava | 25.2 million tonnes exported, 83% of production, while about 9% of Thais were undernourished |

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

- The undernourished total is a minimum: countries without an estimate count as zero, and the ranking of rates only covers the countries that have one.
- Food availability is not consumption: it includes what is wasted in shops and at home.
- The theoretical number of people fed uses a single 2,400 kcal average and leaves aside transport, storage, prices and politics.

## Stack

Python · Pandas · Matplotlib · VS Code

## Data sources

Four extracts from the FAO (Food and Agriculture Organization of the United Nations) statistics, provided by OpenClassrooms for the Data Analyst path. The daily need of 2,400 kcal is the midpoint of the 2,300 to 2,500 kcal range given in an FAO publication: https://www.fao.org/4/x5643f/x5643f00.htm

## Note on the translation

This project was first written in French in December 2025 as part of my OpenClassrooms Data Analyst training. The notebook was translated into English and re-run for my portfolio in October 2026. The FAO files are in French, so country, product and column names stay in French.

---

Axel Derobert · Data Analyst · Lyon · [Portfolio](https://axeldrtdata.github.io) · [LinkedIn](https://www.linkedin.com/in/axel-derobert-5717463b1/)
