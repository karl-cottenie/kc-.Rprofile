# kc-.Rprofile
How to create a profile file that reads the beginning of each R file

This works nicely with the new snippet I created.
In RStudio > Preferences > code > Edit Snippets...
Copy the lines below, and save the updated snippets file

snippet stup
	##############################
	## ${1:title}
	##
	## Karl Cottenie
	##
	`r paste("##", Sys.Date())`
	##
	##############################
	
	library(${2:package})
	
	# Startup ends here
	
  Now if you type "stup" at the beginning of a file, it will paste the above code, you can add the title of your script file, and when you press your tab key the cursor will jump to the library command, and you can for instance add tidyverse, or ggplot, or whatever you normally use. The snippet will automatically add the date, of course you should change the author :-)
