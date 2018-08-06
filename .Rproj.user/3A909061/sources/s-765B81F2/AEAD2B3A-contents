## Script which copies the labs from the Documents folder to the website folder

# Start with the location of the ids_labs folder
lab_directory <- "~/Documents/ids_labs/"

# Choose destination 
destination_directory <- "~/Documents/Websites/ids-labs/content/labs/"

# Find the individual lab folders
unit_directories <- paste0(lab_directory, "unit_", 1:4) 
lab_folders <- list.dirs(unit_directories, recursive = FALSE)

# Remove the wierd "pd" folders
lab_folders <- lab_folders[!grepl("pdlab", lab_folders)]

# Create a list of ALL lab files
lab_files <- list.files(lab_folders)

# Find the HTML files
html_file <- grep("\\.html$", list.files(lab_folders), value = TRUE)

# Copt where the HTML files reside
html_from <- paste0(lab_folders, "/", html_file)

# Transfer HTML files to new folder
file.copy(html_from, destination_directory)

# Search for sub-directories and copy them over
for (i in seq_along(lab_folders)) {
  folder_contents <- list.dirs(lab_folders[i])
  if (length(list.dirs(lab_folders[i])) > 1) {
    file.copy(folder_contents[-1], destination_directory, recursive = TRUE)
  }
}


