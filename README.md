# Student Performance Analysis with Fuzzy Logic

This project utilizes a fuzzy logic approach to analyze student performance data. The analysis is based on multiple factors, including GPA, weekly study time, and absences, to compute a reward metric. The dataset used in this analysis is the [Students Performance Dataset](https://www.kaggle.com/datasets/rabieelkharoua/students-performance-dataset).

## Dataset

The dataset contains information on various student performance metrics such as:
- **GPA**: Grade Point Average (on a 4-point scale).
- **StudyTimeWeekly**: Weekly study time (in hours).
- **Absences**: Number of absences.
- Additional variables related to extracurricular activities, parental support, and more.

## Prerequisites

To run the notebook, the following Python libraries must be installed:
- `numpy`
- `pandas`
- `scikit-fuzzy`

You can install the required libraries using the following command:

```bash
pip install numpy pandas scikit-fuzzy
```

## Project Workflow

1. **Dataset Loading**:
   - The dataset is loaded and inspected to understand its structure and data types.

2. **Fuzzy Variables Definition**:
   - Fuzzy variables are created for GPA, study time, and absences.
   - Membership functions are defined for these variables (e.g., low, medium, high).

3. **Fuzzy Rules Creation**:
   - Rules are established to compute a reward score based on the interaction of GPA, study time, and absences.

   Example Rules:
   - If GPA is high and study time is high, then reward is high.
   - If GPA is low and absences are high, then reward is low.

4. **Fuzzy System Simulation**:
   - A control system is created using the defined rules.
   - Rewards are computed for each student based on their performance data.

5. **Output and Analysis**:
   - The computed rewards for each student are displayed.

## Sample Code

```python
import numpy as np
import pandas as pd
import skfuzzy as fuzz
from skfuzzy import control as ctrl

# Define fuzzy variables
gpa = ctrl.Antecedent(np.arange(0, 4.1, 0.1), 'GPA')
study_time = ctrl.Antecedent(np.arange(0, 21, 1), 'StudyTimeWeekly')
absences = ctrl.Antecedent(np.arange(0, 31, 1), 'Absences')
reward = ctrl.Consequent(np.arange(0, 101, 1), 'Reward')

# Define membership functions
gpa['low'] = fuzz.trapmf(gpa.universe, [0, 0, 2.0, 2.5])
...
```

## Results

The fuzzy logic model provides a reward metric for students based on their GPA, study time, and absences. This reward can help identify areas for improvement and suggest interventions for better performance.

## References

- [Scikit-Fuzzy Documentation](https://pythonhosted.org/scikit-fuzzy/)
- [Students Performance Dataset](https://www.kaggle.com/datasets/rabieelkharoua/students-performance-dataset)

## Contributing

Contributions are welcome! Please feel free to submit a pull request or raise an issue for any suggestions or bugs.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
