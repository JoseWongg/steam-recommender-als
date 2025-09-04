# Steam Game Recommender with Spark MLlib (ALS)

A collaborative filtering recommender system for Steam games using **Apache Spark MLlib (ALS)**.  
The project demonstrates how to build an implicit-feedback recommender at scale on Databricks.

It focuses on:
- Preparing implicit feedback from purchase/play events.  
- Generating integer IDs for users and games (required by ALS).  
- Training and tuning an ALS model.  
- Evaluating performance and producing top-N recommendations per user.  

## Repository Structure
```
steam-recommender-als/
├── notebooks/
│   ├── Steam_Recommender.html   # Databricks HTML export (open in browser)
│   ├── Steam_Recommender.dbc    # Databricks archive (import into workspace)
│   └── Steam_Recommender.ipynb  # Jupyter notebook
├── data/
│   ├── games.csv                # Game catalog / ID mapping (140 KB)
│   └── steam-200k.csv           # User–game interaction dataset (7.68 MB)
├── LICENSE
└── README.md
```

## Notebooks
Provided in three formats for convenience:
- **HTML (`.html`)** — open directly in a browser to review results.  
- **Databricks Archive (`.dbc`)** — import into a Databricks workspace.  
- **Jupyter Notebook (`.ipynb`)** — run locally (with Spark installed) or in Databricks.  

## What’s Inside
- Data preparation:
  - Transform “purchase” / “play” events into implicit feedback.  
  - Create stable integer IDs for users and games.  
- Model training:
  - Alternating Least Squares (ALS) for implicit feedback.  
  - Train/test split and hyperparameter tuning.  
- Evaluation and outputs:
  - Performance metrics and sanity checks.  
  - Top-N recommendations per user with example lookups.  

## Dataset
This project uses two datasets:
- `games.csv` — a compact game catalog for ID mapping and display names (included).  
- `steam-200k.csv` — user–game interactions (≈7.68 MB, included).  

The `steam-200k.csv` dataset is derived from Steam usage data.  

### Using the data in Databricks
1. In Databricks, go to **Data → Create → Add Data → Upload File**.  
2. Upload both datasets (`games.csv` and `steam-200k.csv`).  
3. Target paths (examples):  
   - `/FileStore/games.csv`  
   - `/FileStore/steam-200k.csv`  
4. Load in Spark:  
   ```python
   games = spark.read.option("header", "true").csv("/FileStore/games.csv")
   events = spark.read.option("header", "true").csv("/FileStore/steam-200k.csv")
   ```

## How to Use
### Option 1: Quick View  
Open `notebooks/Steam_Recommender.html` in your browser to see the full notebook with code and outputs.

### Option 2: Run in Databricks  
1. Log in to your Databricks workspace.  
2. Import `notebooks/Steam_Recommender.dbc`.  
3. Attach to a cluster and run all cells.  

### Option 3: Run Locally  
1. Ensure you have Apache Spark installed.  
2. Open `notebooks/Steam_Recommender.ipynb` in Jupyter.  
3. Adjust dataset paths as required.  

### Clone this repository
```bash
git clone https://github.com/JoseWongg/steam-recommender-als.git
cd steam-recommender-als
```

## Authorship & Contact
Developed by **Jose Wong**  
j.wong@mail.com  
https://www.linkedin.com/in/jose-wongg  
https://github.com/JoseWongg  

## License
MIT — see the [LICENSE](LICENSE) file for details.
