# cli-bookmarker
A very simple cli bookmarker made with shell script (still in development)

## Usage
```
bm [option]
bm [option] [id...]
bm [option] [url]
bm [option] [url] -d [description] 
```

## Tools Required
* fzf
* core utils like cat, sed, awk, echo...

## Options
```
-a, write a bookmark in the bookmark file
-l, list all the bookmarks
-r, remove bookmark with the specified id, or search with fzf it not
-o, -s, open bookmark if id is specified, search with fzf if not 
-e, edit with default text editor
```

## Examples

add a bookmark
```
bm -a https://www.github.com
```
Add a bookmark with a description
```
bm -a https:/www.example.com -d "an example website"
```
list all
```
bm -l
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
edit with default text editor
```
bm -e
```

## TODO features

* Debugging more use cases
* Create a configuration file where the user will be able to change the launchers and the bookmark file
* open with xdg-open by default
* tags system, will be useful for playlists or tools like print all websites with tag X
* import favorites from browser
* feature to open urls directly, not necessarily using the id
* html page
