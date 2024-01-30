# QLC_config




## Fixtures 
Go into C:\Users\USERNAME\QLC+\Fixtures\ by default, but I think you can just import them from this directory 


## Styles 
Location C:\Users\USERNAME\QLC+
The default one is ok. It's a bit bright to run a show with. 
The custom one is built off the RJones one I think. It is better to run a show (and matches the web one in colours) but results in the loss of some menu tabs adjusting fixtures or something like that - it needs more work. 


## Shows / projects 
The one from shibari sydney is here .  it has several things that should be improved 


- [ ] single colour for fill / uplighting 
- [ ] clean up all functions / make sure they work 
- [ ] simplify the tap 
- [ ] add a physical midi controller


## Creating shortcuts 
- Create the shortcut 
- change the target to `C:\Windows\System32\cmd.exe /c "SET QT_AUTO_SCREEN_SCALE_FACTOR=1 && START /D ^"C:\QLC+^" qlcplus.exe -w -o C:\Users\<PROJECT_PATH>"`