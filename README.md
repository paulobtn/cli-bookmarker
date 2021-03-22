# cli-bookmarker
A very simple cli bookmarker made with shell script that allows fuzzy searching and
assignment of different URLs patterns for different launchers. <br>
Some things you can do with cli-bookmarker:
* Share bookmarks across different protocols: http, gopher, gemini... each one opening with its respective browser
* fuzzy search through your saved youtube videos and launch them with your music or video player
* Use tags to organize your bookmarks

## Instalation
put the bm file somewhere you can launch such as $HOME/.local/bin: 
```
([ -d "$HOME/.local/bin" ] || mkdir -p "$HOME/.local/bin") && \
curl -sSL https://raw.githubusercontent.com/paulonetodev/cli-bookmarker/main/bm -o "$HOME/.local/bin/bm" && \
sudo chmod +x "$HOME/.local/bin/bm"
```
To launch as simply "bm" you should add $HOME/.local/bin to your path
```
export PATH="$HOME/.local/bin:$PATH"
```

### Tools Required
* fzf
* software from gnu core utils like cat, sed, awk, echo, column... normally they are installed by default in your distribution

## Usage
```
bm [url] [description]? [tag...]?
bm [option]
bm [option] [tag]
bm [option] [id...]
bm [option] [url]
```
## Options
```
--create-config, create a configuration file: $HOME/.config/cli-bookmarker/bmrc
-l, list all the bookmarks
-r, remove bookmark with the specified id, or search with fzf if not
-o, open bookmark if id is specified, open URL if a url is specified or, search with fzf if no argument was given
-e, edit with default text editor
-t, fuzzy search of entries with an especific tag
-h,--help show help
-v,--version show version
```

## Configuration

By default, cli-bookmarker will look for the configuration file:
```
$HOME/.config/cli-bookmarker/bmrc
```

 which can be created with:
```bash
bm --create-config
```

A simple configuration would be:
```bash
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
# launch youtube videos with vlc
youtube.com/watch vlc 
# launch github with firefox
github.com firefox
# launch gemini's URLs in the terminal browser amfora
gemini:// amfora
```
this works by matching the url the user intends to launch with every
entry in \[urls\], the last one that matches will define the launcher.


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

search and launch bookmark
```
bm
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

* import favorites from browser

## License

License GPLv3: GNU GPL version 3. <br>
This is free software: you are free to change and redistribute it. <br>
Written by Paulo Neto
