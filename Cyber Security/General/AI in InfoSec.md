
## Introduction

You will construct three distinct `AI` models in this module:

1. A `Spam Classifier` to determine whether an SMS message is `spam` or not.
2. A `Network Anomaly Detection Model` designed to identify abnormal or potentially malicious network traffic.
3. A `Malware Classifier` using `byteplots`, which are visual representations of binary data.

### Environment setup

while HTB offer two option for setup (Playground and miniconda with Jupiter lab), I will just used me local setup and install any python lib during the Course.

### Python Libraries for AI

during this course will used two libraries `Scikit-learn` and `Pytorch`, so let's download these two libraries

```
pip install scikit-learn torch
```

### Datasets

`Datasets` are structured collections of data used for analysis and model training. Including

- `Tabular Data`: Data organized into tables with rows and columns, common in spreadsheets or databases.
- `Image Data`: Sets of images represented numerically as pixel arrays.
- `Text Data`: Unstructured data composed of sentences, paragraphs, or full documents.
- `Time Series Data`: Sequential data points collected over time, emphasizing temporal patterns.


The provided dataset, [demo_dataset.csv](https://academy.hackthebox.com/storage/modules/292/demo_dataset.zip) is a `CSV` file containing network log entries.

now let's write some code to do some basic functions on this dataset
1. Load Dataset
2. show some row from the dataset
3. show summary of the dataset
4. Identify missing values of each columns

```python
import pandas as pd

# Load the dataset
data = pd.read_csv("demo_dataset.csv")

# Display the first few rows
print(data.head())

# Get a summary of the dataset
print(data.info())

# Identify missing values
print(data.isnull().sum())
```


### Data Preprocessing

**Data preprocessing** transforms raw data into a suitable format for machine learning algorithms. Key techniques include:

- `Data Cleaning`: Handling missing values, removing duplicates, and smoothing noisy data.
- `Data Transformation`: Normalizing, encoding, scaling, and reducing data.
- `Data Integration`: Merging and aggregating data from multiple sources.
- `Data Formatting`: Converting data types and reshaping data structures.

now will write some code snippet to validate the each data column in the dataset we have.

**Identify invalid IP address**

```python
import re
import pandas as pd


def is_valid_ip(ip):
    pattern = re.compile(r'^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$')
    return bool(pattern.match(ip))


# Load the dataset
data = pd.read_csv("demo_dataset.csv") 

# Check for invalid IP addresses
invalid_ips = data[~data['source_ip'].astype(str).apply(is_valid_ip)]
print(invalid_ips)
```

![[Pasted image 20250830083120.png]]

**Check Invalid Port Number**
```python
import re
import pandas as pd


def is_valid_port(port):
    try:
        port = int(port)
        return 0 <= port <= 65535
    except ValueError:
        return False


# Load the dataset
data = pd.read_csv("demo_dataset.csv")

# Check for invalid port numbers
invalid_ports = data[~data['destination_port'].apply(is_valid_port)]
print(invalid_ports)
```

![[Pasted image 20250830091427.png]]
in the same way as IP and port will check invalid `protocols`, `bytes_transferred` and `thread_level`.

After identify invalid parts in the dataset, will start to handle the invalid data.

