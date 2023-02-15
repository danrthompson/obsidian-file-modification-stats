# Better Word Count

## Overview
This plugin tracks the number of words added to each file on each day.

## Features
As mentioned, it tracks the number of words added or removed from each file on each day. So for each day, you have a list of files modified, with the word count they had at the start of the day, as well as the word count at the end of the day.

From that, you can calculate the number of words changed per day for each file, the number of words written per day, the number of words written in total, etc.

I have also added a function to the plugin that processes all the files that already exist when the plugin is added. That way, the word counts are not inaccurate. Without that, anytime you modify a pre-existing file, the plugin will think that you added all of the contents of the file that day. Whereas if you call `processNotesAfterInstallation`, it will store the number of words in the file when the plugin was installed, so that each day's word count will only contain the new files that were added that day.

It handles concurrency properly with multiple devices, although if you make updates with two devices at the same time, it could lose the changes from one or the other device. But generally it should lose very little data, and in the end it should be fine because it will just misattribute a handful of words to the wrong day.

## Limitations

Right now, it just stores that info in the settings. You can create a dataviewjs table that shows the info in any way you want, but you have to create that query yourself at the moment.

Also, there is not a way to use a command to run `processNotesAfterInstallation`. You have to do it from the console.

Right now, it will not handle renaming files or deleting files properly. Renamed files will be seen as newly created files and the entire contents will show up for the day that the rename took place. And deleted files (and therefore the accompanying deleted characters) are not tracked. It will store the stats from the deleted file indefinitely.

## Future Features
I want to add commands that will automatically create dataview queries to show daily stats on your daily notes page, as well as other queries that show useful information.

Right now, I have a dataview query that I am using that shows the files modified on a given day on the daily note page. I'd like to change what it shows, and also add stats about how many words were added in a given day, or a given range of days.

I want to add a command that will call `processNotesAfterInstallation`.

This is very much a hobby project, so I cannot guarantee there will be any future additions to the project going forward.