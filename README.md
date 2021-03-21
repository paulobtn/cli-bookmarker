# cli-bookmarker
A very simple cli bookmarker made with shell script.
You can assign different URLs for different launchers

## Usage
```
bm [url] [description]? [tag]?
bm [option]
bm [option] [tag]
bm [option] [id...]
bm [option] [url]
```

## Tools Required
* fzf
* software from gnu core utils like cat, sed, awk, echo, column...

## Options
```
--create-config, create a configuration file: $HOME/.config/cli-bookmarker/bmrc
-l, list all the bookmarks
-r, remove bookmark with the specified id, or search with fzf if not
-o, open bookmark if id is specified, search with fzf if not 
-e, edit with default text editor
-t, fuzzy search of entries with an especific tag
```

## Examples

create a configuration file
```
bm --create-config
```

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
* open with xdg-open by default
* import favorites from browser