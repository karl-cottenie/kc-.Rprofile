# kc-.Rprofile
## How to create a profile file that reads the beginning of each R file
Copy this profile file either in your home directory or in each working directory. A quick google on .Rprofile and your OS will help you out for the advantages/disadvantages of this. However, I created this profile file to ensure that it will read all your script files within a folder, and execute them until it finds the line "# Startup ends here". So that is why I called it generic but specific: it is specific for each file, so that you can load for instance each library on a script by script basis. 

I assume that this will be mainly for loading libraries, so I specified the script to only read the first 30 lines, but you can increase/decrease this for your coding practices. I also made it recursive, so it will read all the script files within the folder structure, but you can change this too.

And I have also added some encouragement, that has the secondary objective that you can see if the .Rprofile code worked correctly.

## Snippet usage

This works nicely with the new snippet I created.
In RStudio > Preferences > code > Edit Snippets...
Copy the lines below, and save the updated snippets file

```
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
```

  Now if you type "stup" at the beginning of a file, it will paste the above code, you can add the title of your script file, and when you press your tab key the cursor will jump to the library command, and you can for instance add tidyverse, or ggplot, or whatever you normally use. The snippet will automatically add the date, of course you should change the author :-)
