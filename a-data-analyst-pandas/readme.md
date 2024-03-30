# PANDAS Complete

### In this, we will cover all aspects of Pandas.

## Series

```py

ice_cream = ["Chocolate", "Vanilla", "Strawberry", "Rum Raisin"]
pd.Series(ice_cream)

sushi = {
    "Salmon": "Orange",
    "Tuna": "Red",
    "Eel": "Brown"
}
pd.Series(sushi)

prices = pd.Series([2.99, 4.45, 1.36])
prices.sum() # mean, product, std

adjectives = pd.Series(["Smart", "Handsome", "Charming", "Brilliant", "Humble", "Smart"])
adjectives.unique()
adjectives.value_counts()
adjectives.size
adjectives.values
adjectives.index

fruits = ["Apple", "Orange", "Plum", "Grape", "Blueberry", "Watermelon"]
weekdays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Monday"]
pd.Series(data=fruits, index=weekdays)


pokemon = pd.read_csv("./pokemon.csv", usecols=["Name"]).squeeze("columns")
google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")

google.head()
google.tail()

sorted_lst = sorted(pokemon, reverse=True)
print(max(google))
print(min(google))


5 in pokemon.index
"Bulbasaur" in pokemon.values

pokemon.sort_values(ascending=False)


pokemon = pd.read_csv("pokemon.csv", index_col="Name").squeeze("columns") 
pokemon.sort_index(ascending=True)


pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon.iloc[10]
pokemon.iloc[700:1010]

pokemon = pd.read_csv("pokemon.csv", index_col="Name").squeeze("columns")
pokemon.loc["Bulbasaur"]
pokemon.loc[["Charizard", "Jolteon", "Meowth"]]

pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon.iloc[0] = "Borisaur"
pokemon.iloc[[1, 2, 4]] = ["Firemon", "Flamemon", "Blazemon"]

pokemon_df = pd.read_csv("pokemon.csv", usecols=["Name"])
pokemon_series = pokemon_df.squeeze("columns").copy()


google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")
google.count()
google.sum()
google.product()
google.mean()
google.std()
google.max()
google.min()
google.median()
google.mode()
google.describe()


google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")
google + 2

pokemon = pd.read_csv("pokemon.csv", index_col="Name").squeeze("columns")
pokemon.value_counts()

pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon.apply(lambda x: x + "_add")

pokemon = pd.read_csv("pokemon.csv", index_col="Name").squeeze("columns")
attack_powers = pd.Series({
    "Grass": 10,
    "Fire": 15,
    "Water": 15,
    "Fairy, Fighting": 20,
    "Grass, Psychic": 50
})
pokemon.map(attack_powers)

```

## Dataframes Basics

```py

nba = pd.read_csv("nba.csv")
nba.head(3)

nba.index
nba.values[0] # get the 0th row
nba.shape
nba.dtypes
nba.columns
nba.axes
nba.info()

revenue = pd.read_csv("revenue.csv", index_col="Date")
revenue.sum(axis="index")
revenue.product(axis="columns")

nba.Team
type(nba.Name) # pandas.core.series.Series
names = nba["Name"].copy()
names.iloc[0] = "Whatever"

nba = pd.read_csv("nba.csv")
columns_to_select = ["Salary", "Team", "Name"]
nba[columns_to_select]

nba["Position"].value_counts(normalize=True) * 100
nba.dropna(how="any")
nba.dropna(how="all")
nba.dropna(subset=["College", "Salary"])

nba = pd.read_csv("nba.csv").dropna(how="all")
nba["Salary"] = nba["Salary"].fillna(0)
nba["College"] = nba["College"].fillna(value="Unknown")


nba = pd.read_csv("nba.csv").dropna(how="all")
nba["Salary"] = nba["Salary"].fillna(0)
nba.dtypes

nba["Salary"] = nba["Salary"].astype(int)


nba["Team"].nunique()
nba["Position"] = nba["Position"].astype("category")
nba["Team"] = nba["Team"].astype("category")

nba.sort_values("Salary", ascending=False)
nba.sort_values("Salary", na_position="first", ascending=False)
nba.sort_values(["Position", "Salary"], ascending=[True, False])
nba.sort_index(ascending=False)


nba = pd.read_csv("nba.csv").dropna(how="all")
nba["Salary"] = nba["Salary"].fillna(0).astype(int)
nba["Salary Rank"] = nba["Salary"].rank(ascending=True).astype(int)

```

## Dataframes : Data Filtering

```py

employees = pd.read_csv("employees.csv")
employees["Start Date"] = pd.to_datetime(employees["Start Date"], format = "%m/%d/%Y")

employees["Last Login Time"] = pd.to_datetime(employees["Last Login Time"], format="%H:%M %p").dt.time
employees["Senior Management"] = employees["Senior Management"].astype(bool)


employees = pd.read_csv("employees.csv", parse_dates=["Start Date"], date_format="%m/%d/%Y")
employees["Last Login Time"] = pd.to_datetime(employees["Last Login Time"], format="%H:%M %p").dt.time

employees[employees["Gender"] == "Male"]
employees[employees["Salary"] > 110000]
employees[employees["Bonus %"] < 1.5]
employees[employees["Start Date"] < "1985-01-01"]
employees[employees["Last Login Time"] < dt.time(12, 0, 0)]

is_female = employees["Gender"] == "Female"
is_in_marketing = employees["Team"] == "Marketing"
salary_over_100k = employees["Salary"] > 100000
employees[is_female & is_in_marketing & salary_over_100k]

is_senior_management = employees["Senior Management"]
started_in_80s = employees["Start Date"] < "1990-01-01"
employees[is_senior_management | started_in_80s]

target_teams = employees["Team"].isin(["Legal", "Sales", "Product"])
employees[target_teams]

employees[employees["Team"].isnull()]
employees[employees["Team"].notnull()]


employees[employees["Bonus %"].between(2.0, 5.0)]
employees[employees["Start Date"].between("1991-01-01", "1992-01-01")]
employees[employees["Last Login Time"].between(dt.time(8, 30), dt.time(12, 0))]

employees[employees["First Name"].duplicated(keep="first")]
employees.drop_duplicates("Team", keep="first")
employees.drop_duplicates(["Senior Management", "Team"], keep="last").sort_values("Team")

employees["Gender"].nunique()
employees.nunique()

```

## Dataframes Data Extraction

```py

bond = pd.read_csv("jamesbond.csv")
bond.set_index("Film", inplace=True)
bond.reset_index(inplace=True)

bond = pd.read_csv("jamesbond.csv")
bond.iloc[4:8]

bond.set_index("Film", inplace=True)
bond.loc[["Goldfinger", "Thunderball"]]

bond = pd.read_csv("jamesbond.csv", index_col="Film").sort_index()
bond.loc["GoldenEye":"Octopussy", ["Actor", "Bond Actor Salary", "Year"]] # Range of rows from GoldenEye to Octopussy
bond.iloc[:7, :3]

bond.loc["Diamonds Are Forever", "Actor"] = "Sir Sean Connery"
bond["Actor"] = bond["Actor"].replace("Sean Connery", "Sir Sean Connery")

bond = bond.rename(columns={ "Year": "Year of Release", "Box Office": "Revenue" })

bond.drop(columns=["Box Office", "Budget"]) # use inplace for modifying directly
bond.drop(index=["No Time to Die", "Casino Royale"])
bond.drop(index=["No Time to Die", "Casino Royale"], columns=["Box Office", "Budget"])

bond.sample(n=2, axis="columns")
bond.sample(n=2, axis="rows")


bond.sort_values("Box Office", ascending=False).head(4)
bond.nlargest(n=4, columns="Box Office")

actor_is_sean_connery = bond["Actor"] == "Sean Connery"
bond.where(actor_is_sean_connery)

```

## Text Data

```py

chicago = pd.read_csv("chicago.csv").dropna(how="all")
chicago["Employee Annual Salary"].describe()

chicago["Department"] = chicago["Department"].astype("category")
chicago["Position Title"].str.lower()
chicago["Position Title"].str.upper()
chicago["Position Title"].str.title()
chicago["Position Title"].str.len()
chicago["Position Title"].str.title().str.len()
chicago["Position Title"].str.strip()
chicago["Position Title"].str.lstrip()
chicago["Position Title"].str.rstrip()


chicago["Department"].str.replace("MGMNT", "MANAGEMENT").str.title()

water_workers = chicago["Position Title"].str.lower().str.contains("water")
chicago[water_workers]

ends_with_iv = chicago["Position Title"].str.lower().str.endswith("iv")
chicago[ends_with_iv]

chicago = pd.read_csv("chicago.csv", index_col="Name").dropna(how="all").sort_index()
chicago["Department"] = chicago["Department"].astype("category")
chicago.index = chicago.index.str.strip().str.title()

chicago.columns = chicago.columns.str.upper()


chicago = pd.read_csv("chicago.csv").dropna(how="all")
chicago["Department"] = chicago["Department"].astype("category")

chicago["Position Title"].str.split(" ").str.get(0).value_counts()
chicago["Name"].str.title().str.split(", ").str.get(1).str.strip().str.split(" ").str.get(0).value_counts()


chicago[["Last Name", "First Name"]] = chicago["Name"].str.split(",", expand=True)

```

## MultiIndex

```py 
bigmac = pd.read_csv("bigmac.csv", parse_dates= ["Date"], date_format="%Y-%m-%d")

bigmac = pd.read_csv("bigmac.csv", parse_dates= ["Date"], date_format="%Y-%m-%d", index_col=["Date", "Country"]).sort_index()
bigmac.index.names

bigmac.index.get_level_values("Date")
bigmac.index.get_level_values(0)
bigmac.index.get_level_values(1)
bigmac.index.set_names(names="Time", level=0)
bigmac.index = bigmac.index.set_names(names=["Time", "Location"])


bigmac = pd.read_csv("bigmac.csv", parse_dates=["Date"], date_format="%Y-%m-%d", index_col=["Date", "Country"])
bigmac.sort_index(ascending=[True, False])


bigmac.iloc[0]
bigmac.loc["2000-04-01"]
bigmac.loc[("2000-04-01", "Canada")]

start = ("2000-04-01", "Hungary")
end = ("2000-04-01", "Poland")
bigmac.loc[start:end]
bigmac.loc[("2012-01-01", "Brazil"): ("2013-07-01", "Turkey"), "Price in US Dollars"]
bigmac.loc[start:end].transpose() # creates a multiindex for the columns



world = pd.read_csv("worldstats.csv", index_col=["year", "country"]).sort_index(ascending=[True, True])

world.stack().to_frame() # The `stack` method moves the column index to the row index.

world.unstack()

world.unstack().unstack().head()



sales = pd.read_csv("salesmen.csv", parse_dates=["Date"])
pivoted = sales.pivot(index = "Date", columns="Salesman", values = "Revenue")

melted_data = quarters.melt(id_vars="Salesman", var_name="Quarter", value_name = "Revenue")
re_pivoted = melted_data.pivot(index="Salesman", columns="Quarter", values = "Revenue")

foods = pd.read_csv("foods.csv")
foods.pivot_table(values="Spend", index="Gender")

foods.pivot_table(values="Spend", index="City", aggfunc="sum")
foods.pivot_table(values="Spend", index="Item", columns=["Gender", "City"], aggfunc="sum")

```


## GroupBy

```py

fortune = pd.read_csv("fortune1000.csv", index_col="Rank")
fortune.groupby("Sector").head() # groupby gives a collection of dataframes

grouped_sector = fortune.groupby('Sector')
for sector, group_data in grouped_sector:
    print(f"Sector: {sector}")
    print(group_data.head())

grouped_sector.size() # size of each df in the collection

sectors = fortune.groupby("Sector")
sectors["Revenue"].get_group("Energy").sum()
sectors["Profits"].max()
sectors[["Revenue", "Profits"]].sum()


fortune = pd.read_csv("fortune1000.csv", index_col="Rank")
sectors = fortune.groupby(["Sector", "Industry"])
for (sector, industry), group_data in fortune.groupby(["Sector", "Industry"]):
    print(f"Sector: {sector}, Industry: {industry}")
    print(group_data.head(1))

sectors["Revenue"].sum().head(20)

fortune = pd.read_csv("fortune1000.csv", index_col="Rank")
sectors = fortune.groupby("Sector")
sectors.agg({"Revenue" : "sum", "Profits" : "max"})

def top_two_companies_by_employee_count(sector):
    return sector.nlargest(2, "Employees")
sectors.apply(top_two_companies_by_employee_count)

sectors.apply(top_two_companies_by_employee_count).groupby("Industry")



```