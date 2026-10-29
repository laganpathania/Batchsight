# BatchSight: bioprocess digital twin and multivariate analysis

Understand your fed-batch data and catch drift early. BatchSight reads each batch against its own history and against process physics, using multivariate statistics and a mechanistic model on the same dataset.

**Try it live:** https://laganpathania.com/twin/

## What is inside

| Module | Question it answers | Method |
|---|---|---|
| Batch Evolution | How do runs compare over time? | Overlaid trajectories per variable, as concentration or absolute mass |
| Multivariate (PCA) | Which batches are unusual? | Principal component scores with a 95% Hotelling T² ellipse |
| Predictive (PLS) | What predicts yield or quality early? | PLS regression with cross-validated tuning and variable importance (VIP) tested by permutation |
| Kinetic (ODE) | What do growth and consumption rates look like? | Mechanistic ODE fit with feed and sampling events built into the mass balance |
| Prescriptive Optimizer | Where could controllable levers move the process? | Search within the PLS model for a target point, with a warning when it extrapolates |

## How to use it

1. **Demo.** Explore the full workflow on simulated fed-batch data. Change the reactor assumptions in the side panel and watch every module respond.
2. **Try with your data.** Upload a CSV with one row per time point: a batch identifier, a time column, your process variables and one target such as titer. Map the columns in the side panel.
3. **Interpret and decide.** Use the results to frame questions for your process team.

## Run it on your computer

Use Python 3.11 to 3.13.

```
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

## Limits

- An exploratory tool, not validated for GxP decisions.
- The demo uses simulated data. Conclusions about a real process need real data.
- Multivariate models need a dense batch history. With about 15 batches, cross-validation variance is high. Production validation calls for more than 30.
- The optimizer searches a correlational model. It points to hypotheses to test, not to proven causes.

## Privacy

The live version runs in your browser. Your CSV is never uploaded to a server and is gone when you close the tab. Please still anonymise batch identifiers before uploading.

## Author

Lagan Pathania, lab automation architect. [laganpathania.com](https://laganpathania.com)
