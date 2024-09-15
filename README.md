VIM Commands 
# SOME QUICKIES
## Indent
```
:set autoindent
:set smartindent     - It will increase the indent in a new block.
```
### Count
```
Ctrl + a - Increment counter integer value under cursor
Ctrl + x - Decrement counter integer value under cursor
```
## Clipboard
```
:/Crtr+R* - Paste system clipboard text into command line to search the same
:Ctrl+R 0 - Paste last yanked text in command line
```
## Browse
```
:bro[wse] ol[dfiles] - type the number and enter [press spacebar to view more files, note the of file num to edit, press q]
:ol[dfiles]  - show recent files list. To choose file n :e #&lt;n
:Vex d:\n (press tab) - open vertically split explorer showing d:/n... folders, press
:tabnew        - open a new tab for a new untitled [No Name] file
:browse tabnew - open a new tab with file open dialog
```
```
i       - Insert text from cursor
I       - Insert text from START OF LINE
a       - Append text at char AFTER cursor
A       - Append text at end of line
R       - Overwrite mode until ESC
C       - Change from cursor to end of line
H       - Move to top line in the current screen
M       - Move to middle line in the current screen
L       - Move to bottom line in the current screen
w,W     - move forward  by word, place cursor at beginning of word (W leaps over special chars)
b,B     - move backward by word, place cursor at beginning of word (B leaps over special chars)
e,E     - move forward  by word, place cursor at end       of word (E leaps over special chars)
ggVG    - Select all(gg - goto top of file; V - line select mode, G - goto end of file)
ggVG"*y - Select all and copy to system clipboard
"*yy    - yank/copy to system clipboard from cursor till EOL without new line
vty    - Select text till char before "" (closing quote) and COPY to vim clip. Useful"
to copy string values. Place cursor on 1st char after starting " quote and performing this.
vt"p    - Select text till char before " (closing quote) and PASTE from vim clip. Useful
to overwrite string values. Place cursor on 1st char after starting " quote and performing this.
v%      - select block of text enclosed within {},(), [], WHILE cursor is on opening {,(,[
*       - find next occurrence of the word under cursor
#       - find prev occurrence of the word under cursor
:'<,'>s/red/green/g - find/replace only within visual selected block of lines
first select lines in visual mode and press : it will automatically enter the
range '<,'> and then type the command s/red/green/g (replace red with green)
:s/\%Vold/new/g  - replace the text 'old' to 'new' ONLY WITHIN the VISUAL selection (using atom %V)
(the difference is here it doesn't include the whole line in start of visual or
of of visual select but exactly from the start/end character)
```
### CHANGE DEFAULT FONT
```
http://www.troubleshooters.com/linux/vifont.htm
gVim Edit --> Startup Settings
gVim74 will open _vimrc file from vim installation / user home folder)
From command mode type
:set guifont=*
this opens font dialog window
choose any font / size (e.g Lucida Console / size 12)
To make this default font from command line type
:set guifont?
you can see the font settings in vim command line something like below based on the font/size chosen

set gfn=Lucida_Console:h12:cANSI
or
set guifont=Lucida_Console:h12:cANSI
copy/paste the above like to _vimrc file to make this font change permanent
Note: any space after = in the command set gfn= should be escaped with a slash like
set guifont=Monospace\ 12
```

### CHANGE DEFAULT VIM COLOR SCHEME
Note the color scheme name as seen at gVim -- Edit -- Color Scheme   
open _vimrc file, add line   
colors slate   

TIP 1    
Create a line like ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ of 100 chars   
i~ESCx100p   <--       i for insert mode, ~ type this char, Press ESCAPE key, x cut char ~, type 100, p - paste times (100)   
i - Enter into insert mode   
    `-` type the required char (-) using which the line is made   
    <Esc>; - Escape back to normal mode from insert mode   
    x - Delete the char - (also copied to unnamed register ")   
    100 - repeat 100 times the the following command   
    p   - paste 100 times the char from unnamed register "   

TIP 2:    
Replace ALL comma `,` in a line with EOL (End Of Line)   
:%s/,/\r/g   

### MOVE AROUND
```
h, j, k, l - Move Cursor (left, down, up, right respectively)   
gj,gk      - Move Cursor down/up across same which is wrapped in the screen   
% - Move to associated ( ), { }, [ ] cursor SHOULD be on  ( ), { }, [ ]   
[( - Moves cursor to previous available parenthesis   
]) - Moves cursor to next available parenthesis   
[{ - Moves cursor to previous available bracket   
]} - Moves cursor to next available bracket   
H - Move to top line in the current screen   
M - Move to middle line in the current screen   
L - Move to bottom line in the current screen   
Ctrl E - scroll screen up   
Ctrl Y - scroll screen down   

w - Move forward word by word   
0 - (num 0) Move to beginning of line   
^ - Move to beginning of line with non white-space char   
$ - Move to end of line  
o - add a new line below current (caps letter O add new line above current line)   
A - append text at end of line   
J - join line   
Ctrl f - Next page   
Ctrl b - back page   
Ctrl d - down half page   
Ctrl u - up half page   
Ctrl l - refresh screen    
gg - Move to top of file  
GG - Move to end of file   
100G - goto line 100  
10| - goto column 10  
( - jump backward one sentence  
) - jump forward  one sentence  
{ - jump backward one paragraph   
} - jump forward  one paragraph  
e -  go to the end of the current word   
E -  go to the end of the current WORD   
b - go to the previous (before) word   
B - go to the previous (before) WORD   
w - go to the next word   
W - go to the next WORD   
WORD - WORD consists of a sequence of non-blank characters, separated with white space.   
word -  word consists of a sequence of letters, digits and underscores.   
Example to show the difference between WORD and word
192.168.1.1 - single WORD
192.168.1.1 - seven words.
Ctrl v - Block/Column selection mode
e.g
Select a block by pressing CTRL-v
(if you want to select 5 lines from a given column till end of line, after
Ctrl-v, press j 5 times to select 5 lines and $ to select till end of lines for those 5 lines)
Type I (Block Insert mode),
Edit the text. For example, if I wanted to prepend bullet points before each line type *
Press <Esc>
Watch as each line is prepended with *
to read about "Visual-block Insert" type :help v_b_I)
Ctrl q    - Block / column wise selection mode
Alt Mouse - Block / column wise selection mode (gVIM only)
(place cursor from where block select should be done
hold down ALT key, drag-select using mouse)
```
### SCREEN MOVEMENT
z.  Center the screen on the cursor   
zt  Scroll the screen so the cursor is at the top   
zb  Scroll the screen so the cursor is at the bottom   
Ctrl E - scroll screen up   
Ctrl Y - scroll screen down   


### BOOKMARKS
m{a-zA-Z} - mark cursor position   
`{a-z} - goto marked cursor position (line & column) only in current file (backtick key)   
{a-z} - goto marked line (cursor at the beginning of line) only in current file   
```
`{A-Z} - goto marked cursor position (line & column) only in current file (backtick key)    
{A-Z} - goto marked line (cursor at the beginning of line) in any file   
(you may be editing ten files. Each file could have mark a, but only one file can have mark A)      
' - goto previous line position and place cursor at the beginning of line(two single quotes key)   
`` - goto cursor position before the latest jump and place cursor exactly at previous line & column(two back ticks above tab key)   
(To jump to a mark enter an apostrophe (') or backtick (`) followed by a letter.l   
Using an apostrophe jumps to the beginning of the line holding the mark, while   
a backtick jumps to the line and column of the mark.)   
. - goto previously modified line   

```

### DELETE Commands
```
X  - backspace (backward delete char)
x  - forward delete char
dw - delete word
d$ - delete to end of line
dd - delete line (cut, p - to paste this)
U  - undo undo
u      - Undo (repeat to get to the oldest change)
Ctrl r - Redo (repeat to get to the latest change)

ce - change to end of word
c$ - change to end of line
~  - change case
```

### MACROS
. - repeat the last command   
^N - auto complete   
qa - record macro at a   
@a - replay macro a   

### GVIM STARTUP SETTINGS
Create ~/.vimrc file (In Windows GVim7.4 Edit->Startup Settings, will create _vimrc file.   
Enter the following commands in the file and save it.)   
"turn on auto numbering   
set num   
highlight search"   
set hls   
set incsearch   
"wrap text (line break)   
set lbr   
syntax on   
set guifont=Lucida_Console:h9:cDEFAULT   

### Command line to dynamically change TEXT WRAP 
:set wrap
:set nowrap

### SEARCH
/ - search forward   
? - search backward   
n - next match   
N - prev match   
`*` - Go to the next occurrence of the current word under the cursor.    
`#` - Go to the previous occurrence of the current word under the cursor.   
:noh - clear highlight or previous search (no highlight)   

### SPLIT VIEWS
:vsp - create vertical    split of current window   
:sp  - create horizontal  split of current window   
:Sexplore - browse by splitting a new horiz window   
:Explore - browse directory, o any file to open   
:Vexplore - Explore with vertical window   

### CUT/COPY/PASTE
v      - enter visual selection mode followed by use any movement commands to select text   
select block of text using h,j,k,l, $, } etc.,(any movement command)   
V      - visual select whole line (ref. MOVE AROUND sec. here for more details)   
Ctrl-v    - Block / column wise selection mode   
Ctrl-q    - Block / column wise selection mode   
Alt+Mouse - Block / column wise selection mode   
(place cursor from where block select should be done   
hold down ALT key, drag-select using mouse)   
y - copy/yank   
x - cut   
p - paste   
yVj - copy 2 lines (V select current and each j after that selects consecutive lines)   

COPY NON-CONSECUTIVE MULTIPLE LINES INTO A REGISTER
To copy 2 lines into register a   
aY - one line is copied into register ""a (Y is synonym for yy - yank line)"   
"AY - after moving to a different line, append this line to register a   
(referring register in capital appends instead of over writing)   
ap  - this pastes 2 lines copied as above"   

### COPY A HTML TAG BLOCK / FRAGMENT
vat    - Place the cursor on tag say <FONT>..</FONT> and then type this command.   
Selects full block including <FONT>..</FONT>   j   
vit    - While the cursor in on inner text of an html tag block type this.   
cat, cit, yat, yit --- try all this similarly   
e.g for the tag <FONT>my sample text</FONT>   

typing vit while cursor is on m of my selects the text 'my sample text'   
vat    - for the above same example selects the whole <FONT>my sample text</FONT> fragment   

yiw    - yank inner word (copy word under cursor, say "first")   
...      Move the cursor to another word (say "second")   
viwp   - select "second", then replace it with "first"   
...      Move the cursor to another word (say "third")   
viw"0p - select "third", then replace it with "first"   

vg_y   - yank/copy to vim clipboard from cursor till EOL without new line   
vg_"*y - yank/copy to system clipboard from cursor till EOL without new line   
"*yy   - yank/copy to system clipboard from cursor till EOL without new line   

ay  - register 'a' copies text already selected ( using v(visual mode) command)"   
"ayy - register 'a' copies(yanks) current line   
ap  - register 'a' contents pasted"   

s - substitute (cut/paste)   
R - Replace(overwrite) mode until ESC   
r - replace single char   

### Multiple clipboards using registers a-ZA-Z
e.g 
"fy - copy  firstname to   register f (after selecting firstname in visual mode)      
ly - copy  lastname  to   register l (after selecting lastname in visual mode)"   
"fp - paste firstname from register f (after selecting the text to be overwritten if needed)   
lp - paste lastname  from register l (after selecting the text to be overwritten if needed)"   

### PASTE IN INSERT MODE
1. Get into insert mode using any commands like i, a, A etc.,
2. press Ctrl R" (Press Control R and ") at the place you want to insert text from last yank/copy
   or
   press Ctrl R* (Press Control R and *) at the place you want to insert text from SYSTEM clipboard
   or
   press Ctrl R<a-zA-Z> (Press Control R and any register that has saved text)

NOTE: " (quote) is register command and Ctrl R automatically gets into read from register mode   
notice the " char at cursor position) once you press Ctrl R, which means we   
need to press only the register a-ZA-Z from which we need to read the text from.   
- register always has the latest/last yanked text   
  "*  - has the SYSTEM clipboard text   
  a-zA-Z - has user stored texts in registers a though z or A through Z   

### SYSTEM CLIPBOARD
`*`    represents system clipboard"
       "*yy  - copies current line to system clipboard   
       *p   -  pastes content from system clipboard"   
       e.g      
       v$"*y - enter visual mode, select till EOL and copy to system clipboard   
       v}"*y - enter visual mode, select paragraph and copy to system clipboard     

:wa       - save all files  
:xa       - exit all saving changes   
ZZ        - close and exit  
:bufdo bd - close all buffers   

:b 1 - switch to buffer 1   
:b <Tab>       - offers all buffers in a menu ( :b is short cut of buffer)   
:b car<Tab>    - offers car.c car.h etc., from buffers   

:b! 2) would allow to hide buffer 1 (keeping its changes), and display buffer 2   
Set the hidden option (:set hidden) so any buffer can be hidden (keeping its changes)   
without first writing the buffer to a file. This affects all commands and all buffers.   
Set the confirm option (:set confirm) so that when you tell Vim to abandon a buffer but   
you have unsaved changes, Vim will ask you whether to save your changes first, abandon them,   
or cancel the action. The choices given do not seem to allow simply hiding the buffer as in the previous options.   
Set either the autowrite or the autowriteall options (:set autowrite or :set autowriteall)   
to automatically save any changes made to the buffer before it is hidden.   

vim -p file1.txt file2.txt  - open multiple files   
:tabs      - list all tabs   
:tabm0     - move to first tab   
:tabfirst  - move to first tab   
:tabm      - move to last tab   
:tablast   - move to last tab   
:tabn      - move to next tab   
gt         - move to next tab   
:tabT      - move to previous tab   
gT         - move to previous tab   
0gt or 1gt - move to first tab   
:tabclose  - close current tab   
:tabonly   - close all other tabs except current   

### FIND & TILL
fx  - find next x   
Fx  - find prev x   
tx  - find next x but just before x   
Tx  - find prev x but just after x   
;   - Repeat latest f, t, F or T [count] times   
,   - Repeat latest f, t, F or T in opposite direction [count] times     
dtx - delete till x   
dfx - delete till and including x   
ctx - change till x   
cfx - change till and including x   


:g/pattern/command - apply command to all matches for the pattern   
e.g   
:g/temp/d - delete all occurrences of the word temp   
`:1,$/^#/d - delete all lines starting with # (1,$ is equal to g)   `   
:g!/^#/d  - delete all lines NOT starting with #   
:5,10m0   - move lines 5 to 10 above 1st line of file   

### FIND/REPLACE ONLY WITHIN VISUAL SELECTED LINES
When text is visually selected, press : to enter a command.   
The command line will automatically enter the range:   
:'<,'>   
:'<,'>s/red/green/g   

```
NOTE:
<  visual selection automatically bookmarks <u>start line</u> in the key <
>  visual selection automatically bookmarks <u>end   line</u> in the key >   
`<  (back tick key above tab) visual selection automatically bookmarks <u>start character</u> in the key <   
`>  (back tick key above tab) visual selection automatically bookmarks <u>end   character</u> in the key <   

(only the access key ' and ` is different for LINE and CHARACTER position bookmark as they both   
are bookmarked using < and > registers   
```
gv  - command selected the last visual selection made (using the above bookmark key)   

### FIND/REPLACE ONLY WITHIN VISUAL SELECTED TEXT
The substitute(s command) by default works on line mode search. To consider find/replace <u>ONLY within   
the characters</u> visually selected, Autom %V is used    

:s/\%Vold/new/g  - replace the text 'old' to 'new' ONLY WITHIN the VISUAL selection   
(using atom %V, \before % is escape char)   

### FIND/REPLACE WHOLE WORD AND DON'T MATCH PARTIAL TEXTS
Original Text: This is his idea   
enclose the word to be matched within \< and \>   
:s/\<his\>/her/   
Translated Text: This is her idea   
(Note: if \< and \> weren't used the the his in the word 'This' also would have   
got changed)   

### FIND MULTIPLE WORDS USING REGEX WORD AND REPLACE</b>
Original Text: Linux is good. Life is nice.   
:%s/\(good\|nice\)/awesome/g   
Translated Text: Linux is awesome. Life is awesome.   

### FIND/REPLACE TO PREFIX LINE NUMBER> IN ALL LINES
:%s/^/\=line(".") . ". "/g   

### FIND/REPLACE TEXT HAVING SPECIAL CHARACTERS

Original Text: c:/windows/system32/   

%s!/!\\!g   

Translated Text: c:\windows\system32\   

NOTE: Here we are using ! as argument separator instead of / in the substitute(s) command   
first \ in \\ is for escaping   

### FIND/REPLACE

:%s/fff/rrrrr    - % represents whole file   
- for all lines in a file, find string fff and replace with rrrrr only for 1st occurrence   
  :%s/fff/rrrrr/g  - replace all occurrences   
  :%s/fff/rrrrr/gc - replace all with confirmation   
  :%s/fff/rrrrr/gi - ignore case   
  :'a,'bs/fff/rrr/gi  - for lines between line marked "a" (ma) and marked "b" (mb)   
  :5,20s/fff/rrrrr/gc - for all lines between 5 and 20   
  :%s/*$/ - for all lines in a file, delete blank spaces at end of line   
  :%s/\(.*\):\(.*\)/\2:\1/g  - for all lines in a file, move last field delimited by ":" to the first field. <br>Swap fields if only two   
  :%s#<[^>]\+>##g - find and remove all HTML tage but keep the text contents   
  :%s/^\(.*\)\n\1$/\1/ - find and remove all duplicate lines   

Find/Replace in ALL files   
The following performs a search and replace in all buffers (all those listed with the :ls command):   
:bufdo %s/pattern/replace/ge | update   
(use :wa to save all buffers after the changes)   

If you don't wish to save the results of your replacement, but want to review each changed <br>buffer first, you can force the bufdo to   

continue without saving files with bufdo!:   
:bufdo! %s/pattern/replace/ge   

Find/replace is in both current directory and all sub-directories for given set of file extensions    
:arg **/*.cpp   - All *.cpp files in and below current directory.   
:argadd **/*.h   - And all *.h files.   
:arg           - Optional: Display the current arglist.   
:argdo %s/pattern/replace/ge | update    - Search and replace in all files in arglist   

Replacing current word (under cursor) if all files   
:arg *.cpp  All *.cpp files in directory.   
:argadd *.h  And all *.h files.   
...  Move cursor to word that is to be replaced.   
*  Search for that exact word.   
   :argdo %s//replace/ge | update  Search and replace in all files in arglist.   

### SORTING
:'a,'b !sort   - sort block of lines between and including marked by ma and mb   

### REVERSING LINES
:'a, 'b !tac     - reverse of order of lines in the block marked ma and mb   
:r !!date - replace with date by executing shell command date ( 2 exclamations required in windows)   
:sh  - open a shell   
:exit  - exit back to vim   

### TEXT OBJECT
is, as - represent text object (sentence),   
- is ignores spaces   
- as includes space   
  e.g.,   
  das  - delete current sentence including spaces   
    - da**s** where **s** is text object sentence    
    - da**w**, where w is word   
      caw - change all word (all here means if cursor is middle the word full word will be changed (all these text object based commands are very useful)   
      ci' - change inner text eclosed withing ' (single quotes   
      ci" - same as above for double quotes. applies for all of < ] ) }   
      similarly for di', yaw' etc.,   


### USING COMMANDS FROM HISTORY
type : and pres up/down arrow to pick from recent list. This method allows to edit the command before using it   
q:      - (type in normal mode) lists command history in [Command Line] window    
use movement keys j,k to locate the command to run and press ENTER   
- CTRL C for command line of [Command Line] window   
- Another CTRL C to quit from [Command Line] window     
  :his    - lists the command history,    
  :his /  - lists the history of searches made    

### GENERAL INFO / ISSUES
### q1. p(paste) command automatically yanks(copies) text being replaced and hence next p doesn't paste    
what was originally yanked(copied).   
- Use registers to paste multiple time. For effectiveness use multiple registers.    
Like for example   
"""fy - copy firstname to register f (after selecting firstname in visual mode)   
      ly - copy lastname to register l (after selecting lastname in visual mode)"   
"""fp - paste firstname from register f(after selecting the text to be overwritten if needed)   
      lp - paste lastname from register l(after selecting the text to be overwritten if needed)"   

### :reg - view all registers   

There are nine types of registers:   *registers* *E354*     
1. The unnamed register ""   
2. 10 numbered registers "0 to "9   
3. The small delete register "-   
4. 26 named registers "a to "z or "A to "Z   
5. four read-only registers ":, "., "% and "#   
6. the expression register "=    
7. The selection and drop registers "*, "+ and "~   
8. The black hole register "_   
9. Last search pattern register "/    

### q2. Commonly used short-cut keys in any editor
http://vim.wikia.com/wiki/Using_standard_editor_shortcuts_in_Vim   
Open LAST VIM Session   
1. While VIM has multiple files opened in many tabs save this session   
:mksession d:\vim_session   
2. Open gVim74.exe -S D:\vim_session (update gVim exe shortcut link target with -S session_file   

### ENCRYPTING FILE WITH PASSWORD
:X   
will ask to enter the password twice   
:w d:/encrypted_file.txt (will save the file encrypted)    
Close VIM application fully   
Open the VIM and open the file  d:/encrypted_file.txt   
VIM will ask for the password to decrypt the file   
NOTE: closing and opening the file in the same VIM application session will NOT ask for the password to be entered again.   

_vimrc (.vimrc) settings   
set autoindent   
set smartindent   
set fileencoding=utf-8    
set fileencodings=ucs-bom,utf8,prc   
set encoding=utf-8    
set guifont=Lucida_Console:h12:cDEFAULT    
set tabstop=4        " The width of a TAB is set to 4.    
set shiftwidth=4     " Indents will have a width of 4.    
set softtabstop=4   " Sets the number of columns for a TAB.   
set expandtab       " Expand TABs to spaces.   
set nu   
set ic   
set tw=0    "text width unlimited (doesn't break at 80th col to next line   
set nowrap   

### :marks - list of marks    
ma - set current position for mark A   
`a - jump to position of mark A   
y`a - yank text to position of mark A   
set multiple paths in vim for use with :find command   
alt E - start up settings (_vimrc)   
add lines   
set path-=c:/ns/ - is to remove any old paths   
set path+=F:/BACKUP/ += appends path to vim search path to use with :find   
:ls list all files in buffers   
:b1 open file numbered 1   
:bn swith to next buffer   
:ball open all files   
:bw write and close buffer and remove from :ls list   
:buffers list all buffers   

:2bw write and close 2nd buffers as noted from :buffers command   

While in edit mode   
Ctrl-r "*pastes system clipboard   
Ctrl-r "0 pastes last yanked word   
Check :reg to see all register and use any from the list after Ctrl-r   

### Vim sessions   
:mksession ~/mysession.vim   
Then later you can source that vim file and you'll have your old session back:    
:source ~/mysession.vim    
or open vim application with the -S option:    
$ vim -S ~/mysession.vim   
5. number followed by dot – repeat last vim command 5 times    


### Delete leading spaces
g/^\s*$/d   
:[range]g/pattern/cmd    


### Insert Line Numbers
Select the lines that needs numbering to be inserted   
(to select lines press V and then j repeatedly to select as per the number of lines to be select)   
enter in command line   
:'<,'>s/^/=(line(".")-line("'<")+1).' '   



### :marks - list of marks   
ma - set current position for mark A   
```
`a - jump to position of mark A   
y`a - yank text to position of mark A   
```
set multiple paths in vim for use with :find command   
alt E - start up settings (_vimrc)   
add lines   
set path-=c:/ns/ - is to remove any old paths   
set path+=F:/BACKUP/ += appends path to vim search path to use with :find   
:ls list all files in buffers   
:b1 open file numbered 1   
:bn swith to next buffer   
:ball open all files   
:bw write and close buffer and remove from :ls list   
:buffers list all buffers   
:2bw write and close 2nd buffers as noted from :buffers command   
While in edit mode   
Ctrl-r "*pastes system clipboard    
Ctrl-r "0 pastes last yanked word    
Check :reg to see all register and use any from the list after Ctrl-r   
### Vim sessions   
:mksession ~/mysession.vim   
Then later you can source that vim file and you'll have your old session back:   
:source ~/mysession.vim   
or open vim application with the -S option:   
$ vim -S ~/mysession.vim   

5. number followed by dot – repeat last vim command 5 times   