# leaderboard

There are three components to creating a leaderboard with the present code:

1. demon/ A demon, that is supposed to be set in a server to track the appearance of files that contain results. The key file is ldb-update.sh, which creates a file list of results. If there are new files, then it runs regen_res.R, which appends the new data below the old one, and then pushes the updated folder onto github.

2. shinyapp/ A shinapp, which reads results from a pushed txt and displays them graphically.

3. Well-behaved humans, who do the following to add results.

- Users drop one or more folders containing your pyannote evals (which must include the text "result.pyannote" in the name) into an agreed-upon folder. The pattern and the folder can be changed at the top of the ldb-update.sh file
- Folders can be named anything and the files can be at any level of recursivity
- That said, if the system uses the ground truth VAD, then somewhere in the name (in a folder or in a file) the letters "gt" should appear. (And if it does not, then one should not use gt on the name!). NOTE. This was useful for our workshop; you can edit any filters that are useful to you using this example.
- Result files must have been generated using pyannote. NOTE: any system result that has a "Could not find hypothesis for file" warning gets removed from consideration

To reuse this code, 

- clone the present repo into a server
- set up a demon that runs ldb-update.sh regularly, probably [like this](http://etutorials.org/Linux+systems/how+linux+works/Chapter+4+Essential+System+Files+Servers+and+Utilities/4.6+Scheduling+Recurring+Tasks+with+Cron/)
- inspect app.R inside the shinyapp folder and modify the address at the top to read your own data
- I use [RStudio](https://www.rstudio.com/) for updating the shiny app code and publishing it. (You may want to follow a [shiny tutorial](https://shiny.rstudio.com/tutorial/) first.)
- you can trial-run the app locally in RStudio. To push it to [shinapps.io](shinapps.io) you need to have an account with them. [Here](https://acristia.shinyapps.io/jsalt19_spkd_lb/) is an example of a leaderboard created with this code.
- If you do go the online route, I recommend rename the shinyapp folder to something with more punch (by default, this folder's name will be on the url).