---
layout: post
title: "Text Editors"
excerpt: "One second saved per minute = 1.666% better living"
tags: [apple, mac, setup]
image:
# feature: pic RichTextEditorToolBar 1900x500.jpg
  feature: https://cloud.githubusercontent.com/assets/300046/14622140/227572b0-0585-11e6-8d8c-55c1faa4fd68.jpg
  credit: MH Education
  creditlink: http://highered.mheducation.com/sites/0000065899/student_view0/question_editor/rich_text_editor_toolbar.html
comments: true
---
<i>{{ page.excerpt }}</i>
<hr />

{% include _toc.html %}

This is a random collection of notes on text editors for the Mac.

There is not shortage to the number of programs available to edit code.

Built-in OSX:

   * <a href="#vim">vim</a>
   * <a href="#pico">pico</a>
   * nano

Free:

   * <a href="#atom">Atom</a> from GitHub (free)
   * <a href="#Code">Code</a> from Microsoft (free)
   * <a target="_blank" href="http://brackets.io/">
   http://brackets.io - Adobe Brackets</a> is on Windows too
   * <a target="_blank" href="http://barebones.com/products/textwrangler/">
   http://barebones.com/products/textwrangler</a> is the
     little brother to BBEdit.
   * <a target="_blank" href="http://www.annedawson.net/Python_Editor_IDLE.htm">
   http://www.annedawson.net/Python_Editor_IDLE.htm">
   Python IDLE Editor</a>

   * mvim ? for Mac

Licensed nagware:

   * $89 <a href="#SublimeTextz">Sublime Text</a>
   * Texttastic
   * Byword 
   * There is no equivalent of Notepad++ on Windows

Free IDEs:

   * <a href="#Eclipse">Eclipse</a>
   * Aptana Studio
   * NetBeans
   * <a target="_blank" href="https://github.com/spyder-ide/spyder">Spyder</a> (for Python pyflakes and pylint code analysis)
   * Visual Studio Express from Microsoft

Licensed IDEs:

   * IntelliJ and WebStorm and PhpStorm from JetBrains
   * Visual Studio from Microsoft

<hr />

<a name="Features"></a>

## Features #

* Markdown display
* Code completion
* Pre-compile on the fly
* Static code scan on the fly
* Full project navigation
* Refactoring (renaming) support
* Debugging

<a name="vim"></a>

## Vim

To edit the file executed upon opening a command-line Terminal:

   <strong>vim ~/.bash_profile</strong>

To get out of VIM, type:

   <pre>
   :q to quit (short for :quit)
   :q! to quit without saving (short for :quit!)
   :wq to write and quit (think write and quit)
   :x to write and quit (shorter than :wq)
   :qa to quit all (short for :quitall)
   </pre>


<a name="pico"></a>

## pico

According to <a target="_blank" href="https://en.wikipedia.org/wiki/Pico_%28text_editor%29">
Wikipedia</a>, pico stands for "pine composer".

   ![pico menu 75](https://cloud.githubusercontent.com/assets/300046/15268678/21302782-19a4-11e6-9f8d-873c5a3073e4.jpg)

The ^ character means hold down the <strong>control</strong> key while you press the character.

<a id="SublimeTextz"></a>

## Sublime Text

Many tutorials make use of this tool.

There are two simultaneous production versions of Sublime Text: 2 and 3.

### Download and Install Sublime Text

* <a target="_blank" href="https://www.sublimetext.com/3">https://www.sublimetext.com/3</a>
   is recommended even though it's labeled "beta" because desirable packages are being written for it.

* <a target="_blank" href="https://www.sublimetext.com/2">https://www.sublimetext.com/2</a>

Expanded explanations for various platforms:

* http://docs.sublimetext.info/en/latest/getting_started/install.html

* On Linux: https://github.com/TCattd/sublime-text-linux-installer

### Configure for command-line invocation

To use the Sublime Text text editor from the command line,
make a symlink to subl.

0. If you don't have a folder <strong>/usr/local/bin/</strong>, create it.

   <pre>
   mkdir /usr/local/bin/
   ls
   </pre>

0. Assuming you've placed Sublime Text in the Applications folder:

   <pre><strong>
   sudo ln -s "/Applications/Sublime Text 3.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl
   </strong></pre>

0. To use Sublime Text as the editor for many commands that prompt for input,
   set your EDITOR environment variable:

   <pre><strong>
   export EDITOR='subl -w'
   </strong></pre>

   Specifying -w causes the subl command to not exit until the file is closed.

0. Use the Sublime text editor to open the profile file:

   <pre><strong>subl ~/.bash_profile</strong></pre>


### Install Package Control

One advantage of Sublime Text is its plug-ins.

0. Switch to an internet browser to visit
   <a target="_blank" href="https://sublime.wbond.net/">Package Control home page</a>.
0. Click Browse at the upper right for the most popular:

   * Emmet for keyboard shortcuts
   * SideBarEnhancements
   * SublimeLinter to find typos
   * Theme - Soda to look better
   * SFTP to transfer files from within the editor UI.

0. Click the <strong>Popular</strong> heading for a list with more detail.

0. Visit <a target="_blank" href="https://sublime.wbond.net/">Package Control home page</a>.

0. Open SublimeText 3.
0. If not already installed, see <a target="_blank" href="https://packagecontrol.io/installation#st3">
   https://packagecontrol.io/installation#st3</a>
0. Select your version of Sublime you have open.
0. Double-click on the command text to select it.
0. Press Ctrl+C to copy the command into the operating system's invisible clipboard.
0. Switch back to SublimeText (press Command+Tab).

0. Bring up Sublime's command-line <strong>Console</strong> by using the
   <strong>control+`</strong> (back-tick) shortcut or click menu View > Show Console.

   NOTE: The Console recognizes <strong>Python</strong> code.

0. Paste the command and press Enter.

   This creates the Installed Packages/ folder.

   If you get `IndentationError: unexpected indent` ???

0. Press `control+` again to remove the Console.
0. Restart Sublime Text.

### Use Package Control

0. Press <strong>Cmd+Shift+P</strong> to bring command palette in front.

   <img width="401" alt="scr sublime text 3 package manager" src="https://cloud.githubusercontent.com/assets/300046/15268029/c69a6dc8-198f-11e6-8860-7c8ccba65cef.png">

   The position from the previous action is remembered.

0. Type <strong>pac</strong> for Package Control. (Press Esc to dismiss it)
0. Select <strong>Install Package</strong>.

   NOTE: This may take a few seconds to bring up a list from a website visited above.

   <img width="469" alt="scr sublime text 3 package manager packages" src="https://cloud.githubusercontent.com/assets/300046/15268227/3c23493e-1995-11e6-983b-32fd4f708e76.png">

0. Type in a package name and press Enter to install it:

   <a target="_blank" href="https://packagecontrol.io/packages/Sublime%20Tutor">Sublime Tutor</a>

   (This is similar in operation to the Vim Tutor.)

0. Read more about SublimeText:

   <a target="_blank" href="http://sublimetexttips.com/">http://sublimetexttips.com</a>

   <a target="_blank" href="https://app.pluralsight.com/library/courses/sublime-text-3-from-scratch/table-of-contents">
   Sublime Text 3 From Scratch</a> 1h 42m video released 29 Oct 2013
   by <a target="_blank" href="http://www.jesseliberty.com/">Jesse Liberty</a>
   (<a target="_blank" href="https://www.twitter.com/jesseliberty/">@JesseLiberty</a>)

   ### Settings #

Use Sublime Text on Retina? for crisp, readable text, to Settings add 

   <pre><strong>
   "font_options" : ["gray_antialias"] 
   </strong></pre>

### Install spell check

Recommended spelling from the geniuses at Google.
Install ST v3 
https://github.com/noahcoad/google-spell-check/tree/st3
by https://github.com/noahcoad/google-spell-check/



<a id="Git_Editor"></a>

## Git Editor

If Git finds conflicts, it needs a way to show the differences in a text editor.

Git uses the default vim editor.
To quit the page, press <strong>:q!</strong> (colon to specify a command, q to specify quit, exclamation point for immediate).

Sublime Text is a popular text editor.

https://help.github.com/articles/associating-text-editors-with-git/




<a id="IntelliJ"></a>

## IntelliJ 

Advantage of using the intelliJ IDE:

   * Simple keystrokes wraps statements in a try-catch or if-else block.
   * It generates getter and setter methods for object attributes.
   * Inbuilt packaging tools like gradle, SBT, grunt, bower, etc.
   * Directly access databases such as SQL, ORACLE, PostgreSQL, Microsoft SQL Server 
   * Supports different programming languages (Java, Javascript, Clojure, etc.)
   * Editions for different operating systems:  Windows, Linux, etc. 

### IntelliJ Control Key Shortcuts

During initial configuration, specify the Project SDK
using the command up-arrow to the secret portal:

<ol type="1">
<li> Click New button </li>
<li> Select JDK </li>
<li> Click on the folder list (containing bin, etc.)</li>
<li> Press <strong> command + up arrow </strong>
to <strong> navigate up a folder level</strong>
from Home to the **MacOS** folder. </li>
<li> Click Choose to select the Java associated
with the system. This is called the "Secret Portal" approach.</li>
</ol>

Defaults changeable in Preferences | Keymaps

command + G to Generate
<br />
command + O to go to class
<br />
command + &#9003; Delete line

Web pages:

   * http://symbolcodes.tlt.psu.edu/keyboards/charpalosx.html
   * http://www.guru99.com/intellij-selenium-webdriver.html


<a name="#atom"></a>

## Atom #

0. Use an internet browser to <a target="_blank" href="https://atom.io/">atom.io</a>

   The site recognizes your operating system (OS X, Windows, or Linux)
   and presents the appropriate download button.

0. <a target="_blank" href="https://confirmsubscription.com/h/i/FDEEF15834EF73C7">Sign up for updates</a>

0. Follow Twitter @AtomEditor

   Atom has package control, themes, auto-completion built-in.

* https://github.com/atom/spell-check
  doesn't work
  per http://stackoverflow.com/questions/27731981/use-spell-check-in-code-comments

   To enable Spell Check for your current file type: put your cursor in the file,
   open the Command Palette (cmd-shift-p), 
   and run the Editor: Log Cursor Scope command. 

   This triggers a notification which will contain a list of scopes. The first scope that's listed is the one you should add to the list of scopes in the settings for the Spell Check package. 

   Examples: source.coffee, text.plain, text.html.basic.

   Press <strong>cmd-shift-:</strong> 
   to bring up the list of corrections when your cursor is on a misspelled word.


<a name="EditorConfig"></a>

## Editor Config #

Put a <strong>.EditorConfig</strong> file 
(<a target="_blank" href="https://editorconfig.org/#download"> from editorconfig.org</a>)
in your root folder, 
and the editor will format your code according to the rules defined in the file
for whatever type of file is being edited.

It's supported by default in the Atom editor.




<a name="Emett"></a>

## Emett #

It may take some effort to memorize the keyboard sequences, but these are the ones I remember because I save time using them:



<a name="Eclipse"></a>

## Eclipse IDE install #

To install 
   <a target="_blank" href="http://macappstore.org/eclipse-java/">eclipse-java</a>
using [Homebrew](/macos-homebrew/):

   <tt><strong>
   brew update<br />
   brew cask install eclipse-java
   </strong></tt>

   The response:

   <pre>
Please migrate your Casks to the new location and delete /opt/homebrew-cask/Caskroom,
or if you would like to keep your Caskroom at /opt/homebrew-cask/Caskroom, add the
following to your HOMEBREW_CASK_OPTS:
&nbsp;
  --caskroom=/opt/homebrew-cask/Caskroom
&nbsp;
For more details on each of those options, see https://github.com/caskroom/homebrew-cask/issues/21913.
==> Satisfying dependencies
complete
==> Downloading https://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/neon/R/eclipse-java-neon-R-macosx-cocoa-x86_64.tar.gz&r=1
==> Verifying checksum for Cask eclipse-java
==> Moving App 'Eclipse.app' to '/Applications/Eclipse.app'
🍺  eclipse-java staged at '/opt/homebrew-cask/Caskroom/eclipse-java/4.6.0' (0B)
   </pre>


<a name="Code"></a>

## Microsoft Code #

On Mac: 
   To get VS Code to make use of the current working directory, follow
   <a target="_blank" href="http://stackoverflow.com/questions/30159158/how-do-i-set-up-a-link-to-open-up-visual-studio-code-from-terminal-on-osx">
   these instructions</a>:   

0. In Finder, click on a file using two fingers to select
   <strong>Open with</strong> Visual Studio Code (version 1.0+).

0. Select Code's menu View, Command Palette at the top of the screen.

0. Begin typing this until the full command is recognized in the list:

   <tt><strong>
   Install 'Code' command in PATH
   </strong></tt>

0. Select the full command that appears in the drop-down.

0. Exit the Code program.

0. You can now, in a new Terminal shell window, use the code command to open a file:

   <tt><strong>
   code hello
   </strong></tt>

   BTW, "hello" in the example above can be any file.

* http://michaelcrump.net/using-github-with-visualstudio-code/


## More on front-end styling #

This is one of several topics:

{% include front-end_links.html %}


## More on OSX #

This is one of a series on Mac OSX:

{% include mac_links.html %}
