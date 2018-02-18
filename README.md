# pythonista-scripts
Useful scripts to be run in Pythonista for iOS.  Kudos to [@cclauss](https://github.com/cclauss) for line by line code cleanup and helpful comments on improving many of these scripts.

- **/bible/BibleVerses.py** - This Pythonista script will retrieve any bible verse or verses and copy them to the clipboard or 1Writer, Editorial, or Drafts via a url. The script allows you to select between 10 different English language bible versions for scripture. The default version setting is the New American Standard.  The script uses the [getBible.net](https://getbible.net/api) api as the query source for scripture. More info is available in the script comments.  The script can be initialized stand alone from Pythonista or from a url action in 1Writer, Editorial, or Drafts.  If run stand alone, the script will copy the verse(s) returned from the query to the clipboard and print them to the console. You can then copy the verses to any application you wish using the clipboard.  If the script is called from one of the 3 text editors mentioned above via a url, the scripture will be appended to the calling editor's open doc.  Inspiration for this script came from [@pfcbenjamin](https://sweetnessoffreedom.wordpress.com/projects/) and his script [BibleDraft.py](https://gist.github.com/pfcbenjamin/423b27d4a56635220be9).

- **CreateHeaders.py** - Script automates the process of adding or editing header code comments to a new or existing script.  This script was originally written as a template but is now called from the wrench menu in Pythonista.  You can add a set of header comments to a script or edit existing comments in a script by loading the script in the editor and calling this script from the wrench menu.  A form dialog is used to edit the comments.  Contributors include @lukaskollmer who wrote the original template [script](https://github.com/lukaskollmer/pythonista-scripts/blob/master/Templates/New%20Script%20with%20info%20header.py), and @ccc who provided code cleanup and added a function to create a dictionary of fields in the original script.  Inspiration also came from [this](https://forum.omz-software.com/topic/3329/share-code-file-template-to-automatically-add-an-header-comment-block) thread in the omz-software forum.

- **DateTimePicker.py** - Script allows the selection of any date, time, or combination therein using the Datepicker ui view.  This works well for logging entries in a diary or journal. The script can be run stand alone or it can be called from apps such as 1Writer and Drafts using their respective URL schemes (see comments in script for more info and requirements). A seperate pyui file is no longer required, as it's ui code was added to this script.

- **GetPyuiAttribs.py** - This Pythonista script allows the selection of a pyui file from any folder in the Pythonista documents directory. Once selected, the script mines the attributes of the view and subview objects in the file and converts them to text that can be modified slightly and entered as code into the associated .py file. This makes for an easier coding transistion for scripts that use a pyui file to be merged into a single .py file. The attributes are displayed in the console and written to the clipboard for easy copying to the .py file. I prefer incorportating the ui code into the .py file, rather than maintaining 2 files, and this script makes this more convenient. Thanks goes to @nekotaroneko for his script, [GUI_Helper.py](https://github.com/nekotaroneko/GUI_Helper), which provided inspiration for this script. Many thanks to @omz as well for his script, [File Picker.py](https://gist.github.com/e3433ebba20c92b63111), which provided the excellent file-picker code used in this script and Gui_Helper.py. 

- **Search_TMDB.py** - A script that I find useful to quickly look up info on a movie title, TV series, or movie-tv people using the api at https://www.themoviedb.org.  The results of the search queries to the api are displayed in a ui TextView in Markdown format and can be exported to 1Writer, DayOne, Drafts, Editorial or the clipboard. The results can also be imported to these apps if this script is called via a url from the app itself. When exported to a Markdown capable editor the movie title & poster appear in hypertext with a direct link to the TMDB database if more info is desired. This script is capable of displayng the query results in a markdown TextView using [Markdown.py](https://github.com/mikaelho/pythonista-markdownview), a script that is placed in the site-packages folder, and called as a module in this script. The 2 image files, 'movie_camera.gif' and tmdb_logo.jpg have been added to this repo.  The image files are loaded into their respective ImageViews in the ui for this script.  They should be placed in the same directory as this script.  Additional requirements and information is provided in the code comments

- **PhotosToDropbox.py** - A script that lets you select multiple photos from the iPhone camera roll, resize & geo-tag them, and upload them to Dropbox where they are renamed and organized based on the date and time they were taken.  The cool part is that the script will preserve the metadata of the original photo if desired, using the [Pexif module](https://github.com/bennoleslie/pexif) to read the metadata from the original and write it back to the resized copy.  The Pexif module can be imported into Pythonista by simply copying pexif.py into the Pythonista 2.1 'site-packages' directory.  The script requires [DropboxLogin.py](https://gist.github.com/omz/4034526) to allow Pythonista login access to your Dropbox account. Follow the comments and links at the bottom of the linked Github page for information about upgrading the login script to be compliant with Dropbox API v2.0.  The script also requires Pythonista 2.1 or higher, as it makes use of the updated Photo module.

- **TimeClock.py** - Calculates the time elapsed in hours & minutes between two user selected times using the Date-Time Picker in the Pythonista ui. Ideal for calculating hours in shift work. Code includes time deductions for lunches if applicable.

- **/weather_anywhere/WeatherAnywhereFunctions.py** - This script was inspired by @cclauss' script '[weather_where_you_are.py](https://github.com/cclauss/weather_where_you_are)' and uses the [weather api](http://www.wunderground.com/weather/api) from www.wunderground.com.  The script is a vessel to store the functions that WeatherAnywhereScene.py uses to display it's information in a scene. In order to use the script you will need to aquire an api key from the wunderground website. The key is free if your usage is 500 or less server hits per day and provides a wealth of weather information. Lots of weather info is provided via the api, including forecast, humidity, pressure, temperature, precipitation amounts, wind speed, wind chill, percent of precipitation, moon cycles, and weather history. The info is in imperial units, but can easily be changed to metric via a flag in the script. The script makes use of a txt file, 'cities.txt', to be located in the same folder as the script, and 38 gif files that display weather types, located in the '/icons' subfolder of the script's folder. The script will download the icons if it doesn't find them.  The txt file can contain popular local, regional, national and international cities of your choosing, including their state, if national, or country, if international, and their zip links.  The file is easily editable with the Pythonista editor. The zip link is automatically added to the cities list when you choose to add a new city. I've included a sample cities.txt file in this repository. 

- **/weather_anywhere/cities.txt** - A sample txt file of cities for 'WeatherAnywhereScene.py'.

- **/weather_anywhere/WeatherAnywhere.pyui** - The pyui file that contains the objects for the front end menu for WeatherAnywhereScene.py.  The file needs to reside in the same directory as WeatherAnywhereFunctions.py, WeatherAnywhereScene.py, and cities.txt.  The objects include 2 buttons and a tableview that uses cities.txt as it's data source.  One button allows for viewing the current weather from your current location and the other allows you to add new cities to the cities.txt.  Cities can be deleted from the tableview and cities.txt via a swipe to left in the tableview cells.

- **/weather_anywhere/WeatherAnywhereScene.py** - I wanted to be able to add weather icons and have them scroll with the text, so a scene seemed to be the best answer. This script gives a comprehensive representation of the weather for the city you choose. It displays the current weather, weather for the next 24 hrs, weather for the next 7 days, and buttons on the title bar for viewing the weather on the web and weather alerts for the region if applicable.  The display is a scene inside a ui.view.  It is designed for an iPhone 4,5,6 or 6+ in portrait orientation running Pythonista v2.0 and adopts to the appropriate display size of the iPhone being used. The script uses the functions in 'WeatherAnywhereFunctions.py' to retrieve the necessary weather info displayed.  The script allows scrolling the scene by inertia.  A basic scrolling example was created by Dalorbi on the [pythonista forums](http://omz-forums.appspot.com/pythonista/post/4998190881308672). Ability for scrolling the scene with inertia was added by [hroe](https://gist.github.com/henryroe/6724117). This script needs to be placed in the same folder as WeatherAnywhereFunctions.py, to make use of some of it's functions. The script also uses the weather icons stored in a subfolder '/icons' off the script folder.

- **SendGpsData.py** -  A Pythonista script for texting your GPS location & current weather using clipboard, email, or SMS messaging. Requires [Launch Center Pro](https://itunes.apple.com/us/app/launch-center-pro/id532016360?mt=8) to provide ability to email and SMS msg the text, and an api key from [here](http://www.wunderground.com/weather/api) to get weather data. The script can be run stand alone from Pythonista or be called from 1Writer, Editorial, or Drafts via a URL, in which case the text will be appended to the caller's open doc for use in journaling, logs, etc. Github contributors to this script are noted in script's comments.

- **ListToFantastical2.py** - This script parses BOTH reminders and events from comma seperated text passed from URL's in LCP, 1Writer, or Drafts and posts them in Fantastical2 and returns you to the caller app. Thanks to Fantastical's natural language parsing, your 'tasks' can be reminders or events.  The reminders must start with a 'Task', 'Todo', 'Reminder', or 'Remind me' pre-text followed by the todo itself.  Events don't need the pre-text. For more on this see [here](http://www.geekswithjuniors.com/note/5-awesome-things-from-fantastical-2-that-can-improve-your-wo.html)
and [here](http://plobo.net/recursive-actions-with-launchcenterpro-and-pythonista) for 2 well documented intros to the proper syntax. Inspiration came from [this](https://gist.github.com/pslobo/25af95742e1480210e2e) script.  Thanks goes to @pslobo for his Github contribution. 
