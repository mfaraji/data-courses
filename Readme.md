# How to Get the Dataset

To complete the pandas exercise, you’ll need a dataset. Below are several ways to obtain or create one:

---

## 1. **Download a Sample Dataset**

### **Kaggle**
- Visit [Kaggle Datasets](https://www.kaggle.com/datasets).
- Search for a dataset (e.g., "retail sales" or "e-commerce data").
- Download the dataset as a CSV file (requires a free Kaggle account).

### **Google Dataset Search**
- Use [Google Dataset Search](https://datasetsearch.research.google.com/) to find datasets from various sources.

### **Open Data Portals**
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/index.php)
- [Data.gov](https://www.data.gov/)
- [Awesome Public Datasets (GitHub)](https://github.com/awesomedata/awesome-public-datasets)

---

## 2. **Generate a Synthetic Dataset with Python**

You can create a synthetic dataset programmatically using Python. Below is an example script to generate a dataset named `sales_data.csv`:

```python
import pandas as pd
import numpy as np
from faker import Faker

# Generate synthetic data
faker = Faker()
num_records = 1000

data = {
    "OrderID": [faker.uuid4()[:8] for _ in range(num_records)],
    "Date": [faker.date_between(start_date="-1y", end_date="today") for _ in range(num_records)],
    "CustomerID": [faker.uuid4()[:8] for _ in range(num_records)],
    "Product": np.random.choice(["Laptop", "Smartphone", "Tablet", "Headphones", "Monitor"], num_records),
    "Category": np.random.choice(["Electronics", "Accessories"], num_records),
    "Quantity": np.random.randint(1, 10, num_records),
    "UnitPrice": np.random.uniform(50, 1000, num_records).round(2),
}

# Calculate total revenue
data["TotalRevenue"] = (data["Quantity"] * data["UnitPrice"]).round(2)

# Create DataFrame
df = pd.DataFrame(data)

# Save to CSV
df.to_csv("sales_data.csv", index=False)

print("Synthetic dataset created: 'sales_data.csv'")
