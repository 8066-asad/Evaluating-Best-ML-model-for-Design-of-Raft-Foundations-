# Structural Reinforcement ML Predictor

A comprehensive machine learning solution for predicting reinforcement steel requirements in concrete raft foundations. This project automatically selects the best-performing model from multiple algorithms to predict reinforcement areas, bar spacing, and number of bars required for structural design.

## Project Description

This project implements an end-to-end machine learning pipeline specifically designed for structural engineering applications. It takes concrete raft foundation parameters as input and predicts detailed reinforcement requirements including:

- Reinforcement areas (mm²/m) for different strips
- Bar spacing calculations (mm)
- Number of bars required for each direction

The system automatically evaluates multiple machine learning algorithms and selects the best-performing model based on R² scores, ensuring optimal prediction accuracy for structural design applications.

## Features

- **Multi-Model Evaluation**: Tests 8 different ML algorithms including Linear Regression, Ridge, Lasso, ElasticNet, Random Forest, XGBoost, and Neural Networks
- **Automatic Model Selection**: Automatically selects the best-performing model based on cross-validation results
- **Structural Engineering Calculations**: Incorporates domain-specific calculations for bar spacing and count based on structural design principles
- **Overfitting Detection**: Built-in analysis to detect and prevent model overfitting
- **Comprehensive Visualization**: Generates detailed plots for model comparison and performance analysis
- **Professional Scaling**: Implements both StandardScaler and RobustScaler for optimal data preprocessing
- **Multi-Output Prediction**: Handles simultaneous prediction of multiple reinforcement parameters
- **Excel Integration**: Direct support for Excel file input and processing

## Installation Instructions

### Prerequisites

- Python 3.7 or higher
- pip package manager
- Google Colab environment (recommended) or local Python environment

### Dependencies

Install the required packages using pip:

```bash
pip install openpyxl scikit-learn matplotlib seaborn tensorflow xgboost pandas numpy scipy
```

### Environment Setup

1. **For Google Colab (Recommended)**:
   ```python
   !pip install openpyxl scikit-learn matplotlib seaborn tensorflow xgboost --quiet
   ```

2. **For Local Environment**:
   ```bash
   git clone <repository-url>
   cd structural-reinforcement-ml
   pip install -r requirements.txt
   ```

### Required Data Format

Your Excel file should contain the following columns:
- `Number of Columns`
- `Area Of Raft (m^2)`
- `Compressive strength of Concrete Fc' (Mpa)`
- `Concrete Unit Weight (kN/m^3)`
- `Subgrade Modulus kN/m/m^2`
- `Column Area (m^2)`
- `Maximum Axial Load on Column in kN`
- `Total Axial load on Column (kN)`
- `Thickness of Raft (mm)`
- `Preffered Dia of Bars (mm) in Bottom direction X direction`
- `Preffered Dia of Bars (mm) X Top direction`
- `Preffered Dia of Bars (mm) Bottom Y direction`
- `Preffered Dia of Bars (mm) Top Y direction`
- `Bottom As (mm^2/m) X strip`
- `Top As (mm^2/m) X strip`
- `Bottom As (mm^2/m) Y strip`
- `Top As (mm^2/m) Y strip`

## Usage

### Running the Complete Pipeline

1. **Upload your Excel file** when prompted by the system
2. **Execute the main script** - the system will automatically:
   - Load and analyze your dataset
   - Test multiple ML algorithms
   - Select the best-performing model
   - Generate comprehensive results and visualizations

### Making Predictions with the Best Model

```python
# Example usage for new predictions
import pandas as pd

# Prepare input data
new_input = pd.DataFrame({
    'Number of  Columns': [16],
    'Area Of Raft (m^2)': [400],
    "Compressive strength of Concrete Fc' (Mpa)": [25],
    'Concrete Unit Weight (kN/m^3)': [25],
    'Subgrade Modulus kN/m/m^2': [30000],
    'Column Area (m^2)': [0.25],
    'Maximum Axial Load on Column in kN': [1500],
    'Total Axial load on Column (kN)': [24000],
    'Thickness of Raft (mm)': [500],
    'Preffered Dia of Bars (mm) in Bottom direction X direction': [16],
    'Preffered Dia of Bars (mm) X Top direction': [16],
    'Preffered Dia of Bars (mm) Bottom Y direction': [16],
    'Preffered Dia of Bars (mm) Top Y direction': [16]
})

# Make predictions
predictions = predict_new_sample_best(new_input)
print(predictions)
```

### Key Functions

- `predict_new_sample_best(input_features)`: Main prediction function for new samples
- `calculate_bar_spacing_and_count(area_required, bar_diameter)`: Structural calculation function
- `test_all_models(X, y)`: Comprehensive model testing function
- `evaluate_model_cv(model, X, y)`: Cross-validation evaluation function

## Code Structure

```
structural-reinforcement-ml/
├── main.py                    # Main execution script
├── README.md                  # This file
├── requirements.txt           # Python dependencies
└── data/
    └── sample_data.xlsx       # Sample input data
```

### Main Components

1. **Data Loading & Preprocessing (Steps 1-3)**
   - Excel file upload and analysis
   - Feature extraction and target definition
   - Data quality assessment

2. **Model Definitions (Steps 4-5)**
   - Structural engineering calculation functions
   - Neural network architectures
   - Model creation utilities

3. **Model Evaluation (Steps 6-8)**
   - Cross-validation implementation
   - Comprehensive model testing
   - Performance comparison

4. **Results & Visualization (Steps 9-14)**
   - Best model selection
   - Overfitting analysis
   - Prediction visualization
   - Performance reporting

## Examples

### Sample Input
```python
input_data = {
    'Number of  Columns': 16,
    'Area Of Raft (m^2)': 400,
    "Compressive strength of Concrete Fc' (Mpa)": 25,
    'Concrete Unit Weight (kN/m^3)': 25,
    'Subgrade Modulus kN/m/m^2': 30000,
    # ... other parameters
}
```

### Sample Output
```
Bottom As (mm²/m) X strip: 1250.45 mm²/m
Spacing (mm) Bottom X: 160 mm
Number of Bars for Bottom in X direction: 7 bars
Top As (mm²/m) X strip: 980.23 mm²/m
Spacing (mm) Top X: 200 mm
Number of Bars Top X: 6 bars
# ... additional outputs
```

### Performance Metrics
The system provides comprehensive performance analysis:
- **R² Score**: Coefficient of determination for each output
- **MAE**: Mean Absolute Error
- **RMSE**: Root Mean Square Error
- **Overfitting Analysis**: Training vs. test performance comparison

## Contributing Guidelines

We welcome contributions to improve this structural engineering ML solution!

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes**
   - Add new ML algorithms
   - Improve structural calculations
   - Enhance visualization
   - Add documentation

4. **Test your changes**
   - Ensure all models still work
   - Verify structural calculations
   - Test with sample data

5. **Submit a pull request**
   - Provide clear description of changes
   - Include test results
   - Reference any related issues

### Development Standards

- Follow PEP 8 style guidelines
- Add comprehensive docstrings
- Include unit tests for new functions
- Update documentation as needed
- Ensure backward compatibility

### Areas for Contribution

- **New ML Algorithms**: Add support for additional algorithms
- **Enhanced Visualizations**: Improve plotting and analysis tools
- **Performance Optimization**: Optimize model training and prediction
- **Documentation**: Improve code documentation and examples
- **Testing**: Add comprehensive unit tests
- **UI/UX**: Develop web interface or GUI

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 Structural Reinforcement ML Predictor

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## Acknowledgments

- Built for structural engineering applications
- Incorporates industry-standard reinforcement design principles
- Optimized for concrete raft foundation analysis

## Support

For questions, issues, or contributions, please open an issue on the GitHub repository or contact the development team.

**Note**: This tool is designed for engineering analysis and should be used in conjunction with professional structural engineering expertise and code compliance verification.
