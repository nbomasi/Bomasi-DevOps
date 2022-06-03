# MEAN STACK DEPLOYMENT TO UBUNTU IN AWS

1. **Install NodeJs**

Command: _Install NodeJs ; sudo apt update ; sudo apt upgrade ; sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates ; curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - ; sudo apt install -y nodejs_

2. Installing MongoDB

Note: I used the information in the follow link to install mongoDB, since the guide we had was for EC2 18.04, it was throwing error "package Mongodb has no installation candidate. Link: https://www.cloudbooklet.com/how-to-install-mongodb-on-ubuntu-22-04/

Other commands: sudo npm install body-parser ; mkdir Books && cd Books ; npm init ; vi server.js ;

``` var express = require('express');
var bodyParser = require('body-parser');
var app = express();
app.use(express.static(__dirname + '/public'));
app.use(bodyParser.json());
require('./apps/routes')(app);
app.set('port', 3300);
app.listen(app.get('port'), function() {
    console.log('Server up: http://localhost:' + app.get('port'));
});
```

![MongoDB install](https://user-images.githubusercontent.com/65962095/171927429-499088cc-fa12-481d-8436-5122625b7acf.PNG)


