# Sublime Stata Enhanced

* Version 2.2.1
* Date: August 2, 2016

This package basic support for Stata (11–14, Windows and OS X) and comes with:

* Language definition for `.do` and `.ado` files 
* Commands for sending individual lines or selections to Stata (available via the command palette and with keyboard shortcuts):
	* (*OS X*) Send current line or selection to Stata: `super+enter`
	* (*Windows*) Send current line or selection to Stata: `ctrl+enter`
* A build system for Stata files

## Background

This is a modified version of [Steve Harris's Stata package](https://github.com/docsteveharris/stata). Because of scripting limitations in Stata < 12, his version relied on creating temporary `.do` files to pass commands to Stata. Stata 13 added fancy new AppleScript commands (specifically `DoCommand` and `DoCommandAsync`) that allow for scripted commands and eliminate the need for temporary files. Because of that, this package is far simpler than other Sublime Text packages.

For compatability with previous versions of Stata, however, I have included commands that create temporary files, as in the original Stata package. As such, this package works with Stata 11 and above on both OS X and Windows.


## Installation

There are two ways to install this package:

1. Search for "Stata Enhanced" on [Package Control](https://sublime.wbond.net/)
2. Copy the entire plugin folder to `~/Library/Application Support/Sublime Text 2/Packages` or `~/Library/Application Support/Sublime Text 3/Packages`


## Configuration options

### OS X

* (**Stata 11 and 12 only**) This package sends selected code to a temporary file and then opens that file in Stata via Finder. In order for it to work correctly on your system, you must ensure two things are true:
	1. `.do` files must be set to open in Stata by default in Finder (right click on a `.do` file > "Get Info" > "Open with" > "Change all…" > Select Stata. 
	2. `.do` files opened in Stata need to be run, not edited. Change this in Preferences > Do-file Editor > Advanced > Edit do-files opened from the Finder in Do-file Editor (uncheck this)

By default, when sending code to Stata on OS X, Sublime Text will maintain focus so you can continue to edit, following the pattern of RStudio, which sends code to the R console from the script editor without changing focus away from the editor. If you prefer for Stata to take focus after sending lines or selections, set the `switch_focus_to_stata` to `true` in `Stata Enhanced (OS X).sublime-settings`.

### Windows

* (**All versions of Stata**) Set the full path of your Stata installation (with slashes reversed) in `Stata Enhanced (Windows).sublime-settings` (default is `"C:/Program Files (x86)/Stata13/StataSE-64.exe"`)
* This package sends selected code to a temporary file and then opens that file in Stata. In order for it to work correctly on your system, you must ensure that `.do` files opened in Stata are run, not edited. Change this in Do-file Editor > Edit > Preferences > Advanced > Edit do-files opened from Windows instead of executing them (uncheck this)


## Roadmap and wish list

* Stata 13 for Windows [has support for Automation APIs](http://www.stata.com/automation/). It would be cool to use those instead of temporary files (like how the OS X version of the plugin uses temporary files for Stata 11–12, but the API for 13).
