# MLOPs-Assignment
# Data Processing, Training, and Inference Pipeline Automation 🚀

This project automates the data preprocessing, model training, and inference pipelines using Apache Airflow. The following steps outline the creation and configuration of these pipelines.

## Table of Contents 📚

1. [Project Structure](#project-structure)
2. [Setup Instructions](#setup-instructions)
3. [Data Preprocessing Pipeline](#data-preprocessing-pipeline)
4. [Model Training Pipeline](#model-training-pipeline)
5. [Inference Pipeline](#inference-pipeline)
6. [Running the Pipelines](#running-the-pipelines)

## Project Structure 🗂️

The project is organized as follows:

```
Assignment/
├── 01_data_pipeline/
│   ├── notebooks/
│   │   └── data_cleaning_template.ipynb
│   ├── scripts/
│   │   ├── city_tier_mapping.py
│   │   ├── constants.py
│   │   ├── data_validation_checks.py
│   │   ├── dummy.ipynb
│   │   ├── interaction_mapping.csv
│   │   ├── lead_scoring_data_pipeline.py
│   │   ├── leadscoring_test.csv
│   │   ├── schema.py
│   │   ├── significant_categorical_level.py
│   │   ├── test_with_pytest.py
│   │   ├── unit_test_cases.db
│   │   ├── utils.py
│   │   └── utils_output.db
├── 02_training_pipeline/
│   ├── notebooks/
│   │   └── lead_scoring_experimentation.ipynb
│   ├── scripts/
│   │   ├── constants.py
│   │   ├── lead_scoring_training_pipeline.py
│   │   └── utils.py
├── 03_inference_pipeline/
│   ├── data/
│   │   └── leadscoring_inference.csv
│   ├── scripts/
│   │   ├── constants.py
│   │   ├── lead_scoring_inference_pipeline.py
│   │   └── utils.py
```

## Setup Instructions 🛠️

### Prerequisites

Ensure you have the following installed:
- Python 3.6+
- Apache Airflow 2.0+
- SQLite

### Installation

1. Clone the repository:
   ```sh
   git clone <repository_url>
   cd Assignment
   ```

2. Create a virtual environment and activate it:
   ```sh
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install the required Python packages:
   ```sh
   pip install -r requirements.txt
   ```

4. Initialize Airflow:
   ```sh
   airflow db init
   ```

5. Create an Airflow user:
   ```sh
   airflow users create --username upgrad --firstname upgrad --lastname upgrad --role Admin --email spiderman@superhero.org --password admin
   ```

6. Start the Airflow web server:
   ```sh
   airflow webserver --port 6007
   ```

7. Start the Airflow scheduler in a new terminal:
   ```sh
   airflow scheduler
   ```

## Data Preprocessing Pipeline 🧹

1. Navigate to the `scripts` directory:
   ```sh
   cd Assignment/01_data_pipeline/scripts
   ```

2. Implement data cleaning functions in `utils.py` using the provided notebook `data_cleaning_template.ipynb`.

3. Update the `significant_categorical_level.py` file with significant levels for categorical variables.

4. Ensure all functions read from and write to `utils_output.db`.

5. Test the functions in a dummy notebook (`dummy.ipynb`).

6. Write unit tests in `test_with_pytest.py` and verify the outputs against `unit_test_cases.db`.

7. Define the DAG for the data pipeline in `lead_scoring_data_pipeline.py`.

8. Place the scripts and required files in `~/airflow/dags/Lead_scoring_data_pipeline`.

### File Changes and Execution Order 📄

1. **utils.py**:
   - Split the data cleaning tasks into functions.
   - Functions order: `build_dbs`, `load_data_into_db`, `map_city_tier`, `map_categorical_vars`, `interactions_mapping`.
   - Read input data and write output to `utils_output.db`.

2. **significant_categorical_level.py**:
   - Populate the lists with significant categorical levels.

3. **constants.py**:
   - Store all constant values.

4. **dummy.ipynb**:
   - Test all functions to create the `utils_output.db` database.

5. **test_with_pytest.py**:
   - Write unit test cases for the functions to check their output against expected results.

## Model Training Pipeline 🏋️‍♂️

1. Navigate to the `scripts` directory:
   ```sh
   cd Assignment/02_training_pipeline/scripts
   ```

2. Implement the model training functions (`encode_features` and `get_trained_model`) in `utils.py`.

3. Test the functions in a dummy notebook.

4. Define the DAG for the training pipeline in `lead_scoring_training_pipeline.py`.

5. Place the scripts and required files in `~/airflow/dags/Lead_scoring_training_pipeline`.

### File Changes and Execution Order 📄

1. **utils.py**:
   - Functions: `encode_features`, `get_trained_model`.
   - Read input data from `lead_scoring_data_cleaning.db`.

2. **constants.py**:
   - Store all constant values.
   - Set the MLflow experiment name to `Lead_scoring_mlflow_production`.

3. **dummy.ipynb**:
   - Test all functions.

## Inference Pipeline 🔮

1. Navigate to the `scripts` directory:
   ```sh
   cd Assignment/03_inference_pipeline/scripts
   ```

2. Implement the inference functions (`encode_data`, `input_features_check`, `load_model`, `prediction_col_check`) in `utils.py`.

3. Test the functions in a dummy notebook.

4. Define the DAG for the inference pipeline in `lead_scoring_inference_pipeline.py`.

5. Place the scripts and required files in `~/airflow/dags/Lead_scoring_inference_pipeline`.

### File Changes and Execution Order 📄

1. **utils.py**:
   - Functions: `encode_data`, `input_features_check`, `load_model`, `prediction_col_check`.
   - Read input data from `lead_scoring_data_cleaning.db`.

2. **constants.py**:
   - Store all constant values.

3. **dummy.ipynb**:
   - Test all functions.

## Running the Pipelines ▶️

1. **Data Pipeline**:
   - Manually trigger the data pipeline via the Airflow UI.

2. **Training Pipeline**:
   - Ensure the data pipeline has completed.
   - Manually trigger the training pipeline via the Airflow UI.

3. **Inference Pipeline**:
   - Ensure the data pipeline has processed the inference data.
   - Manually trigger the inference pipeline via the Airflow UI.

4. **Validate**:
   - Verify the outputs at each stage to ensure correctness.

### Screenshots 📸

Include screenshots of the Airflow UI showing the successful execution of each pipeline.

### Final Note 🏁

Once all pipelines are running successfully, you have completed the automation workflow. Congratulations on completing the assignment! 🎉

---

This README provides an overview and setup instructions to run the automated pipelines for data preprocessing, model training, and inference using Apache Airflow. Ensure all steps are followed meticulously for successful execution.
