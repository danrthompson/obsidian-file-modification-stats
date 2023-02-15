# Better Word Count

## Overview
This plugin tracks the number of words added to each file on each day.

## Features
As mentioned, it tracks the number of words added or removed from each file on each day. So for each day, you have a list of files modified, with the word count they had at the start of the day, as well as the word count at the end of the day.

From that, you can calculate the number of words changed per day for each file, the number of words written per day, the number of words written in total, etc.

I have also added a function to the plugin that processes all the files that already exist when the plugin is added. That way, the word counts are not inaccurate. Without that, anytime you modify a pre-existing file, the plugin will think that you added all of the contents of the file that day. Whereas if you call `processNotesAfterInstallation`, it will store the number of words in the file when the plugin was installed, so that each day's word count will only contain the new files that were added that day.

## Limitations

Right now, it just stores that info in the settings. You can create a dataviewjs table that shows the info in any way you want, but you have to create that query yourself at the moment.

Also, there is not a way to use a command to run `processNotesAfterInstallation`. You have to do it from the console.
## Future Features
I want to add commands that will automatically create dataview queries to show daily stats on your daily notes page, as well as other queries that show useful information.

I want to add a command that will call `processNotesAfterInstallation`.

This is very much a hobby project, so I cannot guarantee there will be any future additions to the project going forward.