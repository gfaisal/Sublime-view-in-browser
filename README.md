Sublime - View in browser

Sublime Text - View In Browser

View In Browser is a Sublime Text plugin that will open whatever is in your current view/tab. If the file current open is new and has not been saved a temporary file is created (in your default temp directory for your OS) with the extension of .htm and your browser will open it. However if the current open file is saved and has a name this plugin will open it in whatever you have set to handle its type.

By default the keystroke assigned to this plugin is CTRL + ALT + V.
Installation

Using the Sublime Text Package Control plugin (http://wbond.net/sublime_packages/package_control) press CTRL + SHIFT + P and find Package Control: Install Package and press Enter. Find this plugin in the list by name View In Browser.
Configuring Browsers

By default this plugin will open files in Firefox. You can configure it to open using another browser of your choice. To do this, choose Settings - User from Preferences > Package Settings > View In Browser.

The browser you wish to use to open files is set in the key named browser. The following is a list of browsers configured for use out of the box.

    Firefox - Mac OS, Linux, Windows
    Chrome - Mac OS, Linux, Windows
    Chrome64 - Windows
    Safari - Mac OS
    Internet Explorer - Windows
    Chromium - Linux

Other Browsers

View In Browser also provides key bindings to open your current view in browser other than your browser setting. Below is a listing of the keys and what browser open with those key bindings.

    CTRL + ALT + F - Firefox
    CTRL + ALT + C - Chrome
    CTRL + ALT + I - Internet Explorer
    CTRL + ALT + S - Safari

Like any other key binding in Sublime these can be changed. Below is an example of the key configuration. You can remap these in your User key bindings configuration file.

[
    { "keys": [ "ctrl+alt+v" ], "command": "view_in_browser" },
    { "keys": [ "ctrl+alt+f" ], "command": "view_in_browser", "args": { "browser": "firefox" } },
    { "keys": [ "ctrl+alt+c" ], "command": "view_in_browser", "args": { "browser": "chrome" } },
    { "keys": [ "ctrl+alt+i" ], "command": "view_in_browser", "args": { "browser": "iexplore" } },
    { "keys": [ "ctrl+alt+s" ], "command": "view_in_browser", "args": { "browser": "safari" } }
]

Windows Considerations

One of the things you may notice in the Windows configuration for chrome is a variable in the command path that looks like: %Local AppData%. This is a reference to your Windows installation's AppData folder in your user profile directory. There is a variable there because this value will differ for each user on your computer, and Chrome installs to your AppData folder.

Here is a list of supported variables:

    AppData - Your main application data folder for your profile (usually roaming)
    Personal - Your documents location
    Desktop - The path to your Desktop location (may be unreliable)
    Start Menu - The path to your Start Menu items location
    Local AppData - Your local application data folder for your profile
    My Video - Path to your videos location
    My Pictures - Path to your pictures location
    My Music - Path to your music location

Note that many of these are not terribly useful for determining browser location, unless you have decided to install Firefox in your My Music folder.
Configure to View on Local Server

The View In Browser plugin also supports the ability to view files in the context of a local server. So if you have a local Apache, Tomcat, or some other server application running you can configure this plugin to open your file prefixed with a URL.

To configure this the View In Browser plugin reads the configuration of your currently loaded project. You can edit a project file by opening the sublime-project file by choosing Project -> Edit Project. In your project file you will need to specify two things:

    baseUrl - The root URL to prefix files with
    basePath - The base path where your site/application lives

Here's how that looks.

{
    "folders":
    [
        {
            "path": "/home/<username>/code/python/my-cool-website"
        }
    ],
    "settings": {
        "sublime-view-in-browser": {
            "baseUrl": "http://localhost:8080",
            "basePath": "/home/<username>/code/python/my-cool-website"
        }
    }
}

Notice the key named settings which is a dictionary that contains another key named sublime-view-in-browser. This is where you will put your baseUrl and basePath settings.

Now when you activate View In Browser your file will open with the HTTP protocol instead of the FILE protocol.
