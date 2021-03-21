# cli-bookmarker
A very simple cli bookmarker made with shell script that allows
assignment of different URLs patterns for different launchers.

## Usage
```
bm [url] [description]? [tag...]?
bm [option]
bm [option] [tag]
bm [option] [id...]
bm [option] [url]
```

## Configuration

By default, cli-bookmarker will look for the configuration file:
```
%HOME/.config/cli-bookmarker/bmrc
```

 which can be created with:
```
bm --create-config
```

A simple configuration would be:
```
[general]
bmfile $HOME/bookmarks
editor vim
browser firefox
```

By default the launcher uses xdg-open and http/https bookmarks must start with http:// or https://. By changing the default browser, urls like "github.com" are going to work as expected.

### URL patterns

cli-bookmarker is able to open specific urls with specific software.
A simple configuration:
```bash
[urls]
#launch youtube videos on vlc
youtube.com/watch vlc 
#launch github with firefox
github.com firefox
#laucnh gemini's protocol URLs in the terminal browser amfora
gemini:// amfora
```
this works by matching the url the user intends to launch with every
entry in \[urls\], the last match one that matches, will set the launcher.



## Tools Required
* fzf
* software from gnu core utils like cat, sed, awk, echo, column...

## Options
```
--create-config, create a configuration file: $HOME/.config/cli-bookmarker/bmrc
-l, list all the bookmarks
-r, remove bookmark with the specified id, or search with fzf if not
-o, open bookmark if id is specified, open URL if a url is specified or, search with fzf if no argument was given
-e, edit with default text editor
-t, fuzzy search of entries with an especific tag
```

## Examples

create a configuration file


add a bookmark
```
bm https://www.github.com
```

Add a bookmark with a description
```
bm https:/www.example.com "an example website"
```

Add a bookmark with description and tags
```
bm https://www.example2.com "another example website" tag1 tag2 tag3
```

list all
```
bm -l
```

list filtering by tag
```
bm -l classical-music
```

remove the third and fourth entry
```
bm -r 3 4
```

search the entries you want to remove. You can select multiple entries with tab
```
bm -r
```

open the second entry
```
bm -o 2
```

fzf search before launching
```
bm -o
```

launch any URL
```
bm -o w3.org
```

fzf search filtered by tags
```
bm -t music
```

edit with default text editor
```
bm -e
```

## TODO

* Help command
* Version Command
* import favorites from browser
