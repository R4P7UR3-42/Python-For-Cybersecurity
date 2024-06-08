# Cocktail Making Instructions
```Python
import requests

userquery = input('Enter a drink>> ')
url = f'https://www.thecocktaildb.com/api/json/v1/1/search.php?s={userquery}'

response = requests.get(url)
result = response.json()['drinks']
instructions = result[0]['strInstructions']

print(instructions)
```