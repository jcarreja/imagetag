# imagetag
script to tag images using bash, dmenu, and exiftool

## Usage

    $ imagetag -t "tags,to,choose,from" imagefiles
    $ imagetag -T /path/to/tagfile imagefiles

When invoking imagetag a taglist needs to be supplied that populates `dmenu`s selection prompt.
The imagefiles are either provided by a list or via stdin.
`dmenu` is then spawned with the current tags (unique list extracted from the imagefiles) and accepts additional tags.

## Adding and removing tags, special tags
Adding is as easy as typing `tag` into dmenu and hitting `Enter`, removing happens if a string leads with a minus sign like `-tag`.
The loop is broken if the special tag "n/a" is supplied (putting "n/a" as the first tag in the supplied tag-list makes it the first choice in dmenu).

## Behind the scenes
The actual update is performed using exiftool, first removing and then adding tags. This process is however i/o-intensive for large raw files, and might take a while. This is the main point I will focus on in future updates.

## Where to use
Of course this can be used from the cmdline, but it was originally intended as an action-script for [sxiv](https://github.com/muennich/sxiv) (awesome program!).