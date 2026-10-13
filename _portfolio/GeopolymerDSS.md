---
title: "Decision Support System for Sustainable Geopolymer Concrete & Critical Mineral Recovery"
collection: portfolio
excerpt: "Built a full-stack Machine Learning web app deployed on Vercel that predicts CO₂e emissions, critical mineral recovery efficiency, and carbon intensity when recycling industrial waste into geopolymer concrete.<br><br><a href='https://github.com/U-Louisville-BACS-Capstone/2026-fall-capstone-geopolymer-concrete' target='_blank' rel='noopener noreferrer' class='btn btn--info'><i class='fab fa-fw fa-github icon-pad-right' aria-hidden='true'></i>View on GitHub</a>"
---

Built a full-stack Machine Learning Decision Support System (DSS) for designing sustainable geopolymer concrete and recovering critical minerals, deployed on Vercel for hosting. The web app tests how different industrial waste materials (Red Mud and Coal Fly Ash) and extraction methods affect three main outcomes: total CO₂e emissions, the percentage of critical minerals recovered, and overall carbon intensity (kg of CO₂e released per kg of mineral recovered).

<div style="margin: 1.5em 0; padding: 1.25em 1.5em; border: 1px solid var(--global-border-color, #d0d7de); border-radius: 10px; background-color: var(--global-bg-color, #f6f8fa); display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 1em; box-shadow: 0 2px 8px rgba(0,0,0,0.06);">
  <div>
    <div style="font-size: 1.1em; margin-bottom: 0.25em;">
      <i class="fab fa-fw fa-github" aria-hidden="true"></i> U-Louisville-BACS-Capstone / 2026-fall-capstone-geopolymer-concrete
    </div>
    <div style="font-size: 0.9em; opacity: 0.85;">
      Full-Stack Capstone Repository &bull; React (Vite) &bull; FastAPI &bull; Scikit-Learn &bull; Supabase &bull; Hosted on Vercel
    </div>
  </div>
  <a href="https://github.com/U-Louisville-BACS-Capstone/2026-fall-capstone-geopolymer-concrete" target="_blank" rel="noopener noreferrer" class="btn btn--info btn--large" style="margin-bottom: 0; white-space: nowrap;">
    <i class="fab fa-fw fa-github icon-pad-right" aria-hidden="true"></i>Explore GitHub Repo &rarr;
  </a>
</div>

How the prediction system works:

The app takes 10 material and process inputs: feedstock type (Red Mud or Coal Fly Ash), process type (Acid Leaching, Alkaline Leaching, or Physical + Leaching), critical mineral group (Scandium-rich, Gallium-rich, or REE Mix), mineral concentration (mg/kg), electricity used (kWh/tonne), thermal energy used (MJ/tonne), acid and alkali reagents added (kg/tonne), water usage (L/tonne), and transport distance (km). It then runs a three-step prediction pipeline:

<ul>
  <li>ML1 (CO₂e Emission Model): Predicts 6 separate sources of carbon emissions (CO₂ from Electricity, Thermal Energy, Reagents, Water, Transport, and Residue) and adds them together to get total CO₂e (kg/tonne). Our tuned Support Vector Machine (SVM) model reached a test R² score of 0.844 (with over 0.998 R² on the main energy, reagent, water, and transport targets) and an average total error (MAE) of ±1.45 kg/tonne.</li>
  <li>ML2 (Recovery Efficiency Model): Predicts what percentage of the critical minerals will actually be recovered from the waste material based on the chosen leaching process and resource inputs.</li>
  <li>Carbon Intensity Calculation: Uses the outputs from both models to calculate how much CO₂e is produced for every kilogram of critical mineral recovered (kg CO₂e/kg), making it easy to compare which recipe is the most sustainable.</li>
</ul>

<figure>
  <img src="{{ '/images/GeopolymerDSS/correlation_heatmap.png' | relative_url }}" alt="Correlation Heatmap of Continuous Variables">
  <figcaption>Correlation heatmap across the 600-record dataset showing how process inputs (electricity, thermal energy, acid/alkali reagents, water, and transport) relate to each CO₂ emission source, total CO₂e, and recovery efficiency.</figcaption>
</figure>

Machine learning pipeline and model testing:

To prepare the 600-record dataset for training, we built a preprocessing pipeline that one-hot encodes the 3 text categories (feedstock, process, and mineral group) and standardizes the 7 numerical inputs. We then trained and compared several models for both prediction tasks:

<ol>
  <li>Testing CO₂e Models (ML1): We tested 8 different models using 80/20 and 70/20/10 train/test/validation splits. These included Linear Regression, Random Forest, Baseline and GridSearch-Tuned Multi-Output SVM, AdaBoost, Baseline and Optuna-Tuned XGBoost (with L1/L2 regularization), and a hybrid Gradient Boosted Decision Tree tuned with Particle Swarm Optimization (GBDT-PSO).</li>
  <li>Testing Recovery Efficiency Models (ML2): We explored how recovery rates change across different waste materials and leaching methods, then compared Linear Regression, Random Forest, and Gradient Boosting using 5-fold cross-validation so the model would not overfit to the training data.</li>
  <li>Saving Models for the Web App: We saved the best-performing pipelines as .joblib files so the backend server can load them and run predictions instantly.</li>
</ol>

<figure>
  <img src="{{ '/images/GeopolymerDSS/ml1_model_comparison.png' | relative_url }}" alt="ML1 Model Comparison Train vs Test R2">
  <figcaption>Comparison of Train vs. Test R² scores across all 8 CO₂e emission models (70/20/10 split). Linear Regression and Tuned SVM performed the best on new test data, while tree-based models overfit to noise in the residue column.</figcaption>
</figure>

<figure>
  <img src="{{ '/images/GeopolymerDSS/recovery_efficiency_eda.png' | relative_url }}" alt="Recovery Efficiency Distributions">
  <figcaption>Charts showing the distribution of Critical Mineral Recovery Efficiency (%) broken down by overall count, Feedstock Type (Red Mud vs. Coal Fly Ash), Process Type, and Critical Mineral Group.</figcaption>
</figure>

<figure>
  <img src="{{ '/images/GeopolymerDSS/ml2_model_comparison.png' | relative_url }}" alt="ML2 Model Comparison Train vs Test R2">
  <figcaption>Train vs. Test R² comparison for the ML2 Recovery Efficiency models, showing why Linear Regression was chosen over Random Forest and Gradient Boosting after 5-fold cross-validation.</figcaption>
</figure>

Full-stack web application setup:

<ul>
  <li>Frontend: Built with React and Vite, giving users a clean dashboard where they can log in, enter material and process numbers, and immediately see their predicted sustainability results.</li>
  <li>Backend API: Built with FastAPI in Python, providing routes for server health checks (/api/health), CO₂e predictions (/api/predict/ml1), recovery efficiency predictions (/api/predict/ml2), and carbon intensity math (/api/calculate/carbon-intensity).</li>
  <li>Database and Authentication: Connected to Supabase to handle user logins and database storage.</li>
  <li>Cloud Hosting: Deployed on Vercel for hosting, running the React frontend alongside the Python FastAPI backend as serverless functions.</li>
</ul>

<p style="text-align: center; margin-top: 2em;">
  <a href="https://github.com/U-Louisville-BACS-Capstone/2026-fall-capstone-geopolymer-concrete" target="_blank" rel="noopener noreferrer" class="btn btn--info btn--x-large">
    <i class="fab fa-fw fa-github icon-pad-right" aria-hidden="true"></i>View Project on GitHub
  </a>
</p>
