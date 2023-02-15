# Better Word Count

## Overview
This plugin tracks the number of words added to each file on each day.

## Features
As mentioned, it tracks the number of words added or removed from each file on each day. So for each day, you have a list of files modified, with the word count they had at the start of the day, as well as the word count at the end of the day.

From that, you can calculate the number of words changed per day for each file, the number of words written per day, the number of words written in total, etc.

## Limitations

Right now, it just stores that info in the settings. You can create a dataviewjs table that shows the info in any way you want, but you have to create that query yourself at the moment.

Also, as of now, when you install the plugin, it will start calculating from that date. It will not have history from the past. It will only process files that are changed, so if you don't change a file, you won't see information about that file in the stats.

Also, the first time you change a file after installing the plugin, it will think that you added all the words to the file on that day.
## Future Features
I want to add commands that will automatically create dataview queries to show daily stats on your daily notes page, as well as other queries that show useful information.

I want to add a command that will force the plugin to process every note in the Vault so that going forward the word counts are correct (rather than being artificially inflated because the first time you modify the file, the entire contents will be considered to have been written on that day).

This is very much a hobby project, so I cannot guarantee there will be any future additions to the project going forward.