# gender_bias_ai_corrections
A resource for developers to train AI models to identify and correct gender stereotypes, exclusion, and underrepresentation in educational materials. Includes biased and corrected text examples across STEM, history, literature, and more.

## Motivation
AI models can perpetuate harmful gender stereotypes prevailing in society. This dataset aims to provide a resource for building more inclusive AI educational tools.

## Dataset Structure
This dataset is available in two formats:
* `gender_bias_correction_dataset_v1.0.csv`: Comma-separated values file.
* `gender_bias_correction_dataset_v1.0.json`: JSON format.

Both formats contain the same data with the following columns:
* `ID`: Unique identifier.
* `Category`: Type of content (Science & Technology, Coding, History etc.).
* 'Reviewed': Can take values 'Y' or 'N' indicating whether the record has been reviewed by a human or not.
* `Biased_Statement`: The gender-biased statement. Eg. "Great scientists like Einstein and Newton changed the world."
* `Corrected_Statement`: More inclusive alternative statement. Eg. "Great scientists like Einstein, Newton, and Marie Curie changed the world."
* `Bias_Type`: Type of bias - can take one of the four types: 'Exclusion', 'Stereotype', 'Underrepresentation', 'Language Bias'.

## Methodology

### Data Collection and Correction
* This dataset is synthetically generated with AI through few-shot prompting requiring AI to generate commonly found biased statements and applying corrections based on the principles of inclusivity. 
* To include a statement in the dataset, we had to verify that the (i) The statement reflects bias inherently and (ii) is a prevailing opinion in atleast a significant minority of population today. 
* For example, "Female teachers are incapable of teaching advanced concepts." is not a prevailing opinion that needs correction and hence would be excluded. Or "The school's advanced physics class has only male students." is not a statement reflecting bias, but an outcome of bias, and hence would be excluded. 
* The corrected statement must reflect reasonable accuracy and historical context where needed to explain the facts observed today instead of simply opposing the bias. 
* For example, "Men have been the primary earners in most households." is corrected as "In the past, men were often the primary earners, but today, both men and women contribute significantly." Here we use the word 'significantly' instead of 'equally' to reflect the society more accurately.

### Dataset Validation
The biased and corrected statements were verified through (i) Human validation (ii) Peer review and (iii) AI check . Topic and bias categorization were verified through AI and human validation.

## Usage

### Example (Python, CSV)
```python
import pandas as pd

df = pd.read_csv("gender_bias_correction_dataset_v1.0.csv")
print(df.head())
```
### Example (Python, JSON)
```python
import json

with open("gender_bias_correction_dataset_v1.0.json", "r") as f:
    data = json.load(f)
print(data[0])
```
## Contributing
Contributions are welcome! Here's how you can contribute:

### Adding New Data
To add new biased/corrected statement pairs:

1.  Fork this repository.
2.  Create a new branch for your changes.
3.  Add new rows to the `gender_bias_dataset.csv` file, following the existing format.
4.  Ensure that the biased statement clearly demonstrates gender bias and that the corrected statement is neutral and factual.
5.  Submit a pull request with your changes.

Example:
| ID   | Category | Reviewed | Biased Statement                                 | Corrected Statement                                   | Bias Type |
| ---- | -------- | -------- | ------------------------------------------------ | --------------------------------------------------- | --------- |
| 138  | History  |     N     | "The brave pioneers, all men, settled the west." | "The brave pioneers settled the west."                | Exclusion |

### Improving Existing Data
If you find errors or have suggestions for improvements, please submit a pull request with your changes.

### Suggesting New Categories or Bias Types
To suggest new categories or bias types, please create an issue with a clear description and examples.

### Pull Request Process
1.  Fork the repository.
2.  Create a new branch for your changes.
3.  Make your changes.
4.  Submit a pull request.
5.  Your changes will be reviewed, and if approved, merged into the main branch.

## License
This dataset is licensed under the MIT License.
