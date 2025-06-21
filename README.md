# lab1_titanic_Gerbise

This project performs basic Exploratory Data Analysis (EDA) on the Titanic dataset (titanic.csv) using Pandas, Matplotlib, and Seaborn to uncover insights about passenger survival.

1. We load the Titanic dataset using pandas and preview the first few rows to understand the structure.

df = pd.read_csv("titanic.csv")
df.head()

2. We identify columns with missing values to understand data quality and decide on cleaning strategies.

df.isnull().sum()

3. We calculate the overall survival rate by averaging the "Survived" column, where 1 = survived and 0 = did not survive.

df["Survived"].mean()

4. We display the unique embarkation points (Embarked) and count passengers per class (Pclass) from each port.

print(df["Embarked"].unique())
print(df.groupby("Embarked")["Pclass"].value_counts())

5. We create a bar chart showing the percentage of passengers who survived and who did not.

survived_count = df["Survived"].value_counts(normalize=True) * 100

6. We group passengers by gender and compute survival rates, then display the results in a bar chart.

gender_survival = df.groupby("Sex")["Survived"].mean() * 100

7. We add a new column indicating whether a passenger had a recorded cabin, then analyze its impact on survival.

df["HasCabin"] = df["Cabin"].notna()

7.1 We group by cabin availability and visualize the survival rate difference.

cabin_survival = df.groupby(df["HasCabin"].map({True: "Has Cabin", False: "No Cabin"}))["Survived"].mean() * 100
