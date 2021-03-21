# cli-bookmarker
A very simple cli bookmarker made with shell script (still in development)

## Usage
```
bm [url] [description]? [tag]?
bm [option]
bm [option] [tag]
bm [option] [id...]
```

## Tools Required
* fzf
* core utils like cat, sed, awk, echo...

## Options
```
-l, list all the bookmarks
-r, remove bookmark with the specified id, or search with fzf if not
-o, -s, open bookmark if id is specified, search with fzf if not 
-e, edit with default text editor
-t, fuzzy search of entries with an especific tag
```

## Examples

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

fzf search filtered by tags
```
bm -t music
```

edit with default text editor
```
bm -e
```

## TODO features

* Debugging more use cases
* Create a configuration file where the user will be able to change the launchers, the bookmark file and the default editor
* open with xdg-open by default
* import favorites from browser
* feature to open urls directly, not necessarily using the id
* html page with tag filtering
* should create an empty file when listing if no file is found
