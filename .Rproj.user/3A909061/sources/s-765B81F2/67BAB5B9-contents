## Script which edits the labs to include a return link

# Start with the location of the lab html files
lab_html_dir <- "~/Documents/Websites/ids-labs/content/labs/"

# List all of the 
lab_files <- list.files(lab_html_dir, pattern = "\\.html", full.names = TRUE)

# Desired footer
desired_footer <- '.reveal footer {
  display:block;
  position: absolute;
  bottom: 0;
  left: 22px;
  width: 100%;
  font-size: 16pt;
  text-align: left; 
  z-index: 1;
}

.reveal .footer a {
  color: #215C94;
    text-decoration: none;
  -webkit-transition: color .15s ease;
  -moz-transition: color .15s ease;
  -ms-transition: color .15s ease;
  -o-transition: color .15s ease;
  transition: color .15s ease; }

.reveal .footer a:hover {
  color: #649DD4;
    text-shadow: none;
  border: none; }'

footer_code <- '</div>
<footer class="footer">
  <p><a href="{{ .Site.BaseURL }}"><span class="arrow">←</span>Return</a></p>
</footer>
</div>'

# 
# i = 1
for (i in seq_along(lab_files)) {
  # Read in html
  html_text <- readLines(lab_files[i])
  
  # Find the footer in css
  footer_start <- grep("\\.reveal footer \\{", html_text)
  footer_end <- footer_start + grep("\\}", html_text[footer_start:length(html_text)])[1]
  
  # Overwrite the normal footer with the desired one
  html_text[footer_start:footer_end] <- ""
  html_text[footer_start] <- desired_footer
  
  # Find the double </div> which ends the slides/sections
  footer_inds <- grep("^\\s+<\\/div>", html_text)
  html_text[footer_inds] <- ""
  html_text[footer_inds[1]] <- footer_code
  writeLines(html_text, lab_files[i])
}