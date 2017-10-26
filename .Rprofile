#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#
#-#-#-#-#  First attempt for a generic but specific .Rprofile #-#-#-#-#
#-#-#-#-#                Karl Cottenie                        #-#-#-#-#
#-#-#-#-#                 2017-06-12                          #-#-#-#-#
#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#

options(prompt="R> ")
# be explicit about where I am coding
options(continue="... ")
# if code is not finished, makes it more obvious, because ... is longer than +
# Thanks to Cam for this suggestion.
options(width = 90, digits = 4)
# makes console width similar to RStudio script setting for me

.First <- function(){
## Startup code execution
#
# If
# you want to keep startup code included in your R script
# such as what libraries to run at each start up, similar to
# .RProfile, but not hide it in the .RProfile file
#
# Then
# include below code in your .RProfile file

rfiles = list.files(pattern = "\\.R$", full.names = T, recursive = F,
                    include.dirs = FALSE, ignore.case = TRUE)
# Get all the .R or .r files from the working directory. 
# If you want to use other scripts nested in your R folder, recursively,
# switch to "recursive = T", so also in subfolders within your R folder structure.


rfiles = lapply(rfiles, readLines, n = 30)
# read the first 30 lines, you can adjust this to make it bigger if necessary
# Another option is to specify in the first line where to end the startup code,
# then execute until that line, with potentially some code for executing full files.

ends.here = lapply(rfiles, function(x) which(x == "# Startup ends here"))
# This looks through each script file to determine at what line there is a mention
# of an end to run startup code.
# Change this with whatever indicator you want to use.

rfiles = rfiles[sapply(ends.here, length) == 1]
ends.here = ends.here[sapply(ends.here, length) == 1]
# these two lines remove files without startup code

mapply(x = rfiles, y = ends.here, function(x,y){
  lapply(x[1:y], function(z) eval(parse(text = z)))
})
# Runs the beginning of each file until the line of startup identifier

rm(rfiles, ends.here)
# Clean-up objects so they do not clutter your environment

cat("\n==================================\n")
cat("==                              ==\n")
cat("==   Welcome to the fun zone!   ==\n")
cat("==                              ==\n")
cat("==================================\n\n")
# You can never have enough positive encouragement in R.
}

# You will only see the next line if you pay attention :-)
.Last <- function(){
  cat("\n==========================================\n")
  cat("==                                      ==\n")
  cat("==   That was fun, come back for more!  ==\n")
  cat("==                                      ==\n")
  cat("==========================================\n\n")
}  
