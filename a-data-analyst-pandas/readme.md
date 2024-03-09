## PANDAS Complete

* In this, we will cover all aspects of Pandas df.

### Series

```py
ice_cream = ["Chocolate", "Vanilla", "Strawberry", "Rum Raisin"]
pd.Series(ice_cream)

```

```py
sushi = {
    "Salmon": "Orange",
    "Tuna": "Red",
    "Eel": "Brown"
}

pd.Series(sushi)
```


```py
prices.sum()
prices.mean()
prices.std()
prices.product()

```


```py
adjectives = pd.Series(["Smart", "Handsome", "Charming", "Brilliant", "Humble", "Smart"])
adjectives.unique()
adjectives.value_counts()
adjectives.size
adjectives.values
adjectives.index

```



```py
fruits = ["Apple", "Orange", "Plum", "Grape", "Blueberry", "Watermelon"]
weekdays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Monday"]

pd.Series(fruits, weekdays) # data , index
pd.Series(data=fruits, index=weekdays)
```



```py
pokemon = pd.read_csv("./pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon
google.head()
google.tail()
```



```py
pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")
sorted(pokemon, reverse=True) # gives a list
dict(pokemon)
print(max(google))
print(min(google))

```



```py
pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")

pokemon.head()
"Bulbasaur" in pokemon.values


```



```py
pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")

google.head()
pokemon.sort_values(ascending=False)
pokemon.sort_index(ascending=False)


```



```py
pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon.head()
pokemon.iloc[10]
pokemon.iloc[700:1010]

pokemon = pd.read_csv("pokemon.csv", index_col="Name").squeeze("columns")
pokemon.head()
pokemon.loc[["Charizard", "Jolteon", "Meowth"]]
pokemon.get(["Moltres", "Digimon"], "One of the values in the list was not found")

```



```py
pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon.head()

pokemon.iloc[[1, 2, 4]] = ["Firemon", "Flamemon", "Blazemon"]

```



```py
google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")
google.head()

google.count()
google.sum()
google.product()
pd.Series([1, 2, 3, 4]).product()
google.mean()
google.std()
google.max()
google.min()
google.median()
google.mode()
pd.Series([1, 2, 2, 2, 3]).mode()

google.describe()

```



```py
google = pd.read_csv("google_stock_price.csv", usecols=["Price"]).squeeze("columns")
google.head()

google + 2

```



```py
pokemon = pd.read_csv("pokemon.csv", usecols=["Name"]).squeeze("columns")
pokemon.head()
pokemon.apply(lambda x: x + "_add")
```




```py
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

### Dataframes

```py
nba = pd.read_csv("nba.csv")
nba.head(3)
nba.index
nba.values[0]
for index, row in nba.iterrows():
    print(index, row)

```

```py
nba.columns
nba.axes
```

```py


```

```py


```

```py


```

```py


```

```py


```

```py


```

```py


```

```py


```

```py


```

```py


```