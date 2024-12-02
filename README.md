# Description
This project analyses Netflix shows and movies through a modular pipeline. Each step of the pipeline such as data preparation, data cleaning, data exploration, and data visualization is handled in separate Jupyter Notebooks. The entire workflow has been automated using Papermill to execute these notebooks sequentially.

# Netflix Data Visualization Project  

This project provides an automated, modular pipeline for analyzing a Netflix dataset. The pipeline handles **data preparation**, **cleaning**, **exploration**, and **visualization** through separate Jupyter notebooks, with automation powered by **Papermill** for reproducibility and efficiency.  

---

## Requirements  

- Python 3.x  
- R with the **ggplot2** package  

### Python Libraries:  
```python  
import os  
import zipfile  
import pandas as pd  
import matplotlib.pyplot as plt  
import seaborn as sns  
import papermill as pm  
```  

---

## Project Structure  

```  
├── Main_Netflix.ipynb               # Master notebook to automate the pipeline  
├── 01_data_preparation.ipynb        # Data extraction and initial loading  
├── 02_data_cleaning.ipynb           # Data cleaning and preprocessing  
├── 03_data_exploration.ipynb        # Exploratory data analysis (EDA)  
├── 04_data_visualization.ipynb      # Data visualization with charts and plots  
├── Netflix_Data_Visualization2.R    # R-based visualization (integration practice)  
├── Netflix_data.zip                 # Zipped dataset file  
└── README.md                        # Project documentation  
```  

---

## Pipeline Workflow  

### **1. Master Pipeline Execution (Main_Netflix.ipynb)**  
The master notebook orchestrates the execution of each stage using **Papermill**, passing inputs and capturing outputs. Example Papermill code:  
```python  
pm.execute_notebook(  
   '01_data_preparation.ipynb',  
   'output_data_preparation.ipynb',  
   parameters={'input_file': 'Netflix_shows_movies.csv', 'output_file': 'output_data_preparation.csv'}  
)  
```  

---

## 2. Individual Notebook Breakdown  

### **01_data_preparation.ipynb**  
**Input:** `Netflix_shows_movies.csv`  
**Output:** `output_data_preparation.csv`  
**Tasks:**  
- Unzips and renames the dataset.  
- Loads the dataset into a DataFrame.  
- Handles file-related errors and previews the first five rows.  

### **02_data_cleaning.ipynb**  
**Input:** `output_data_preparation.csv`  
**Output:** `output_data_cleaning.csv`  
**Tasks:**  
- Identifies and handles missing values by replacing them with "Unknown."  
- Validates and saves the cleaned dataset.  

### **03_data_exploration.ipynb**  
**Input:** `output_data_cleaning.csv`  
**Output:** `output_data_exploration.csv`  
**Tasks:**  
- Analyzes key columns like:  
  - **Type:** TV shows vs. movies distribution.  
  - **Genres:** Most frequent genres.  
  - **Ratings:** Content rating distribution.  
  - **Release Year:** Content trends over time.  
  - **Country:** Top countries producing Netflix content.  

### **04_data_visualization.ipynb**  
**Input:** `output_data_exploration.csv`  
**Output:** Visual plots (saved as PNG files).  
**Tasks:**  
- Generates bar charts, pie charts, and other visuals for:  
  - **Most Watched Genres**  
  - **Rating Distribution**  
  - **Content Type Distribution**  
  - **Top Release Years**  

**Example Python Code:**  
```python  
sns.barplot(data=df, x='genre', y='count')  
plt.title('Most Watched Genres on Netflix')  
plt.savefig('most_watched_genres.png')  
```  

---

## R Integration  

An additional visualization is replicated in R using the **ggplot2** package, highlighting cross-tool flexibility.  
Run *Netflix_Data_Visualization2.R* in R studio
Make sure the correct image path is inserted into the code and the image should be in the same location.

---

## Error Handling  

### Common Error Example:  
**NameError:** `name 'df' is not defined`  
- **Cause:** Occurs when variables are not passed correctly between notebooks.  
- **Solution:** Use **Papermill** to pass parameters. Example:  
  ```python  
  pm.execute_notebook(  
      '02_data_cleaning.ipynb',  
      'output_data_cleaning.ipynb',  
      parameters={'input_file': 'output_data_preparation.csv', 'output_file': 'output_data_cleaning.csv'}  
  )  
  ```  

**Troubleshooting:**  
- Ensure parameter cells in each notebook are tagged with `"parameters"`.  
- Manually tag cells:  
Manually Tagging Cells in Jupyter Notebook:
Enter Edit Mode:

Open the notebook and click on the cell that contains the input_file and output_file variables.
Open the Cell Toolbar:

In Jupyter Notebook, the "Tags" feature is actually accessed via a "Cell Toolbar." To open it, follow this:
Click on the View menu (top left of your Jupyter Notebook interface).
Then select Cell Toolbar → Edit Metadata.
Edit Metadata:

After selecting Edit Metadata, a small "Edit Metadata" box will appear on the right side of the notebook.
In this box, you can manually add metadata tags for the cell.
Add the parameters Tag:

To tag the cell with parameters, you need to add the following metadata:
json
Copy code
{
    "tags": ["parameters"]
}
If there’s already some metadata there, simply add the "parameters" tag to the "tags" array. If the "tags" array doesn’t exist, you can add it manually.
Save the Metadata:

After you add the tag, click the Save button on the right side to save the changes.

## Advantages of a Modular Pipeline  

- **Modularity:** Each stage operates independently, simplifying debugging and updates.  
- **Reusability:** Notebooks can be reused in other projects.  
- **Version Control:** Changes are easier to track.  
- **Parallel Execution:** Only update and run specific steps as needed.  

---

## Running the Pipeline  

- **Manual Execution:** Run each notebook step-by-step in Jupyter.  
- **Automated Execution:** Use the **Main_Netflix.ipynb** notebook to run all stages sequentially.  

---

## Outputs  

- **Cleaned Data:** `output_data_cleaning.csv`  
- **Exploratory Data:** `output_data_exploration.csv`  
- **Visualizations:** PNG files saved in the directory, including:  
  - Most Watched Genres  
  - Distribution of Content Types  
  - Content Ratings  
  - Top Producing Countries  
  - Top Release Years  

---

## Conclusion  

This project effectively analyzed Netflix’s dataset using a modular pipeline approach. The separation of data preparation, cleaning, exploration, and visualization enhanced organization, reusability, and flexibility. **Papermill** facilitated automation and reproducibility, making the workflow efficient and scalable. Insights from the analysis include genre trends, content types, and production patterns over time, all presented through clear visualizations.

