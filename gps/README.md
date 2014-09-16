# GPS
This project is to enable GPS, and keep it on, even when switching apps, 
while Waze is running. The reason I created this profile was to prevent
Tasker from disabling GPS when Waze was no longer in the foreground. This
would occur when using an application context as the profile trigger.
## Dependencies
* [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) 4.4u3
* [Secure Settings](https://play.google.com/store/apps/details?id=com.intangibleobject.securesettings.plugin) 1.3.4
* [BusyBox](https://play.google.com/store/apps/details?id=stericson.busybox) 15

### Project Structure
#### Profiles
* Waze - Loop

  Responsible for triggering on app start and starting the check-waze loop
* Waze - GPS

  Toggles GPS depending on feedback from the loop

#### Tasks
* check-waze

  Uses Secure Settings to run 'pgrep waze' returning exit code 0 if Waze
  is running, and 1 if it isn't

* toggle-gps

  Uses Secure Settings to simply toggle GPS depending on the exit code

#### Variables
* %V_wait

  Adjusts the wait time in minutes for each loop iteration (default: 5)
* %V_waze

  Contains the exit code from check-waze

### TODO
I'm working on a version that does not require BusyBox for users that don't
have/want root access.

