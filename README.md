# Node Linux Sched Service
A simple scheduling service made using node js.


## What This Can Do
This node app includes:
* Service that watches your schedule XML files and bring up notifications
and run commands to remind you of your scheduled tasks
* [FRIDGE] A tool for creating, editing, and merging the Schedule XML files
* [FRIDGE] A tool for creating a beautiful 


### Notification Service
You only need to run this once to setup the service.

```sh
npm run build-service
```

And poof! The server is now running! To check:

```sh
sudo systemctl status node-linux-sched.service
```
To know more about systemctl and its usage, see the its manual by [going here](http://www.dsm.fordham.edu/cgi-bin/man-cgi.pl?topic=systemctl) or typing `man systemctl` on your terminal.

### Schedule XML Files
Schedules are stored as XML file on the `/schedules` directory inside this project. See `/schedules/README.md` to know more about the expected formatting of the XML files.