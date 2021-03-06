---
layout: page
title: "markdown格式快查手册"
description: ""
---
{% include JB/setup %}
Package Control Messages
========================

MarkdownEditing:
---------------

  # MarkdownEditing
  
  Markdown plugin for Sublime Text. Provides a decent Markdown color scheme (light and dark) with more __robust__ syntax highlighting and useful Markdown editing features for Sublime Text. 3 flavors are supported: Standard Markdown, __GitHub flavored Markdown__, MultiMarkdown.
  
  ![MarkdownEditing][github]
  
  [Dark][github 2] and [yellow][github 3] theme available.
  
  > Your kind donations will help [me](https://github.com/maliayas) pause my daily job and put more serious effort into the development of this plugin for the next 2 milestones ([2.0.5](https://github.com/SublimeText-Markdown/MarkdownEditing/issues?milestone=1&state=open) and [2.2.0](https://github.com/SublimeText-Markdown/MarkdownEditing/issues?milestone=2&state=open)). When they are completed, donation button will be removed. Thanks.
  > 
  > <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&amp;business=W2NXRPD43YSCU&amp;lc=TR&amp;item_name=Ali%20Ayas&amp;item_number=Open%20Source&amp;currency_code=USD&amp;bn=PP%2dDonationsBF%3abtn_donate_SM%2egif%3aNonHosted"><img src="https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif" alt="[paypal]" /></a>
  
  ## Overview
  
  * [Features](#features)
  * [Key Bindings](#key-bindings)
  * [GFM Specific Features](#gfm-specific-features)
  * [Commands for Command Palette](#commands-for-command-palette)
  * [Installation](#installation)
  * [Configuration](#configuration)
  * [Tips](#tips)
  * [Similar Plugins](#similar-plugins)
  * [Known Bugs](#known-bugs)
  * [Contributing](#contributing)
  * [Credits](#credits)
  * [License](#license)
  
  ## Features
  
  * Asterisks and underscores are autopaired and will wrap selected text
      - If you start an empty pair and hit backspace, both elements are deleted
      - If you start an empty pair and hit space, the right element is deleted
  * Backticks are paired
  * At the end of a list item, pressing <kbd>Enter</kbd> will automatically insert the new list item bullet.
      - Pressing <kbd>Tab</kbd> on the blank list item will indent it and switch the list bullet to another one (Order is `*`, `-`, `+` in a cycle).
      - Pressing <kbd>Shift</kbd> <kbd>Tab</kbd> on the blank list item will unindent it in the same way as above.
      - Sequential <kbd>Tab</kbd> s or <kbd>Shift</kbd> <kbd>Tab</kbd> s are supported.
      - You can disable automatic bullet switching or choose which bullets to be used, in your settings file.
      - If a list item contains a [GFM task][GFM], pressing <kbd>Enter</kbd> at the end of the line will continue with a new blank task.
  * At the end of a blockquote line, pressing <kbd>Enter</kbd> will automatically extend blockquote.
  * Selecting some text and pressing <kbd>&gt;</kbd> will convert it to blockquote. The first and the last line don't have to be fully selected; partial select works, too.
  * Left bracket pairing is modified to eliminate the selection and leave the cursor at a point where you can insert a `[]` or `()` pair for a link
  * Displays Markdown headers in the Project Symbol List (<kbd>Ctrl</kbd> <kbd>Shift</kbd> <kbd>R</kbd>). They will start with `#`, so you will know they belong to markdown files at a glance. Also they will be on top of the list because of the presedence of `#`.
  * <kbd>~</kbd> wraps selected text with `~~` (strikethrough).
  * Typing `#` when there's a selection will surround it with `#` to make it a headline. Multiple presses add additional hashes, increasing the level of the header. Once you hit 6 hashes, it will reset to 0 on the next press. The `mde.match_header_hashes` will determine if the `#` are mirrored on both sides or just at the beginning of the line.
  * Typing return at the end of a line that begins with hashmarks will insert closing hashmarks on the headline. They're not required for Markdown, it's just aesthetics, and you can change the `mde.match_header_hashes` option in your settings to disable.
  * Setext-style headers can be completed with `Tab`. That is, typing `Tab` on a line containing only `=` or `-` characters will add or remove enough characters to it to match the length of the line above.
  
  ## Key Bindings
  
  | OS X | Windows/Linux | Description |
  |------|---------------|-------------|
  | <kbd>⌘</kbd><kbd>⌥</kbd><kbd>V</kbd> | <kbd>Ctrl</kbd><kbd>Win</kbd><kbd>V</kbd> | Pastes the contents of the clipboard as an inline link on selected text.
  | <kbd>⌘</kbd><kbd>⌥</kbd><kbd>R</kbd> | <kbd>Ctrl</kbd><kbd>Win</kbd><kbd>R</kbd> | Pastes the contents of the clipboard as a reference link.
  | <kbd>⌘</kbd><kbd>⌥</kbd><kbd>K</kbd> | <kbd>Ctrl</kbd><kbd>Win</kbd><kbd>K</kbd> | Inserts a standard inline link.
  | <kbd>⌘</kbd><kbd>⇧</kbd><kbd>K</kbd> | <kbd>Shift</kbd><kbd>Win</kbd><kbd>K</kbd> | Inserts an inline image.
  | <kbd>⌘</kbd><kbd>⌥</kbd><kbd>B</kbd> <kbd>⌘</kbd><kbd>⌥</kbd><kbd>I</kbd> | <kbd>Ctrl</kbd><kbd>Shift</kbd><kbd>B</kbd> <kbd>Ctrl</kbd><kbd>Shift</kbd><kbd>I</kbd> | These are bound to bold and italic. They work both with and without selections. If there is no selection, they will just transform the word under the cursor. These keybindings will unbold/unitalicize selection if it is already bold/italic.
  | <kbd>⌘</kbd><kbd>^</kbd><kbd>1...6</kbd> | <kbd>Ctrl</kbd><kbd>1...6</kbd> | These will add the corresponding number of hashmarks for headlines. Works on blank lines and selected text in tandem with the above headline tools. If you select an entire existing headline, the current hashmarks will be removed and replaced with the header level you requested. This command respects the `mde.match_header_hashes` preference setting.
  | <kbd>⌘</kbd><kbd>⇧</kbd><kbd>6</kbd> | <kbd>Ctrl</kbd><kbd>⇧</kbd><kbd>6</kbd> | Inserts a footnote and jump to its definition. If your cursor is in a definition, it will jump back to the marker.
  | <kbd>⌥</kbd><kbd>⇧</kbd><kbd>F</kbd> | <kbd>Alt</kbd><kbd>Shift</kbd><kbd>F</kbd> | Locates footnote markers without definitions and inserts their markers for the definition.
  | <kbd>⌥</kbd><kbd>⇧</kbd><kbd>G</kbd> | <kbd>Alt</kbd><kbd>Shift</kbd><kbd>G</kbd> | Locates link references without definitions and inserts their labels at the bottom for the definition.
  
  ## GFM Specific Features
  
  Underscores in words doesn't mess with bold or italic style:
  
  ![underscore-in-words][github 5]
  
  Fenced code blocks gets syntax highlighting inside:
  
  ![fenced-code-block][github 6]
  
  Keyboard shortcuts gets highlighted like in GitHub:
  
  ![keyboard-shortcut][github 7]
  
  Strikethrough is supported:
  
  ![strikethrough][github 8]
  
  ## Commands for Command Palette
  
  ### Fix Underlined Headers
  
  Adjusts every setext-style header to add or remove `=` or `-` characters as needed to match the lengths of their header text.
  
  ### Convert Underlined Headers to ATX
  
  Converts every setext-style header into an ATX style header. If something is selected only the headers in the selections will be converted, otherwise the conversion will be applied to the whole view.
  
  ### Add Missing Link Labels
  
  Scans document for referenced link usages (`[some link][some_ref]` and `[some link][]`) and checks if they are all defined. If there are undefined link references, command will automatically create their definition snippet at the bottom of the file.
  
  ## Installation
  
  _Note_: Sublime text has a native tiny package for Markdown. However, when MarkdownEditing is enabled, native package causes some conflicts. For this reason, MarkdownEditing will automatically disable it. Since it doesn't bring anything new over MarkdownEditing, this is not a loss. But remember, when you disable MarkdownEditing, you have to reenable the native one manually (if you want).
  
  If you are using Sublime Text 2, you have to disable the native package _manually_. To do that, add `Markdown` to your `ignored_packages` list in ST user settings:
  
      "ignored_packages": [..., "Markdown"],
  
  ### [Package Control][wbond]
  
  The preferred method of installation is via [Sublime Package Control][wbond].
  
  1. [Install Sublime Package Control][wbond 2]
  2. From inside Sublime Text, open Package Control's Command Pallet: <kbd>CTRL</kbd> <kbd>SHIFT</kbd> <kbd>P</kbd> (Windows, Linux) or <kbd>CMD</kbd> <kbd>SHIFT</kbd> <kbd>P</kbd> on Mac.
  3. Type `install package` and hit Return. A list of available packages will be displayed.
  4. Type `MarkdownEditing` and hit Return. The package will be downloaded to the appropriate directory.
  5. Restart Sublime Text to complete installation. Open a Markdown file and this custom theme. The features listed above should now be available.
  
  ### Manual Installation
  
  1. Download or clone this repository to a directory `MarkdownEditing` in the Sublime Text Packages directory for your platform:
  2. Restart Sublime Text to complete installation. Open a Markdown file and this custom theme. The features listed above should now be available.
  
  ## Configuration
  
  The plugin contains 3 different Markdown flavors: Standard Markdown, GitHub flavored Markdown, MultiMarkdown. Default is GitHub flavored Markdown. If you want to set another one as default, open a Markdown file and select your flavor from the menu: `View > Syntax > Open all with current extension as`. You're done.
  
  You may want to have a look at the default settings files. They are located at:
  
      Packages/MarkdownEditing/Markdown.sublime-settings         [GitHub flavored Markdown]
      Packages/MarkdownEditing/Markdown (Standard).sublime-settings
      Packages/MarkdownEditing/MultiMarkdown.sublime-settings
  
  If you want to override any of the default settings, you can open the appropriate user settings file using the `Preferences > Package Settings > Markdown Editing` menu. Each flavor has a different settings file.
  
  Bold and italic markers are configurable through ST shell variables. You can use `Preferences > Package Settings > Markdown Editing` menu to see the default settings file. In order to override it, copy & paste its content into the user settings file (`Packages/User/Bold and Italic Markers.tmPreferences`) from the menu and make your edits. It is pretty straightforward.
  
  In order to activate the dark or the yellow theme, put one of these lines to your user settings file of the flavor (`Packages/User/[flavor].sublime-settings`):
  
      "color_scheme": "Packages/MarkdownEditing/MarkdownEditor-Dark.tmTheme",
      "color_scheme": "Packages/MarkdownEditing/MarkdownEditor-Yellow.tmTheme",
  
  If you want to go with your already existing theme, you can reenable it with the same method as above. Keep in mind that, that theme may not cover all the parts of the Markdown syntax that this plugin defines.
  
  By default, when you install the plugin, files with these extensions will be assigned to Markdown syntax: "md", "txt", "mdown", "markdown", "markdn". If you want to prevent any of these extensions to be opened as Markdown, follow these steps:
  
  1. Click on the language menu at bottom right
  2. Select "Open all with current extension as"
  3. Choose your preferred syntax for that extension
  
  ## Tips
  
  We are maintaining a [tips section][tips] in our [Wiki][]. Jump there to learn from others or share your experiences with others.
  
  ## Similar Plugins
  
  * [Knockdown][]
  
       Knockdown offers useful Markdown features and a custom Markdown theme. All of its unique features except its theme are ported to MarkdownEditing and some of them are actually improved further in MarkdownEditing.
  * [Sublime Markdown Extended][]
  * [SmartMarkdown][]
  
  ## Known Bugs
  
  * Setext-style headers (`===` and `---`) do not show up in the symbol list. This is due to a Sublime Text limitation (see [#158][]). However, we are able to put a placeholder to indicate the existence of the header. We encourage you to use Atx-style headers (`#`).
  
  ## Contributing
  
  See `CONTRIBUTING.md` file.
  
  ## Credits
  
  MarkdownEditing was originally created by [Brett Terpstra][brettterpstra] and has become a community project with the goal of consolidating the best features from the varied collection of Markdown packages for Sublime Text. Current development is headed up by [Ali Ayas][github 9].
  
  Related blog posts from Brett:
  * http://brettterpstra.com/2012/05/17/markdown-editing-for-sublime-text-2-humble-beginnings/
  * http://brettterpstra.com/2013/11/23/markdownediting-for-sublime-text-updates/
  
  This plugin contains portions of code from [Knockdown][].
  
  Footnote commands were submitted by [J. Nicholas Geist][github 4] and originated at [geekabouttown][geekabouttown].
  
  ## License
  
  MarkdownEditing is released under the [MIT License][opensource].
  
  [TableEditor]:                 https://github.com/vkocubinsky/SublimeTableEditor
  [Knockdown]:                   https://github.com/aziz/knockdown/
  [Sublime Markdown Extended]:   https://github.com/jonschlinkert/sublime-markdown-extended
  [SmartMarkdown]:               https://github.com/demon386/SmartMarkdown
  [Typewriter]:                  https://github.com/alehandrof/Typewriter
  [OpenUrl]:                     https://github.com/noahcoad/open-url
  [brettterpstra]: http://brettterpstra.com
  [geekabouttown]: http://geekabouttown.com/posts/sublime-text-2-markdown-footnote-goodness
  [github]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/light.png
  [github 2]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/dark.png
  [github 3]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/yellow.png
  [github 4]: https://github.com/jngeist
  [github 5]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/underscore-in-words.png
  [github 6]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/fenced-code-block.png
  [github 7]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/keyboard-shortcut.png
  [github 8]: https://raw.github.com/SublimeText-Markdown/MarkdownEditing/master/screenshots/strikethrough.png
  [github 9]: https://github.com/maliayas
  [opensource]: http://www.opensource.org/licenses/MIT
  [wbond]: http://wbond.net/sublime_packages/package_control
  [wbond 2]: http://wbond.net/sublime_packages/package_control/installation
  [FullScreenStatus]: https://github.com/maliayas/SublimeText_FullScreenStatus
  [macstories]: http://www.macstories.net/roundups/sublime-text-2-and-markdown-tips-tricks-and-links/
  [tips]: https://github.com/SublimeText-Markdown/MarkdownEditing/wiki/Tips
  [Wiki]: https://github.com/SublimeText-Markdown/MarkdownEditing/wiki
  [GFM]: https://help.github.com/articles/github-flavored-markdown
  [#158]: https://github.com/SublimeText-Markdown/MarkdownEditing/issues/158
  


Markdown Preview:
----------------

  Sublime Text 2/3 Markdown Preview
  =================================
  
  Preview and build your markdown files quickly in your web browser from sublime text 2/3. 
  
  You can use builtin [python-markdown][10] parser or use the [github markdown API][5] for the conversion.
  
  **NOTE:** If you choose the GitHub API for conversion (set parser: github in your settings), your code will be sent through https to github for live conversion. You'll have [Github flavored markdown][6], syntax highlighting and EMOJI support for free :heart: :octocat: :gift:. If you make more than 60 calls a day, be sure to set your GitHub API key in the settings :)
  
  **LINUX users:** If you want to use GitHub API for conversion, you'll need to have a custom Python install that includes python-ssl as its not built in the Sublime Text 2 Linux package. see [@dusteye comment][8]. If you use a custom window manager, also be sure to set a `BROWSER` environment variable. see [@PPvG comments][9]
  
  ## Features :
  
   - Markdown preview using the [Python-markdown][10] or the Github API just choose select the build commands.
   - Build markdown file using Sublime Text build system. The build parser are config via the `"parser"` config.
   - Browser preview auto reload on save if you have the [ST2 LiveReload plugin][7] installed.
   - Builtin parser : supports `abbr`, `attr_list`, `def_list`, `fenced_code`, `footnotes`, `tables`, `smart_strong` and `toc` markdown extensions.
   - CSS search path for local and build-in CSS files (always enabled) and/or CSS overriding if you need
   - YAML support thanks to @tommi
   - Clipboard selection and copy to clipboard thanks to @hexatrope
   - MathJax support : \\(\frac{\pi}{2}\\) thanks to @bps10
   - HTML template customisation thanks to @hozaka
  
  ## Installation :
  
  ### Using [Package Control][3] (*Recommended*)
  
  For all Sublime Text 2/3 users we recommend install via [Package Control][3].
  
  1. [Install][11] Package Control if you haven't yet.
  2. Use `cmd+shift+P` then `Package Control: Install Package`
  3. Look for `Markdown Preview` and install it.
  
  ### Manual Install
  
  1. Click the `Preferences > Browse Packages…` menu
  2. Browse up a folder and then into the `Installed Packages/` folder
  3. Download [zip package][12] rename it to `Markdown Preview.sublime-package` and copy it into the `Installed Packages/` directory
  4. Restart Sublime Text
  
  ## Usage :
  
  ### To preview :
  
   - optionally select some of your markdown for conversion
   - use `cmd+shift+P` then `Markdown Preview` to show the follow commands:
    - Markdown Preview: Python Markdown: Preview in Browser
    - Markdown Preview: Python Markdown: Export HTML in Sublime Text
    - Markdown Preview: Python Markdown: Copy to Clipboard
    - Markdown Preview: Github Flavored Markdown: Preview in Browser
    - Markdown Preview: Github Flavored Markdown: Export HTML in Sublime Text
    - Markdown Preview: Github Flavored Markdown: Copy to Clipboard
    - Markdown Preview: Open Markdown Cheat sheet
   - or bind some key in your user key binding, using a line like this one:
     `{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} },`
   - once converted a first time, the output HTML will be updated on each file save (with LiveReload plugin)
  
  ### To build :
  
   - Just use `Ctrl+B` (Windows/Linux) or `cmd+B` (Mac) to build current file.
  
  ### To config :
  
  Using Sublime Text menu: `Preferences`->`Package Settings`->`Markdown Preview`
  
  - `Settings - User` is where you change your settings for Markdown Preview.
  - `Settings - Default` is a good reference with detailed descriptions for each setting.
  
  
  ## Support :
  
  - Any bugs about Markdown Preview please feel free to report [here][issue].
  - And you are welcome to fork and submit pullrequests.
  
  
  ## License :
  
  The code is available at github [project][home] under [MIT licence][4].
  
   [0]: https://github.com/trentm/python-markdown2
   [home]: https://github.com/revolunet/sublimetext-markdown-preview
   [3]: https://sublime.wbond.net/
   [4]: http://revolunet.mit-license.org
   [5]: http://developer.github.com/v3/markdown
   [6]: http://github.github.com/github-flavored-markdown/
   [7]: https://github.com/dz0ny/LiveReload-sublimetext2
   [8]: https://github.com/revolunet/sublimetext-markdown-preview/issues/27#issuecomment-11772098
   [9]: https://github.com/revolunet/sublimetext-markdown-preview/issues/78#issuecomment-15644727
   [10]: https://github.com/waylan/Python-Markdown
   [11]: https://sublime.wbond.net/installation
   [12]: https://github.com/revolunet/sublimetext-markdown-preview/archive/master.zip
   [issue]: https://github.com/revolunet/sublimetext-markdown-preview/issues
   [settings]: https://github.com/revolunet/sublimetext-markdown-preview/issues
  
