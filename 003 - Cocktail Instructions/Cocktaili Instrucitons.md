# Cocktail Making Instructions
```Python
# This was a basic program I made to practice interacting with APIs
# Here I use a free cocktail API (www.thecocktaildb.com)

import requests

userquery = input('Enter a drink>> ')
url = f'https://www.thecocktaildb.com/api/json/v1/1/search.php?s={userquery}'

response = requests.get(url)
result = response.json()['drinks']
instructions = result[0]['strInstructions']

print(instructions)
```