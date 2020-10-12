### Shell

* Shell Emulators
  * bash
    * .bash\_profile, .bashrc
    * the contents on .profiile, .bash\_profile only execute for interactive sessions,
    * you can have all the same settings by referencing .bashrc in .bash\_profile
  * zsh
    * .zshrc
* Shell history
  * .bash\_history, .history, .histfile
  * history:displays history 
  * !N repeat command line number N
    * !! or !: repeat previous command
    * !string repeat most recent match
  * !:N \[&lt;event&gt;&lt;seprarator&gt;&lt;word&gt;\] 
    * eg vi !:2 \(second argument in the previous command line
    * !^: the first agrv, !$: the last
  * Ctrl-r: reverse history search
    * enter: execute a cmd
    * arrows-change one cmd
    * Ctrl-g: cancel the search
* Tab autocompletion
  * commands, files, environmental variables, usernames
* echo \[options\] &lt;string&gt;: print on the screen
  * echo $HOME: print variable
  * echo $?: get program return value
* export &lt;var=val&gt;: export a varaible: set a value of an environmental variable \(that are marked export\) and be visible to all child processes
  * export PATH = "&lt;new path&gt;:$PATH": add one path to PATH
* alias \[name \[=command\]\]: set alias for commands
  * unalias &lt;name&gt;:remove alais
    * unalias -a: remove all
* source &lt;file&gt; : run all commands in file and return
* date: print date
* exit: exit current shell session
* clear: clear screen

#### Environmental Variables

* $PATH: controls the search path of a command, contains a list of directories
* $PS1: customize shell prompt for .bash
  * \d: date in "Weekday Month Date"
  * \h: host name up to first period, H:hostname
  * \n:newline
  * \t: current time in 24, \T:current time in 12, \@:current time in am\pm, \A:current time in HH:MM
  * \u: user name
  * \w: current wd,\W: basename of current wd
  * $: if the effective UID is 0, a \#, otherwise a $
* $prompt: customize shell prompt for zsh 
  * [http://zsh.sourceforge.net/Doc/Release/Prompt-Expansion.html](http://zsh.sourceforge.net/Doc/Release/Prompt-Expansion.html)
* $EDITOR
* $HOME: home directory 
* $HISTSIZE: controls size of history
* LOGNAME: login name of user
* MAIL: local inbox
* PAGER: program to view a file
* OLDPWD:old working directory
* PWD: present working directory

#### Processes and Jobs

* ps: list all processes
  * -e: everything
    * -e --forest: display process tree
  * -f: full format
  * -u username: user's
  * -p pid: information for PID
* pstree: display in tree format
* top, htop: interactive viewer
* &lt;command&gt;&: start command in background\(so can continue with current session\)
* Ctrl-c: kill the foreground process
* Ctrl-z: suspend foreground process
* bg \[%num\]: background a suspended process
* fg \[%num\]: foreground a background process
* kill : kill by job number or PID
  * kill \[-sig\] pid: send a signal to a process
  * kill -l: display a list of signals
* jobs \[%num\]: list jobs
  * %%, %+: current jon, %- previous job
* cron: the scheduler for jobs
  * crontab &lt;file&gt; install a new crontab from file
  * crontab -l: list cron jobs
  * crontab -e:edit cron jobs
  * crontab -r: remove cron jobs
  * input jobs like: \[\* \* \* \* \*\] command 
    * minute, hour, day of the month, month of the year, day of the week
    * eg. 0,30 \* \* \* \* or \*/2 \* \* \* \*\(every 30 minutes \)
    * shortcuts: @yearly, @annually, @weekly, @daily ... in certain distro

#### Shell Command Line Editing

usually the default mode for editing is emacs. can change via commands

* by set -o emacs/vi \(bash, ksh, zsh\) or bindkey -e/v\(zsh,ecsh\) command
* Emacs Mode
  * C-p, C-n: previous/nect commandline\)
  * C-b,C-f: move left/right
  * C-e,C-a:move to begining/end
  * C-x C-e: edit in EDITOR\(default vim\)
* Vim Mode: begin with insert mode
  * esc: enter command mode\(nevigation\)
  * \: Vi style file completion 



