# Better Word Count

## Overview
This plugin tracks the number of words added to each file on each day.

## Features
As mentioned, it tracks the number of words added or removed from each file on each day. So for each day, you have a list of files modified, with the word count they had at the start of the day, as well as the word count at the end of the day.

From that, you can calculate the number of words changed per day for each file, the number of words written per day, the number of words written in total, etc.

I have also added a function to the plugin that processes all the files that already exist when the plugin is added. That way, the word counts are not inaccurate. Without that, anytime you modify a pre-existing file, the plugin will think that you added all of the contents of the file that day. Whereas if you call `processNotesAfterInstallation`, it will store the number of words in the file when the plugin was installed, so that each day's word count will only contain the new files that were added that day.

It handles concurrency properly with multiple devices, although if you make updates with two devices at the same time, it could lose the changes from one or the other device. But generally it should lose very little data, and in the end it should be fine because it will just misattribute a handful of words to the wrong day.

It should handle renames and deletions properly, and it continues to store deleted data indefinitely.

I have created a function (that must be manually called), that you can run after externally changing files, and it should update things properly.

## Limitations

Right now, it just stores that info in the settings. You can create a dataviewjs table that shows the info in any way you want, but you have to create that query yourself at the moment.

Also, there is not a way to use a command to run `processNotesAfterInstallation`. You have to do it from the console.

If you externally edit the files (using an external application, like VSCode, e.g. to use find and replace), the plugin will not attribute the changes to the day that they happened on. Programmatic changes from plugins should be fine, but Obsidian will not pick up on changes made externally. Thus, they will only show up when the file is visited.

I have created a function (that must be manually called), that you can run after externally changing files, and it should update things properly.

## Future Features
I want to add functions that can calculate additional statistics, like
* Net number of words written per day (net meaning additions - deletions from net deleted files)
* Absolute number of words written per day (meaning additions only)
* Number of words written in total
* Number of words written up to a certain date, after a certain date, or in a certain window

The information to calculate those statistics is all present, but it would be nice to make it easy to expose them.

I want to add commands that will automatically create dataview queries to show daily stats on your daily notes page, as well as other queries that show useful information.

Right now, I have a dataview query that I am using that shows the files modified on a given day on the daily note page. I'd like to change what it shows, and also add stats about how many words were added in a given day, or a given range of days.

Ideally, I'd like to exclude words that were written by a template, especially for Daily Notes. I have quite a large template that I use for each day (around 500 words), and I'd like to be able to differentiate between words automatically written by a template vs words that I actually wrote.

I want to add a command that will call `processNotesAfterInstallation`.

This is very much a hobby project, so I cannot guarantee there will be any future additions to the project going forward.