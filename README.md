# OAUTH-1
First Attempt

var express = require('express'),
    body parser = require('body parser'),
    oauth server = require('oauth2-server');
    
var app = express();

app.use(bodyParser.urlencoded({ extended:  true }));

app.use(bodyParser.json());

app.oauth = oauthserver({
  model: {},
  grants: ['password'],
  debug: true
});

app.all('/oauth/token', app.oauth.grant());

app.get('/', app.oauth.authorise(), function (req, res) {
  res.send('Secret area');
});

app.use(app.oauth.errorhandler());

app.listen(3000);
