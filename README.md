# Synology-NodeJS-API
A NodeJS API to communicate with your Synology NAS

You can :
- Login and logout to your Synology NAS
- Communicate with DownloadStation application (go to wiki for more informations)

Installation
```
npm install synology-node-api --save
```

Create your Synology Object
```javascript
const Syno = require('synology-node-api');
var syno = new Syno(
    protocol = "HTTPS",
    address = "192.168.0.0",
    port = "5000",
    username = "admin",
    password = "password",
    debug = true
);
```

Now, you can get all tasks from your Synology NAS like that
```javascript
syno.Auth.Connect().then(function(value) {
    console.log("Your are connected!");
    syno.DS.getTasks().then(function(value) {
        console.log("Success : " + value.Success)

        //Get your tasks
        for(var task in value.Tasks){
            console.log(value.Tasks[task].id)
        }
    }, function(reason) {
        console.log("Error : " + reason.Message)
    })
}, function(reason) {
    console.log("Error : " + reason.Message);
});
```

After doing your business, logout :)
```javascript
data.Auth.Logout().then(function(data){
    console.log("You're log out")
  },function(reason){
    console.log("You're not log out")  
  }
);
```

For documentation go to https://github.com/LionelPaulus/Synology-NodeJS-API/wiki
