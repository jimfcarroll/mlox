# mlox - the elder scrolls Mod Load Order eXpert
mlox is a tool for analyzing and sorting your Morrowind plugin load order.

Version: 0.62

Copyright 2014-2017 [MIT License](License.txt)
* John Moonsugar
* Dragon32
* Arthur Moore

mlox is a mini "expert system" for advising you on your set of plugins.
Use mlox to check for plugin dependencies and conflicts, and to sort your plugins into an optimal load order.

# Obligatory Screen Shot

![mlox interface](https://sourceforge.net/p/mlox/screenshot/mlox_screen.png)

# About
mlox is designed to help people manage large collections of plugins for the popular Elder Scrolls games from Bethesda Softworks.
The program sorts plugins based on a very simple set of ordering rules that comprise a partial order over the set of plugins using a standard topological sort.
It also provides advice on plugin conflicts, missing pre-requisites, and general information of interest based on the user's particular set of plugins.

# Features
* optimally reorders your load order
* warns about missing pre-requisites
* warns about plugin conflicts
* prints notes for things you might want to know about a mod, but were too lazy to read the Readme, or things discussed in forum posts you may have missed.
* Customizable via a rules file. Just create an `mlox_user.txt` in your mlox directory, and start adding your own rules.
* runs on Windows or Linux
* can check someone else's load list from a file:
        mlox.py -wf Morrowind.ini
        mlox.py -wf someones_load_order_posting.txt
or just paste the list of plugins into the Active plugins pane of the GUI. (mlox understands output of Wrye Mash and Reorder Mods++)

**Note**: mlox does not tell you if you have missing Meshes or Textures, it is only a load order tool, and does not report problems with resources!

# Downloading
The latest stable version of mlox can be found [here](https://github.com/mlox/mlox/releases/), and the source code can be found on [github][github].

Unpack the mlox application archive in your Morrowind directory. You should see an mlox directory in the same directory as Morrowind.exe.

If Mlox does not run you may need the [Microsoft Visual C++ 2008 Redistributable Package (vcredist_x86.exe)](http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&displaylang=en).

Mlox versions 0.59 and higher automatically download the latest rules file.
Please do not edit this file!
Users can instead put their own additions in `mlox_user.txt`

# Running
Windows users can run the program by clicking on `mlox.exe`.  Linux users can either click on `mlox.py` or type `python mlox.py` on a command line.

**WARNING**:  Mlox requires that it's directory is writable.  Otherwise database updates will fail.

mlox.py has 2 modes, GUI and command line. When executed with no command line switches it starts in GUI mode.
For information on specific commands use `mlox -h`.

**Note**: On Windows Visa and later, if you installed Morrowind in the default location "C:\Program Files\\...", you may need to turn off UAC to get mlox to recognize your activated plugins in Morrowind.ini.


## Running mlox from source

Mlox is written using Python3, using a PyQt5 graphial interface.
As such, both Python3 and PyQt5 are required.
Several other small libraries are also needed for full functionality.

* Python3 Download link:  https://www.python.org/downloads/
* Once Python 3 is installed, run `pip3 install PyQt5 libarchive-c appdirs`
* Run mlox by typing `python3 mlox.py`

# Other Recommended Software
It is STRONGLY RECOMMENDED that you install Hrnchamd's MCP ["Morrowind Code Patch!"](http://www.nexusmods.com/morrowind/mods/19510)
The MCP makes it safer to change your load order in an existing savegame, amongst many other wonderful fixes it does.

You are also encouraged to use [Wrye Mash](http://wryemusings.com/Wrye%20Mash.html) to manage your plugins.

# Customizing your Load Order

mlox allows you to customize your load order by adding your own sorting rules to a file called `mlox_user.txt`, in your mlox directory.
Then, all you need to do to get your load order re-sorted correctly is press the update button in mlox.

You can add any of mlox's rules to `mlox_user.txt`, but for people that want to customize their load order, the **`[Order]`** rule is probably all that is needed.
Here is a simple example:

Let's say you want to make sure that mlox always puts plugin "Foo.esp" before "Bar.esp". Just create a simple text file called "mlox_user.txt" in your mlox directory (using Notepad or whatever) containing the following:

    [Order]
    Foo.esp
    Bar.esp

From now on, when you press the mlox update button, mlox will make sure that this is the order for those two plugins. Note that the **`[Order]`** rules in mlox_user.txt (your personal rules) take precedence over the rules in mlox_base.txt.

You should also be aware that the **`[Order]`** rule only specifies relative order, so in the example above, it does not mean that Foo.esp must come _immediately_ before Bar.esp, only that Foo.esp must load _somewhere_ before Bar.esp.

# Documentation
The complete documentation for mlox can be found in the Doucmentation directory.

  * [Mlox Usage Guide](Documentation/Using mlox.md) provides a guide to getting started and introduction to usage. **Important Reading!**
  * [Editing Guidelines](Documentation/Editing Guidelines.md) explains the basics of mlox rules, and how they should be used.
  * [Rules Guildelines](Documentation/Rule Guidelines.md) explains the syntax of the mlox rules, and how to write them yourself if you want to customize mlox.
  * [mlox_guts.txt](Documentation/mlox_guts.txt) describes mlox's inner workings and how it does its job.


# Support
If you run into a problem with mlox, please open a support ticket [here][issues].

* Usually when mlox fails it will pop up a window describing the error, please report the contents of this window when reporting a problem.
* If mlox runs but gives unexpected results, please right-click in the "Active Plugins" pane on the left side and choose "Debug" from the popup menu.  Attaching this to the support ticket will help solve the problem.
* Please report all Windows usability problems, as several of the Mlox developers do not use Windows.
* If the mlox GUI disappears upon startup, and you are running from source, you may be using an incompatible version of wxPython.  Please use the version provided [here][wxpython]

# Contribute to the mlox rule-base
mlox can only succeed if you share your knowledge about plugin load order, conflicts, and pre-requisites!
Your contributions will help other players that follow in your footsteps.

You can help contribute to mlox by sharing information about a mod [here][issues].

The mlox project welcomes all submissions of information for inclusion in the mlox rule-base, but the more information you can give when you make the submission, the more likely your submission will be used. Information that lacks detail or is of low quality will be given the lowest priority. Which means it may only get investigate for inclusion if time permits.

So, please try to include:

  * the Full name of the mod(s), the version number, and the author.
    * Good: '"Herbalism" 1.3 by Balor'
    * Bad: 'herbalism mod' (which one? there are a number of them!)
  * a link to the mod, if you have one.
  * the best explanation you can give
    * If it's a conflict, please explain what the actual conflict is.
    * If it's a load order, it would be great to say what the order affects.

## Become a rule-base Editor
If you have solid knowledge of load order issues, and you'd like to be able to contribute to the rule-base by editing it directly, please submit a pull request on [github][github].

Editors of the rule-base should read the [Editing Guidelines](Documentation/Editing Guidelines.md), which explain how the editing process works.

Glory awaits you my friend.

## Note to mod Authors
It is our hope that the users of your mod will benefit from using mlox, and also that maybe mlox will help reduce mod conflicts, and support questions for your mod due to misconfiguration.
This is a grand goal, and there are some things we can do together to see it happen.

The first thing is versioning of your mod.
If mlox can tell what version of your mod the user is using, it can give more accurate advice.
mlox can get the version of a plugin from its header description field (preferred), or from the plugin filename.

So, if the filename stays the same from version to version, then if the description field of the plugin contains a version string on a line by itself mlox will be able to use it.
Wrye Mash can report that version too, so it's just a generally useful thing to have in the description

> Example version string:
>
> Version: 0.57

mlox can also tell the version from the filename.

> Example verioned file name:
>
> Plugin_V1.0.esp

The next thing is teaching mlox about your mod.
Please see the section about [adding rules to mlox](#Contribute to the mlox rule-base) for how to submit a rule.
The more mlox knows, the more useful it is, and people will have fewer load order problems.


[wxpython]: http://downloads.sourceforge.net/wxpython/wxPython2.8-win32-ansi-2.8.7.1-py25.exe
[github]: https://github.com/mlox/mlox
[issues]: https://github.com/mlox/mlox/issues
