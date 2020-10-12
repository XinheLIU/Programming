### Modes

* Open Vim: vim or vim file path
* Normal Mode\(Command Mode\): when enter vim \("vim" in Command Line\) '
  * **&lt;Esc&gt; **from all other modes
  * every thing you enter is a command
* Line Mode : Press : under command mode
* Insert Mode : **&lt;i&gt; **under command line
  * :q to exist vim
* Replace Mode: **&lt;R&gt;**
* pipelines are effective

#### Nevigation Mode

##### Motions

* hjkl 
  * 0 - to the beginning of a line
  * ^ - to the first \(non-empty\) char
* w - move by word, b - move back by word
  * W, B - move without stop at punctuations
* l - move one char
* ctrl f b $ \(regular expression - to the end\) -PageUp and PageDown
* line number + gg or G - go to line
  * : + line number or $ - same function
  * gg move to beginning
  * G move to the end
* z move the view up
* Ctrl + g : display current line, cursor
  * = f\[ile\]
* Ctrl + i, o : jump to previous/next position
* Ctrl + \] jump into \(eg. in the help file\)
* f &lt;chars&gt; : **search** one line
  * F: search backward to first occurance
  * n : go to next 
  * N: go to previous
  * \[count\] f : find to the nth
* t : till \(go to the previous position if next find\)
  * T: 'till: reverse till
  * use combinations: dtw = df&lt;space&gt; 
* J: join lines
  * g J: join with no space added
* /&lt;words&gt; : find in the whole doc
  * ? &lt;words&gt; reverse find
  * \* : go to  next  indent - forward search
  * \#: go to previous indent - backward search
  * n : repeat search in the same direction
  * N : repeat search in the opposite direction

##### Commands

* \[count\] \[register\] &lt;Commands&gt;/ \[register\]\[count\]&lt;Commands&gt; : operation can be combined
* number\(\#\) + operation command : repeat \# times
  * 3d2w
* . - repeat the previous command
* u : undo 
  * Ctrl + r : redo
* d - delete / cut \(saved to** register\) = x**
  * dd -delete a line
    * \[count\] dd 
  * dw, dW- delete word, d3w -delete 3words
  * dl - delete one char\(x\)
  * dk, dj - delete current line the line above or below
  * dh - X
* y - yank \(copy\)
  * yw, y$
  * yy - yanks the entire line
* p - put \(after\)
  * P - put before
  * ddp, xp - swap words or line
  * place at the first empty space \(eg for line, the next line if current line is not empty\)
* &gt;, &lt; : indent and unindent
* g - plus other commands
  * J: join with no space added
  * ~ \[motion\] , ~~: change upper/lower case
  * uw, UW: upper case
  * -v: repeat the previous selection
* ##### Register
* :reg to show all registers

* " : the unnamed register

  * holds operations from d,c,s,x,y

* :0 :holds y \(yanked text\)

* "1 : d, c - deleted and changed

* "2-"9: keeps the past motions in the buffer

* "a - "z : named registers

  * "A-"Z: append in "a-"z registers 

#### Insert Mode

* i - enters into the mode 
  * I = ^ + i : insert on the first char place
  * \[count\] \[operations\]
    * 80 i &lt;char&gt; - insert 80 char, 5 o &lt;char&gt; insert similar 5 lines
* a : append at current cursor
  * A : append at the end of line
* o : insert in new line \(open below\)
  * O - open above
  * \[count\] o - open n lines
* s: substitute
  * S - substitute line
* \[Reg\]\[Count\] c \[motion\] : change \(eg. cw\) to register
  * C - change to the end = c$
  * cc - change line
* ~ : switch upper lower case
  * g ~~ = g ~$ : change case to the eol
  * gu\[motion\] change only upper cases : guu, guW
* J : join lines 

#### Replace Mode \(another kind of insert\)

* R - goes to the mode
* r - replace just one char

#### Text Object

* Use &lt;motion&gt;&lt;a or i &gt; &lt; Obj &gt;
  * **a** : "a" or around : the whole object
  * **i** : "innner" the content within 
* w \(words\), p \(paragraph\), s\(sentence\)
* block object 
  * {}, \(\), "", ' ',&lt;&gt;
* &lt;= or &gt;= for &lt;&gt;
* tag object
  * t for tag

#### Visual Mode

* &lt;enter visual mode&gt;&lt;motions/text objects&gt;&lt;commands&gt; : select then perform a command
  * any command will be performed on a block
* v: characterwise visual mode
  * o, O: move the cursor between ends\(or corner\)
* V: line wise visual mode
* Ctrl-v: blockwise visual mode
* ： enter command mode under visual mode will only perform on selected ranges
* g
  * gv: quickly reselect

#### Macro

* record a series of motions
  * q &lt;register&gt; to start
    * Capital &lt;Register&gt; to append
  * q to stop
  * @&lt;register&gt; to repeat
  * @@ to repeat again
* :&lt;range&gt; normal@&lt;register&gt; to repeat n times
* Save macro
  * in .viminfo /\_viminfo files \(never use register for other things\)
  * .vimrc/\_vimrc file
    * let @&lt;register&gt; = '&lt;macro content&gt;'

#### Line Mode

* :&lt;partial fill&gt; - use up error to look around
* : e ~/.vimrc
* :q to exit
  * **! **- force the command
  * :w - write , :wq - write and quit
* **:help** - get help
  * :help \[command/name\] -get the help of a command
    * help \[command start with\] + Ctrl d : list all commands match the pattern
      * tab : auto complete circle around
  * :h option-list : display all options
  * :h &lt;option&gt;: goes to the list of options you can select from
  * Ctrl +ww : keep the help window open while you are editing\(switch between windows\)
  * :q to quit
* :**set** &lt;options&gt;
  * set &lt;options&gt;! - turn on 
  * set &lt;options&gt;? - check option status
  * set - display not-default options
  * ruler - turn on ruler
    * set **no**ruler - turn off 
    * set ruler! - turn on/off
  * set wildmenu - when you circel around with tab
  * nu\[mber\] : the line count in vim
  * is : incremental search
  * hls\[earch\] : hightlight search
* :reg : show all registers
* :\[range\] :s/{pattern}/{string}/\[flags\] : **substitute command**
  * flags : g-replace all 
  * range : n:m or n,m
    * . : current, $:end, ^:begin 
    * % all
    * :/Global/,/Local/s/...: global search
    * :/Local/s/... local search
    * need to search for "/" : use "\/" or use another separator \(vim will figure out\), rg. :s\#/var/spool\#/usr/local\#
  * :%s/{patttern}/{string}/g - global subs
* :center \[col num\]: center text
* :right, :left: move text to
* :color to see all colors
* :ls buffer list

### Vim Settings

* .vimrc file , rc = run commands, as \_vimrc on Windows
* use " to comment
* common options\( set \)
  * history\(=\)
  * ruler
  * showcmd: show incomplete commands
  * wildmenu
  * scrolloff&lt;=n&gt;: keep n lines on top
  * hls\[earch\]
  * ignorecase, smartcase - ignore case during search, not ignore when uppercase included
  * backup - always have a backup
    * set bex=&lt;Something&gt;: decide the backup file extension
  * lbr - read line wrap
  * ai, si - auto indentation and smart indentation
  * bg=&lt;light/dark&gt; : set color fit a dark/light background
  * shiftwidth, tabwidth,noexpandtab : how much to indent 
  * list: see the space characteristics
  * hidden: whether ask to save before switching buffer
* map &lt;KEY&gt; &lt;KEY\_STROKES&gt;
  * &lt;BS&gt;, &lt;CR&gt; \(enter\) &lt;Enter&gt;&lt;Return&gt; &lt;Esc&gt;&lt;Space&gt;&lt;Up&gt;&lt;Down&gt;&lt;Left&gt;...&lt;tab&gt;&lt;Home&gt;&lt;pageUp&gt;&lt;C-X&gt;&lt;F1&gt;-&lt;F12&gt;
  * &lt;leader&gt;:  
    * let mapleader = "&lt;New\_KEY&gt;"
  * nmap, vmap,cmap,xmap: map under different modes
* :mkvimrc &lt;file\_name&gt; : run as vimrc file
* color &lt;color&gt;
  * customize by home/&lt;user name&gt;/.vim/colors or User/&lt;username&gt;/.vim/colors
* comment by "
* " vim:set ft=vim : set file type
  * also useful for ".c",".py",etc
  * 

#### Buffers

* vim &lt;file1&gt;&lt;file2&gt;/&lt;patterns&gt;: open multiple files, they will be in several buffers.
* :e or :edit &lt;file
* :buffers: show buffers \(or :ls or :files\)
* :buffer&lt;buffer num/buffer name/tab completion&gt;
* :b &lt;buffer name/buffer num&gt;
  * Tab completion
* * press space-contrl-d: give you the list
  * b!&lt;num/name&gt; to override before write
* :bnext/:bn: to next buffer
* :bprevious/:bp: move back buffer
* :bdelete/bd &lt;num/name&gt;:close the buffer
* Ctrl-^: switch to alternate buffer \(with \#\)
* :badd &lt;file&gt;: open a new file to buffer list
* :\[num\]bd or :bdelete: delete from the buffer list
  * :%bd -delete all \(% for special range selection\)
* :bufdo &lt;command&gt;: execute a command on every buffer 
  * eg global substitute
* :wall -write all
* :E or :explore : explore files and open
  * multiple windows
    * :hide: close current window
    * :only: keep only this one open
* :qall! -quit all



