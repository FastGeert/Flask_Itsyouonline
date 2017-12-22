# Flask-Itsyouonline

Flask-Itsyouonline is a plugin for Flask microframework implements the OAuth flow of itsyou.online 

## Configurations

- CLIENT_ID: itsyou.online client id.
- CLIENT_SECRET: client secret.
- REDIRECT_URI: your callback endpoint
- AUTH_ENDPOINT: from where to start the oauth flow
- ON_COMPLETE_ENDPOINT: make a post request to the end point with user informatin.


## Example application

```python
import flask
from flask import Flask, 
from flask_itsyouonline import configure, authenticated

app = flask.Flask(__name__)

configure(app, 'Itsyou.Online organization', 'Itsyou.Online client secret', 
          "http://127.0.0.1/callback", '/callback', 'user:publickey:ssh')

@app.route("/", methods=["GET"])
@authenticated
def home():
    return "Hello %s" % app.config['iyo_user_info']['username']

if __name__ == "__main__":

    app.run(debug=True, port=4000)

```

## Contributions
PRs are very welcome. 
