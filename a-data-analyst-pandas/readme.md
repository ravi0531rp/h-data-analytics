## PANDAS Complete

* In this, we will cover all aspects of Pandas df.

### Series

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