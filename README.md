# Milestone2
NBA Game Analysis using Kalshi Prediction Market & NBA API Data

**Overview**

This project explores NBA game data and prediction-market information to investigate patterns, relationships, and potential insights related to NBA game outcomes.

The project combines data from Kalshi prediction markets and the NBA API, using data analysis, visualization, and machine learning techniques to examine the relationship between market expectations and basketball performance.

**Project Objectives**

Collect and explore NBA game and prediction-market data.
Clean, transform, and prepare data for analysis.
Apply exploratory data analysis and data visualization to identify patterns.
Use unsupervised learning techniques to explore groupings and structure in the data.
Investigate relationships between prediction-market information and NBA game outcomes.

**Getting Started**

1. Clone the Repository
Open a terminal and run:
git clone https://github.com/brad-hof/Milestone2.git
cd Milestone2

2. Create a Virtual Environment
Create an isolated Python environment:
python -m venv .venv

3. Activate the environment.
Windows:
.venv\Scripts\activate

macOS/Linux:
source .venv/bin/activate

4. Install Dependencies
Upgrade pip and install the required packages:

python -m pip install --upgrade pip
pip install -r requirements.txt

**Directory Description**

Notebooks/ — Contains the Jupyter notebooks used for data preparation, Kalshi prediction-market data collection, NBA statistics collection, supervised learning, and unsupervised learning.
data/processed/ — Contains the processed CSV datasets used for analysis, including NBA box scores, Kalshi market data, game-period data, and rolling-average features.
visualizations/ — Contains figures generated during data preparation, model evaluation, and clustering analysis.
requirements.txt — Lists the Python dependencies required to run the project.
.gitignore — Specifies files and directories Git should ignore.

