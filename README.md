# kc-.Rprofile

## Problem in R: how to create a .Rprofile that does not hide important information ...

... but still is specific to each R script file. For instance, a lot of R users in our group load their packages at the top of their R scripts. Often, these packages are the same, but sometimes they add a different one for a specific type of analysis. I use the tidyverse all the time, and in some analyses vegan. A school of thought would be to automatically add these package to the start up using a .Rprofile file. Others would argue that this makes the code less reproducible, since some essential pieces of information are hidden from the R script file.

But what if you could have both? All the boilerplate stuff such as loading packages at the top of each R script file, but execute them automatically when you open that script file? I think I have found a solution to that mythical beast. I googled for it, but could not find anything similar, so that is why I provide my code here. Hopefully somebody else will find this useful, or point me to other, more elegant, solutions that I can incorporate in  my own code.

## How to create a generic but specific profile file that reads the beginning of each R file
Copy this profile file either in your home directory or in each working directory. A quick google on .Rprofile and your OS will help you out for the advantages/disadvantages of these two approaches. However, because of the generic and specific nature of the profile, it is intented to be used as your system-wide profile. 

I created this profile file to ensure that it will read all your script files within a folder, and execute them until it finds the line "# Startup ends here". I assume that this will be mainly for loading libraries, so I specified the script to only read the first 30 lines, but you can increase/decrease this for your coding practices. I also made it recursive, so it will read all the script files within the folder structure, but you can change this too.

And I have also added some encouragement, that has the secondary objective that you can see if the .Rprofile code worked correctly.

## Snippet usage

This works nicely with the new snippet I created. In RStudio > Preferences > code > Edit Snippets... copy the lines below, and save the updated snippets file.

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
	# Add as much code here that you want to execute each time your script file is loaded.
	
	# Startup ends here
```

  Now if you type "stup" at the beginning of a file, it will paste the above code, you can add the title of your script file, and when you press your tab key the cursor will jump to the library command, and you can for instance add tidyverse, or ggplot, or whatever you normally use. The snippet will automatically add the date, of course you can/should change the author :-)
  
If you want to start using this with your existing script files, just add a "# Startup ends here" line after your library statements, and you are good to go, easy peasy.
  
## Problems with my code, other options?

Just let me know, because there are probably edge cases I did not think about, and more elegant solutions that I will not find on my own.
