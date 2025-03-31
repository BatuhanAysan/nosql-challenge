# 🥗 NoSQL Challenge – UK Food Standards Analysis

This project is a data engineering and analysis challenge focused on exploring food hygiene data across the United Kingdom. The source dataset comes from the UK Food Standards Agency and contains detailed records of establishments including their hygiene scores and ratings.

## 📌 Objective

The goal of this project is to clean, update, and analyze a NoSQL database using MongoDB. The final analysis helps a fictional food magazine, *Eat Safe, Love*, decide where to focus future articles based on hygiene ratings.

---

## 🛠️ Tools & Technologies

- **MongoDB**: NoSQL database
- **PyMongo**: Python MongoDB driver
- **pprint**: For formatted output of Mongo documents
- **Pandas**: DataFrame handling for tabular analysis
- **Jupyter Notebook**: Code development environment

---

## ▶️ How to Run This Project

To run this project locally, follow the steps below:

### 1. Clone the Repository

```bash
git clone https://github.com/BatuhanAysan/nosql-challenge.git
cd nosql-challenge
```

### 2. Start MongoDB

Ensure MongoDB is installed and running on your local machine at the default port `27017`.

> You can check if MongoDB is running by using:
>
> ```bash
> mongod
> ```

### 3. Import the Dataset

Use the following command in your terminal to import the JSON file into MongoDB:

```bash
mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json
```

This will:
- Import the data from `establishments.json`
- Drop any existing `establishments` collection in the `uk_food` database
- Create a new collection with the data

### 4. Launch Jupyter Notebook

Make sure Jupyter is installed, then run:

```bash
jupyter notebook
```

Open the following notebooks in your browser:
- `NoSQL_setup_starter.ipynb` → For database setup and data cleaning
- `NoSQL_analysis_starter.ipynb` → For analysis and querying

Run each cell in order to reproduce the full workflow and results.

### ✅ Requirements

Make sure you have the following installed:

- [MongoDB Community Edition](https://www.mongodb.com/try/download/community)
- Python >= 3.8
- Jupyter Notebook
- Python packages:
  - `pymongo`
  - `pandas`

---

## 📂 Project Structure

nosql-challenge/
├── Resources/
│   └── establishments.json
├── NoSQL_setup_starter.ipynb
├── NoSQL_analysis_starter.ipynb
└── README.md


---

## 📈 Project Workflow

### Part 1: Database and Jupyter Notebook Setup
- Imported data using:

  ```bash
  mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json

---

## 🔌 Database Setup

- Connected to MongoDB via **PyMongo**
- Verified that the database and collections were correctly created and loaded

---

## 🛠️ Part 2: Update the Database

- ✅ Added a new halal restaurant: **Penang Flavours**
- ✅ Found and updated the correct `BusinessTypeID` for restaurants
- ✅ Removed all records under the **Dover** local authority
- ✅ Converted the following fields to proper data types:
  - `geocode.latitude` and `geocode.longitude` → *float*
  - `RatingValue` → *int* (non-numeric values were set to `null`)

---

## 📊 Part 3: Exploratory Analysis

### ✅ Question 1: Establishments with Hygiene Score = 20
- Found **41** such establishments

### ✅ Question 2: Establishments in London with Rating ≥ 4
- Found **33** establishments using **regex** search on `LocalAuthorityName`

### ✅ Question 3: Top 5 closest establishments (to *Penang Flavours*) with Rating 5 and lowest hygiene scores
- Used **geospatial filtering** within `0.01°` range and sorted by hygiene score

### ✅ Question 4: Local Authorities with Most Establishments Having Hygiene Score 0
- Used **aggregation pipeline** to count and sort results
- **Top 5:**
  - Thanet
  - Greenwich
  - Maidstone
  - Newham
  - Swale

---

## 📬 Author

**Batuhan Aysan**  
March 2025

---

## ✅ Status

✅ Completed – All requirements met and tested in MongoDB and Jupyter Notebook.
