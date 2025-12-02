Ranking Potentially Hazardous Asteroids
A machine-learning model that assigns a continuous hazard score (0–1) to near-Earth Asteroids using orbital and physical features. The output is a ranked list of objects based on risk. 

Project Structure:
- 'final_code.ipynb' - main notebook containing all data processing, model training and scoring code
- 'git.ignore' - standard ignore file (dataset excluded)

Overview:
The goal of this project is to create a more informative and flexible way to evaluate asteroid hazards.
Traditional PHA classification is binary (hazardous or not), which can hide important differences between asteroids.

This model provides:
- a gradual, continuous measure of risk
- a ranking system to help identify which objects deserve attention first
This makes analysis clearer, more interpretable, and more useful for monitoring potentially risky asteroids. 

The model uses features such as MOID, H-magnitude, eccentricity, inclination, and relative velocity to predict whether an asteroid is potentially hazardous.  
Two small hinge-style adjustments slightly increase the score for:
- very small MOID (close approach),
- low H values (brighter/larger objects)

The final output includes:
●	hazard_prob: continuous risk score from 0-1
●	pred_hazard: Top-K classification (1/0) -> for precision check
●	df_ranked: full dataset sorted by hazard_prob with 1-based danger_rank.

Quick views: printed Top 10, Middle 10, Bottom 10 to check extremes and the center of the ranking

How to Run across datasets:
1.	Prepare dataset.csv with moid, H, a, e, i, pha. (make sure the names of these columns are kept in this format)
2.	Run the script using jupyter notebook (run top down) (Python 3; NumPy, pandas; scikit-learn libraries installed).
3.	View the resulting dataframe with the hazard scores.

Key adjusting factors: (when running with own dataset)
○	K_FACTOR: precision↔recall dial (controls how many are flagged),
○	l2: small regularization (curbs saturation vs recall),
○	hinge points: domain-informed thresholds ('h_moid', 'h_H')

Results: The model successfully produces calibrated hazard probabilities and ranks asteroids by risk, allowing easier prioritization and analysis of potentially hazardous asteroids.

Notes:
The dataset must be added manually if you want to reproduce the model.
Hazard scores are model-based and not equivalent to official NASA risk assessments.



