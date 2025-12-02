# 🚢 PortFlow Analytics: Global Maritime Port Activity Analysis

## 📊 Project Overview

**PortFlow Analytics** is a comprehensive data analysis project that examines global maritime port operations to uncover patterns in vessel traffic, port activity distributions, and geographical shipping trends. This analysis provides valuable insights into maritime logistics, port efficiency, and global supply chain dynamics using real-world port data from 480 ports worldwide.

## 🎯 Project Objectives

1. **Explore Distribution Patterns**: Analyze the statistical distributions of vessels in port, arrivals, departures, and expected arrivals
2. **Identify Outliers**: Detect and analyze extreme values in port activity metrics
3. **Statistical Profiling**: Generate comprehensive statistical summaries including skewness and kurtosis
4. **Visualize Insights**: Create interactive visualizations to communicate findings effectively
5. **Industry Insights**: Provide actionable insights for port authorities, shipping companies, and logistics planners

## 📁 Dataset Information

**File**: `Port_Data.csv`  
**Records**: 480 ports worldwide  
**Source**: Maritime port operations data

### Dataset Features

| Column | Description | Data Type |
|--------|-------------|-----------|
| `Country` | Port location by country | Object |
| `Port Name` | Official name of the port | Object |
| `UN Code` | Unique UN identifier for each port | Object |
| `Vessels in Port` | Current number of vessels docked | Integer |
| `Departures(Last 24 Hours)` | Vessels that departed recently | Integer |
| `Arrivals(Last 24 Hours)` | Vessels that arrived recently | Integer |
| `Expected Arrivals` | Vessels scheduled to arrive | Integer |
| `Type` | Port classification (Port, Anchorage, etc.) | Object |
| `Area Local` | Local geographical classification | Object |
| `Area Global` | Global geographical classification | Object |
| `Also known as` | Alternative names and aliases | Object |

## 🛠 Technical Stack

### Core Libraries
- **Python 3.x**
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computations
- **Matplotlib** - Static visualizations
- **Seaborn** - Statistical visualizations
- **Plotly** - Interactive visualizations
- **SciPy** - Statistical analysis
- **Scikit-learn** - Machine learning utilities
- **NetworkX** - Network analysis (potential future use)

### Key Skills Demonstrated
- Data Cleaning & Preprocessing
- Exploratory Data Analysis (EDA)
- Statistical Analysis
- Data Visualization
- Outlier Detection
- Maritime Industry Analytics

## 📈 Project Structure

```
port-data-analysis/
│
├── port-data-analysis.ipynb    # Main Jupyter Notebook
├── Port_Data.csv               # Dataset
├── README.md                   # This file
│
├── analysis/
│   ├── distribution_analysis/  # Distribution analysis scripts
│   ├── visualization/          # Visualization modules
│   └── statistical_tests/      # Statistical testing modules
│
└── outputs/
    ├── plots/                  # Generated visualizations
    ├── reports/                # Analysis reports
    └── summaries/              # Statistical summaries
```

## 🔧 Installation & Setup

### Prerequisites
```bash
# Clone the repository
git clone <repository-url>
cd port-data-analysis

# Create virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install required packages
pip install -r requirements.txt
```

### Requirements File
Create a `requirements.txt` file with:
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
plotly>=5.0.0
scipy>=1.7.0
scikit-learn>=0.24.0
networkx>=2.6.0
jupyter>=1.0.0
```

## 📊 Analysis Workflow

### 1. Data Loading & Initial Inspection
```python
# Load dataset
df = pd.read_csv("/home/blackest/data_analysis_learn/ship-ports/Port_Data.csv")

# Initial inspection
df.head()
df.info()
df.describe()
```

### 2. Data Preprocessing
```python
# Drop irrelevant column
df_clean = df.drop('Unnamed: 0', axis=1)

# Parse aliases from "Also known as" column
import ast
def safe_parse_aliases(alias_str):
    if pd.isna(alias_str) or alias_str == "[]" or alias_str == "['-']":
        return []
    try:
        cleaned = alias_str.replace("'", '"').replace('"', "'")
        return ast.literal_eval(cleaned)
    except:
        return [alias_str] if alias_str and alias_str != "-" else []

df_clean['Aliases_List'] = df_clean['Also known as'].apply(safe_parse_aliases)
df_clean['Alias_Count'] = df_clean['Aliases_List'].apply(len)
```

### 3. Distribution Analysis
Analyzed four key numerical variables:
- Vessels in Port
- Departures (Last 24 Hours)
- Arrivals (Last 24 Hours)
- Expected Arrivals

### 4. Statistical Analysis
Generated comprehensive statistics including:
- Mean and median values
- Standard deviation
- Skewness and kurtosis
- Quartile distributions

### 5. Visualization
Created interactive plots using Plotly:
- Multi-panel histogram distributions
- Box plots for outlier detection
- Statistical annotation overlays

## 📈 Key Findings

### Statistical Summary

| Metric | Mean | Median | Std Dev | Skewness | Kurtosis |
|--------|------|--------|---------|----------|----------|
| **Vessels in Port** | 153.3 | 86.0 | 217.3 | 5.21 | 36.45 |
| **Departures (24h)** | 99.0 | 48.0 | 170.5 | 5.14 | 33.32 |
| **Arrivals (24h)** | 108.7 | 56.0 | 185.4 | 5.06 | 31.87 |
| **Expected Arrivals** | 39.2 | 16.0 | 82.4 | 7.84 | 92.06 |

### Major Insights

1. **Highly Skewed Distributions**: All metrics show strong positive skewness
2. **Outlier Ports**: A few major ports handle exceptionally high traffic
3. **China Dominance**: Multiple Chinese ports in top 10 by vessel count
4. **Singapore**: Key global hub with high departures/arrivals
5. **Activity Patterns**: Arrivals generally exceed departures across ports

### Top Ports by Vessel Count
1. **Shanghai, China** - 2,420 vessels
2. **Nantong, China** - 1,572 vessels
3. **CJK (Changjiangkou), China** - 1,529 vessels
4. **Nanjing, China** - 1,414 vessels
5. **Singapore** - 1,109 vessels

## 🎨 Visualizations

### 1. Distribution Analysis Dashboard
- Four-panel histogram layout
- Mean and median markers
- Interactive hover information
- Downloadable plots

### 2. Outlier Detection
- Box plots for each numerical variable
- Extreme value identification
- Statistical range visualization

### 3. Statistical Annotations
- Automated annotation of key statistics
- Clear labeling of distribution characteristics
- Comparative analysis across metrics

## 🚀 How to Run the Analysis

### Option 1: Jupyter Notebook
```bash
jupyter notebook port-data-analysis.ipynb
```

### Option 2: Python Script
```bash
python -m analysis.run_full_analysis
```

### Option 3: Step-by-Step Execution
1. Open the Jupyter notebook
2. Run cells sequentially
3. View outputs and visualizations inline
4. Export results as needed


## 📊 Business Applications

### For Port Authorities
- Optimize resource allocation
- Improve operational efficiency
- Plan infrastructure investments
- Benchmark against global peers

### For Shipping Companies
- Route planning optimization
- Port selection strategies
- Schedule reliability analysis
- Cost optimization

### For Logistics Planners
- Supply chain optimization
- Risk management
- Capacity planning
- Market analysis

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/your-feature`
3. **Commit your changes**: `git commit -m 'Add some feature'`
4. **Push to the branch**: `git push origin feature/your-feature`
5. **Open a Pull Request**

### Contribution Areas
- Additional analysis methods
- New visualizations
- Performance optimizations
- Documentation improvements
- Dataset expansions

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **Dataset Providers**: Maritime data collection teams
- **Open Source Community**: Maintainers of Python data science libraries
- **Industry Experts**: Maritime logistics professionals
- **Educational Resources**: Data science learning platforms

## 📞 Contact & Support

For questions, suggestions, or collaboration opportunities:

- **Email**: [johnmuritu22@gmail.com]
- **LinkedIn**: [https://www.linkedin.com/in/ndungu-muritu-73768028a/]

## 📚 Resources & References

### Technical Documentation
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Plotly Python Documentation](https://plotly.com/python/)
- [Scikit-learn User Guide](https://scikit-learn.org/stable/user_guide.html)

### Maritime Industry Resources
- [International Maritime Organization](https://www.imo.org/)
- [World Shipping Council](https://www.worldshipping.org/)
- [Port Technology International](https://www.porttechnology.org/)

### Data Science Learning

- [Coursera Data Science Specialization](https://www.coursera.org/specializations/data-science)
- [Kaggle Datasets](https://www.kaggle.com/datasets)

---

**⭐ If you find this project useful, please give it a star on GitHub!**

---

*Last Updated: November 2023*  
*Version: 1.0.0*
