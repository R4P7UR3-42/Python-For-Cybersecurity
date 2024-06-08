# Script to Make Web Requests and Manipulate Headers
```Python
# This program was used to practice sending web requests and manipulating certain headers for more a more desireable outcome
import requests
from requests.exceptions import *
from gtoken import Get_Token

# Variables

token = Get_Token()
user = 'user_name'
auth_header = (user, token)
base_url = 'https://api.github.com/'
header = {
    'Authorization': 'token ' + token
}

# Actionable code
res = requests.get(f'{base_url}user', headers=header)
print(res.json())
```