## Linux Command Line

#### Get Help

* \[command\] --help or -h : get help
* **man : display the online manual**
  * man -k &lt;search\_term&gt;
  * &lt;enter&gt; down, &lt;space&gt; down page, g-top,G-bottom, q-quit, /:search, ?: search back, h:help

#### Navigate

* Space :  can escape spaces, or use quote
* ls : list all files and folders of current working directory
  * ls -l : check permission
  * ls -a : all hiden and unhiden files
  * ls -al : combine 
  * ls -F: reveal file types
  * -t : list by time
  * -r : reverse order \(common: -latr\)
  * -R : list recusrively 
  * --color : colorize
* tree : visual ls -R
  * -d: directories only
  * -C colorize output
* cd &lt;directory&gt; : change directory
  * current directory is short for "."
  * parent directory is".."
  * previous directory is "-"
  * home directory "~"
* pwd - present working directory

#### Edit

* mkdir &lt;directory&gt; : make new directory in current directory
* cp &lt;source&gt; &lt;destination&gt; : copy
  * cp - r &lt;source&gt; &lt;destination&gt; : copy all files in source \( r is "recursive"\)
  * cp -i : run in interactive mode
* rm &lt;file&gt; : remove the file
  * rm -f &lt;file&gt; : remove and skip the confirmation
  * rm -r &lt;directory&gt; : remove the whole directory \(recursive\)
  * rm -rf &lt;directory&gt; : combine above two
  * rm &lt; source&gt; &lt;destination&gt; : rename the source
* rmdir
* mv &lt;source&gt; &lt;destination&gt;
  * -i: interactive mode
* touch \[option\] &lt;filename&gt;: create new empty file
* tar \[-\] c\|x\|t f \[file\]&lt;tarfile&gt; \[pattern\]: create, list or extract contents of a tar archive following patterns \(if supplied\)
  * c: create tar archive
  * x: extract files from archive
  * t: display table of contents
  * v: be verbose
  * z: use compression \( create tgz\)
  * -f file: the tar file to operate against
  * eg.tar acf tps.tgz tpsreports,  tar tf tps.tar
* gzip: compress files
  * gunzip: uncompress files
  * gzcat: concatenates compressed files
  * zcat: concatenates compressed files
* cat &lt;filename&gt; \[file name2\] &gt; \[new file name\] : concatenates and display files
* more &lt;fileame&gt;: browse through the file, &lt;space&gt; to enter, q to quit
* less &lt;file&gt;: enable backward movement and pattern searches on more
* head \[-\#\]  &lt;file&gt;, tail \[-\#\] &lt;file&gt;: view head and tail \(\# lines\)
  * tail -f \[file\]: follow line in real time
* diff &lt;file1&gt; &lt;file2&gt; : compare files
  * sdiff: side-by-side
  * vimdiff: highlight in vim
    * Crtl-w w: go to next window
    * :q quit, :qa quit all, :qa!
* sort &lt;file&gt;: sort text in file
  * sort -k &lt;F&gt; &lt;file&gt;: sort by key, F is the field number
  * sort -r: sort reversely
  * sort -u: sort unique
* du: estimates file usage
  * du -k: display in kilobytes
  * du -h: display in human readable format
* cut &lt;file&gt; : cut selected portions of a file
* tr

#### Search

* find \[path...\] \[options\] \[expression\] : recursively finds files in path, default path is pwd
  * -name matchname
  * -iname case-insensitive name
  * -ls perform ls on each found one
  * -mtime &lt;days&gt; that days old
  * -size &lt;size&gt;
  * -newer &lt;file&gt; newer than file
  * -exec &lt;command&gt; {} \; execute command on all found ones
* locate \[pattern\]: faster, but not in real-time
* grep &lt;pattern&gt; \[file\]: global regular-expression: display pattern matches a file
  * -i: ignore case
  * -c: count the number of occurrences in a file
  * -n: precede output with line numbers
  * -v: invert match
* file &lt;file&gt;: display file type
* strings: display printable strings
* where &lt;command&gt;:find the binary file of command

#### Pipes

&lt;command-output&gt; \| &lt;command-input&gt; : use output of command as another input

#### Wildcards

* \*: matches zero or more char
  * \*.txt, a\*.txt, 
* ?: matches one char
* \[\] : match one of eg. \[aeiou\]
  * \[!\]: matches not char
  * \[a-e\], \[3-6\]: matches range
  * named classes
    * \[\[:alpha:\]\]
    * \[\[alnum:\]\] \(alpha-numeric: letters and decimal digits\)
    * \[\[:digit:\]\]
    * \[\[:lower:\]\], \[\[:upper:\]\]
    * \[\[:space:\]\], space, tab - all white space
* \&lt;wildcard&gt; : escape: match a wildcard
* can work with any command with parameter &lt;filename&gt;



