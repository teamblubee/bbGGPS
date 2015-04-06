bbGGPS

This is a [Google Play Game Services](https://developer.android.com/google/play-services/index.html) module for the [Godot game engine](http://www.godotengine.org/wp/), written by [blubee](http://blubee.me)

This module should be straigh forward to use.

###Implemented Abilities
####Login or Logout to Google Play Game Services
####Increment or Unlock achievements

[Setup](https://developers.google.com/games/services/android/quickstart) your app in the new Google Play Services developers console.




Download this project put the "GodotGooglePlayGameServices" inside your godot-src/modules foler. Then recompile your android export templates.

How To Compiling Android Export Templates

###Adding Your APP_ID 

Inside the GodotGooglePlayGameServices folder go into the androidmanifestchunk and add your app id ex: 

	<meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ [place app id here]" />


##Example Usage
In any script add this code

var ggps

	func _init():
		if(Globals.has_singleton("bbGGPS")):
			ggps = Globals.get_singleton("bbGGPS")
			ggps(get_instance_ID())

###Now You Can Call
	ggps.sign_in() //This will make sure your user is logged in.
**This will prompt the user to login to Google. You should make sure that the user is fully before calling any of the Google Play Game Services Functions**

In you GDScript file create a function called is_user_logged_in this will return true or false

	func is_user_logged_in(logged_in):
			if(logged_in):
				you can call the implemented Google Play Game Services Functions
			else:
				user isn't logged in, you can request for them to log in.
				
To get the **is_user_logged_in** you must call
	
	ggps.is_loggedIn()


##Function prototype
	init_GGPGS(int device_id)
	sign_in()
	is_logged_in() #this will call back to the GDScript "is_user_logged_in(boolean)" function
	increment_achy(String achievement_id, int increment_amount)
	unlock_achy(String achievement_id)
	show_achy_list()
