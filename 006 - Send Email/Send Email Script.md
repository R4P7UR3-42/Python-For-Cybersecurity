# Script to Send an Email
```Python
# Send an email with content from an API
# Impliment logging
# Make sure email credentials are not in the script (external json file)
# PROPERLY handle all exceptions specifically
import requests
import json
import smtplib
import logging

URL = 'https://v2.jokeapi.dev/joke/Dark'

with open('creds.json', 'r') as f:
    creds = json.load(f)
    f.close()

LOGFILE = 'email_send.log'
EMAIL = creds['email']
PASSWORD = creds['password']
RECIPIENT = EMAIL

logging.basicConfig(filemode='a', filename=LOGFILE, level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')

def send_email(joke):

    try:

        s = smtplib.SMTP('smtp.gmail.com', 587) #Specific to GMail

        s.starttls()

    except smtplib.SMTPConnectError:

        logging.error("Failed to connect to SMTP server")

        exit()

    try:

        s.login(EMAIL, PASSWORD)

    except smtplib.SMTPAuthenticationError:

        logging.error("Authentication Failure.")

        exit()

    try:

        s.sendmail(EMAIL, RECIPIENT, f'\n{joke}')

    except smtplib.SMTPException:

        logging.error("Error, failed to send mail.")

        exit()

    s.quit()

  

def get_joke_content():

    response = requests.get(URL)

    result = response.json()

    if result['error']:

        logging.error('Something went wrong with the request to the API.')

        return None

    if result['type'] == 'twopart':

        # extract a setup and delivery

        setup = result['setup']

        delivery = result['delivery']

        return(f'Setup: {setup}\n Delivery: {delivery}')

    else:

        # extract a single joke

        joke = result['joke']

        return(f'Joke: {joke}')

# start of actual program execution

joke = get_joke_content()

logging.info('Joke retrieved successfully.')

if joke is not None:

    send_email(joke)

    logging.info('Email successfully sent.')
```