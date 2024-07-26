# SHAPI: A SHAP SaaS API

A cloud-based SaaS package providing SHAP (SHapley Additive exPlanations) functionalities via REST APIs. This project implements endpoints to create explainers for various models and generate plots for SHAP values.

## Features

- Create Tree, Linear, and Kernel Explainers
- Compute SHAP values using the created explainers
- Generate bar plots, summary plots, and dependence plots of SHAP values

## Directory Structure

```
shap_saas/
├── app.py
├── requirements.txt
├── config/
│   └── __init__.py
├── models/
│   └── __init__.py
├── explainers/
│   ├── __init__.py
│   ├── tree_explainer.py
│   ├── linear_explainer.py
│   └── kernel_explainer.py
├── plots/
│   ├── __init__.py
│   ├── bar_plot.py
│   ├── summary_plot.py
│   └── dependence_plot.py
└── tests/
    ├── __init__.py
    ├── test_explainers.py
    └── test_plots.py
```

## Installation

1. Clone the repository:
```
bash
git clone https://github.com/yourusername/shap_saas.git
cd shap_saas
```

2. Create a virtual environment and activate it:
```
bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

3. Install the required packages:
```
bash
pip install -r requirements.txt
```

## Usage

1. Run the Flask application:
```
bash
python app.py
```

2. The API will be available at `http://127.0.0.1:5000`.

## Endpoints

### Create Tree Explainer
- **URL:** `/explainers/tree`
- **Method:** `POST`
- **Description:** Uses Tree SHAP algorithms to explain the output of ensemble tree models.
- **Request Body:**
```
{
   "model": "YourModelObject",
   "data": [ ... ]
}
```
- **Response:**
```
{
   "explainer_id": "1"
}
```

### Create Linear Explainer
- **URL:** `/explainers/linear`
- **Method:** `POST`
- **Description:** Computes SHAP values for a linear model.
- **Request Body:**
```
{
   "model": "YourModelObject",
   "masker": { ... }
}
```
- **Response:**
```
{
   "explainer_id": "1"
}
```

### Create Kernel Explainer
- **URL:** `/explainers/kernel`
- **Method:** `POST`
- **Description:** Computes SHAP values using the Kernel SHAP method.
- **Request Body:**
```
{
   "model": "YourModelObject",
   "data": [ ... ]
}
```
- **Response:**
```
{
   "explainer_id": "1"
}
```

### Compute SHAP Values
- **URL:** `/explainers/{explainer_id}/shap_values`
- **Method:** `POST`
- **Description:** Computes SHAP values for the given data using the specified explainer.
- **Request Body:**
```
{
   "data": [ ... ]
}
```
- **Response:**
```
{
   "shap_values": [ ... ]
}
```

### Create Bar Plot
- **URL:** `/plots/bar`
- **Method:** `POST`
- **Description:** Create a bar plot of a set of SHAP values.
- **Request Body:**
```
{
   "shap_values": [ ... ],
   "max_display": 10
}
```
- **Response:** Returns an image of the bar plot.

### Create Summary Plot
- **URL:** `/plots/summary`
- **Method:** `POST`
- **Description:** Create a summary plot of a set of SHAP values.
- **Request Body:**
```
{
   "shap_values": [ ... ],
   "plot_type": "dot"
}
```
- **Response:** Returns an image of the summary plot.

### Create Dependence Plot
- **URL:** `/plots/dependence`
- **Method:** `POST`
- **Description:** Create a dependence plot for a specific feature.
- **Request Body:**
```
{
   "shap_values": [ ... ],
   "feature": "feature_name"
}
```
- **Response:** Returns an image of the dependence plot.

## Testing

1. Run the tests:
```
bash
pytest
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [SHAP Documentation](https://shap.readthedocs.io/en/latest/api.html) for providing the basis for this implementation.
```
