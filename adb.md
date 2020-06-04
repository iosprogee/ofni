### CLI
adb reboot bootloader
adb push gapps-lp-20150314.zip /storage/sdcard1/rom/
adb devices
adb status
adb tcpip 5555
adb kill-server
adb tcpip 5555

adb connect 192.168.1.108
adb reboot recovery
adb sideload pac_jflte-release-20150112.zip
fastboot flash recovery twrp-3.0.2-0-p3100.img


### SETUP USB DEBUGGING FOR ANDROID
 -SETTINGS > SYSTEM > ABOUT PHONE > TAP ON BUILD NUMBER (till developer option enabled)
 -SEARCH DEVELOPER > TAP DEVELOPER OPTION > ON 
 -SET USB DEBUGGING ON


### REMOTE DEBUGGING
 https://developers.google.com/web/tools/chrome-devtools/remote-debugging/
 https://developers.google.com/web/tools/chrome-devtools/remote-debugging/local-server

### COPY FILES
 adb devices
 adb shell
 adb shell ls sdcard
 adb shell ls sdcard/Movies
 adb push /Volumes/NO\ NAME/The.Spectacular.Now.2013.720p.mp4  sdcard/Movies/The.Spectacular.Now.mp4
 adb shell ls -sal sdcard/Movies