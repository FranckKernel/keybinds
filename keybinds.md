Neovim top keybinds:

NOTE: first, because of a plugin called which key, if you just do a keybind press slowly, a list of all continuation will pop up, 
with a description. So you don't need to memorise this file 


Caps on keybinds and key combos are often used for 
1: Do more (bigger word, bigger search window, )
2:  Do it backward
You'll have to learn which is which. 

Generally, if backward makes no sense. then its just do more


--- 
# Basic navigation 

Arrow keys or
  i
j k l


to move cursor in normal mode 


arrow keys to move cursor in insert mode  (i j k l just types text in insert mode )


For a completely normy experience: Stay in insert mode the whole time, And use the mouse to navigate 


--- 
# Normal mode Basic navigation (also works in the other modes like Visual and Block Visual and replace) (not sure about replace, no one use it anyway)

L to go to end of line 
J to go to start of line (first non space character. Cause indentation)
_ to go to true start of line 

I to move cursor to top of page 
K to move cursor to bottom of page 
M to move cursor to middle of page 

zz to shift the page so the cursor (same line number and content) become at the center of the view port/page 
zt to shift ... become top of view port 
zb to shift ... become bottom of view port

gg : Go to top of file 
G: Go to end of file 


<number>gg go to line number (Absolute jump )
23gg : Go to line 23 

5<Up> jump 5 line above (Relative jump)
7<Right> jump 7 right (relative jump)
can use ijkl rather then directions arrows keys


q : Go to previous word (left)
e: Go to next word (right)
I kinda modified them, but you can spam q,e and move from end/start of word 
If at end of word and press e, go to end of next word 
if at start of word and press q, go to start of previous word 
else: 
go to start/end of current word

Q, E : Same but with big words (space only count as separation/word start/end. Not charaters like '.', ',', ':' ... )

% to find matching brackets , and teleport to the matching bracket. Put yout cursor on one bellow and press %

( {   }      )



Esc or jk to leave current mode and return to normal mode  

h to enter insert mode on cursor 
a to enter insert mode on cursor + 1 character to the right 
o to create a new line and enter insert mode on the new line bellow where your cursor was 

H to enter insert mode at the start of the line  
            (or To enter insert mode at cursor on all lines [if in visual block mode. Usfeul to edit multiple lines at once]) 
            ( but thats for later )
A to enter insert mode at the end of the line
        (Or one to the right in visual block mode, again for later)


v to enter visual mode (Selection mode). You can also use the mouse and drag click 
Ctrl+v or Ctrl+q to enter block visual mode (Select text, but vertically, )

r to enter replace mode for 1 charater
<leader>R to enter replace mode for multiple (a wacky rebind. Normally it would just be R. But since full replace mode is rare, it's fine)

c : replace but for combos (Will explain later, really useful)
Dont press c by itself
"Technically combos are called vim actions"


--- 
# Clipboard
Neovim has two clipboard, you can change it so it has one. Ask me how if you want to know how to. Or figure it out with ai. I prefer two. 
~/.config/nvim/lua/_before/options.lua. Search for clipboard
1: The neovim clipboard. It works for that one neovim process.  
			(NC) ^

2: The system clipboard. The usual ctrl+c and ctrl+v one. To put on discord, chatgpt, google ... 
			(SC) ^


System clipboard: 
Ctrl+c to copy selection (lower case work, it won't stop or kill neovim)
ctrl+V to paste 
Note the shift/Caps on V (ctrl+shift+v)


y : Copy selection to neovim clipboard 
d : Cut selection to neovim clipboard 
<backspace> : Delete selection  
x : delete character on cursor 

yy : Copy current line to neovim clipboard 
dd : Cut current line to nc 


p : paste neovim clipboard content (right of cursor)
P : paste neovim clipboard content (left of cursor)

<Space>C copy current line to system clipboard 

See later combos. Useful one : iw, ap, ... 

like diw, yiw, gUiw, ... ciw

<Space>fn : If you fuck up and accidentally overwrite the clipboard, this allow to pick a previous clipboard value
<!-- <leader>fn (leader = space . See later ) { this exist only to make searching easier } -->

---
# Useful navigation plugin (Flash) 


s (type some text) 
the screen goes gray 
type the letter thats in grey to teleport cursor there

f : Like s, but only forward 
F : like s, but only backward 

t : like f, but teleport cursor 1 left of said character 
T: like F but one Right of said character

---
# Telescope stuff

Telescope is the neovim picker with a preview window on the right, which file its from on the left, 
and what you are typing at the bottom. 

All keys who's name are more then 1 letter long are represented as <key name> 

example: 
<Space> 
<Up> 
<Backspace>
<Esc>
<leader>


<leader> = <Space> 
It's a prefix for a lot of stuff. A prefix is something you always do before the rest. 
Some people (nearly no one), use a different prefix, so <leader> is a variable, so change at one place, it changes everywhere else 
but me, and 99% of people just use <leader> = <space>

Like <Ctrl+s> is a prefix for tmux. 


So 
<leader>ff = <Space>ff 
Press space, then f, then f 

With that knowledge

<leader>ff : Telescope pick a file in current directory or deeper. Type the file, then arrow key, then enter and you'll be moved there 
<leader>fg : ... pick a string, useful if you want to know where in your project ABC is written, and want to navigate to that file at that location. 
it searches from current directory unward 

<leader>fF : like FF, but applies to the entire project, so it will search backward, rooted not at pwd (Current directory) but project root (where the .git file/directory is). 
Where you did git init 
<leader>fG : like <leader>fg, but whole project and deeper, not just current directory and deeper. 

Why ff and fg: 
ff uses fzf in default mode (Fuzzy search files)
fg uses rg in default mode (search content of files, and find which files has a match). 
For example, i downloaded novels. And I have chapter 1.txt, chapter 2.txt .... chapter 500.txt

And i want to know Where "Qui Gonn Jinn" appears cause I forgot who he is. 
rg "Qui Gonn Jinn", and i will see all matches. 
Then i find the first appearance, and i will read the text arround it, which has his physical description and context of introduction. 


Or in code, when you search for something that the LSP (see later can't find), then you can find where a variable, macro, function is created, declared, used... 

<leader>f1 or f2 or f3 : <leader>ff, but 1/2/3 directory backward
<leader>g1 or g2 or g3 : <leader>fg, but 1/2/3 directory backward


<leader>fz: Fuzzy search in current buffer (Better search, better Ctrl+f,allows typos, more intelligent search algorithm)

<leader>fb : like <leader>ff, but only for open buffers (Files that are opened in neovim)

<leader>fn : In the neovim clipboard, it's a history of everything you've pasted/cut since the start of the session. And allow you to cahnge your clipboard to it. 
Extremely useful, as a lot of deletion overwrite your clipboard


<leader>fo : Telescope recent files 



---
================================  LSP (The good shit)  Language Server Protocol: Does the same job as a Code Analysis tool, but not integrated.  
Basically, all language feature: 
Go to definition, peak definition, autocompletion, type information... depend on it


gd: Go to definition. Goes where the function is defined  (The one you use all the time). 
            Note: For C, for cross file gd, need bear -- build.sh -> compile_commands.json (Ask Ai if it applies and are curious)
## ^^ **Extremely useful ! **
gD: Go to Declaration. Where the function is declared (in c, thats for header files). Used more rarely. Just doing gd twice will do it too

Pair gd with Ctrl+o and ctrl+p (To undo and redo the jump caused by gd)


gf : Also really useful: 
if there's a filepath on your cursor, it will open that file. 

"$HOME/.config/nvim/init.lua" -- put cursor anywhere between the "" and press gf


gx: Same but for url website links. Put cursor on it, and press gx, and it will open the webpage on your default webbrowser


gw : (Technically, its just fzf, not lsp). 
Like doing <leader>fg, but it already write the current word to the buffer. 
When gd fails, use gw to search. 

ga : Like gw, slightly different, it will go untill left and right spaces. 


<!-- SMALL WORDS AND BIG WORDS DEFINITION -->
|   abc.xyz.123 

|     xyz     : small word 
| abc.xyz.123 : big word

gw with cursor on y: xyz 
ga with cursor on y: abc.xyz.123 
gA like ga, but in project, not just pwd
gW like gw, but search in the entire project, not just current pwd


-- These two are often broken
gi : Go to incoming calls (Those who are calling this function)
go : Go to outgoing calls (The function this function calls)


<leader>fu : Find the functions in this buffer
<leader>fs : All symbols in buffer (Symbols = variable + calss + functions + ...)
<leader>fS : like fs, but searches more


<leader>fk : List all neovim keymaps, helpful to search for keybinds i created. (Will not help with default keybinds)
<leader>fc : Change color theme (kinda useless)


<leader>dw, <leader>de : Find errors in code 
same with dW and dE, just for code in the project, not just in this file. 


## Very useful
<leader>Lr : Rename a symbol 



---
# NEOVIM command
To help you find this:
exit vim, quit vim, exit neovim, quit neovim,  leave vim, leave neovim 
exit nvim, quit nvim, leave nvim, close nvim, close neovim, close vim 



: enter neovim command 

:q quit 
:w save 
:a in combos (all files, not just current buffer) 

:wq save and quit (only save current file) 
:wa save all files
:wqa save all file and exit neovim 

why :w ? w-> write to file. 
A buffer: The content of the file on the ram used by neovim 
A file: The thing on disk 

for noobs, they are interchangeable 

## I end up doing :wa  and :wqa very often . It's like Ctrl+s in muscle memory

There's also a bunch of commands, for neovim stuff, and for plugins 

to execute lua code 

:lua <lua code> 


---- 
# Other useful stuff (Misc)

<leader>tt : Toggle side file manager
<leader>rr : Open lf in neovim 
<laeder>lf : Open lf in neovim 
<leader>lg: OPen Lazygit in neovim 
<leader>u : Toggle undotree (USeful to check the differences of undo/redo, and see the entire undo progression tree)
        ( Curently bugged, fuckeed with barbar, won't leave even when closed). Just open and close neovim


Closing and reopening is annoying, you need to reopen all files and get back to where you are: 


```bash 
rv
# or 
rv <file_path>
# can use a list of files 
rv f1 f2 f3 f4 ... 
```

This is a neovim with session and remote access. 

Basically, it saves which files are opened, where, in what order. 
So when you close neovim, you can do rv to return exactly where you where 

```bash
sv <file_path>
#or 
sv f1 f2 f3 ... 
```
from another terminal, which isn't inside neovim, so you have access to better global pc naviation, sv a file and it will open it in the 
termianl session

One rv can be opened at a time. 

for multiple, use 

rv, rv1, rv2, rv3 
and the corresponding sv


rv by itselfs open the last session as it was. 
rv with files will open the last session witht he file that was opened then and the files you gave


---
# Buffers


--- 
# Tmux like experience
Like with tmux, you can create and move from split. 
There's an integration so Ctrl+s, <Arrow key> or <ijkl> 
will move in and out. So you don't need to use another prefix for moving within panes and windows of neovim for most things 

Try using neovim, tmux and then crete splits inside neovim

For things you need to move through panes and windows, the prefix is Ctrl+w, not Ctrl+s (The tmux prefix)

--- 
# Combos / Vim actions 

y: Yank 
d: cut 
c: cut and enter insert mode (to replace the content)


y and d by itself : Applies on current selection. 

double tap: current line
yy: Copy current line
dd : Delete curent line


iw : current small word   
iW : curernt big word 

f,s,t : See flash plugin info

To cut current word on cursor diw (word ends at . : , and other such stuff)
to cut bigger word on cursor diW (big word end only at space)

same with yiw and yiW (copy current word, not cut)


ciw : delete current word, put it in clipboard, and move cursor to the start of where the word was (USeful to retype a word)


you can also use s,t and f 

df "type some text", type the green color match. 
ds, ... 
dt, ... 
and it will delete from where you where, to where your cursor moved. (see s,f,t)

same with y and c, but with y and c behavior. 




====== 
With simple keys, numbers work too 


5y : Copy 5 characters from here 
5yy : Copy 5 lines from here (total of 5 lines copied)

2dd: Delete this line and the line bellow

5D: cut 5 characters, but moving leftward (backward)



5<Left> 
<Left> means Left Arrow 

or 5j : Move cursor 5 to the left 

7i or 7<Up> move cursor 7 lines up 


9k : Same , 9 down 


so you can do d5l (delete 5 characters starting from cursor moving right)

cl :  delete 1 char and enter insert mode


for key combos. Note that $ is end of line, not L (Something i had to pay for due to trying to make it more intuitive. )
so delete from here to end of line: d$ 
$ is the og default go to end of line 
^ is the og start of line (You'll see these in regular expression and wildcards \[Both are a bash concept, but now more universal\])


So for complex combos, you might need to learn the og keybinds too. But that probably won't happen. 
only d$ is really useful imo



---- 
# Tmux integration and tmux like inside neovim 
## This is also a tmux recap
The Tmux prefix is Ctrl+w
The Vim prefix is ctrl+s

However for navigation, you can use Ctrl+s, and it will magically know to move between neovim, or neovim <-> tmux depending on your position. 
If you are are the border, if goes to the other, and if not, it moves within itself. 1 BUTTON USEFUL FOR BOTH PROGRAM!

Remembers: 
h: Create horizontal split 
v : Create vertical split 
x : close pane. If last pane in window, close window


c:  Create new window
b : Previous window
n : next window 
X : Close window

arrow keys, or 
   i 
j  k  l   : move focus to pane in that direction

So on tmux: 
Ctrl+s, h : create a horizontal split 
on Neovim 

ctrl+w, h : create a neovim split 


To close a pane in neovim, use :q , like to exit neovim 

Ctrl+s, # : Move to window #, 1-9 -> 1-9. 0->10


----
# Buffers

<leader># 
like 1-9 : Move to buffer # 
0 : Move to buffer number 10



<Ctrl+n> : Next buffer 
<Ctrl+b> previous buffer 


<leader>fb : Pick a buffer with telescope


<leader>N : Move buffer right (for buffer reordering)
<leader>B : Move buffer left (for buffer reordering)

<leader>q : Close buffer. 



# ----- End
debugger: 
<leader>d... and <leader>b...

Learn about them yourself

Neovim can have an integrated debugger in it
Though it can be a pain to setup. Some things need setup done in the project repo where you are debugging. 



-----
# To learn more stuff : 
check them with which keys. 

Recommend: Open a .py, .c, .lua or .sh file 
Sometime you might need other filetype for plugins used by that files. Preferably the plugin you want to learn about and its keybinds are loaded. 
scroll down, do zz (so the cursor is in the center of the page)

Make sure the terminal is full screened and the neovim window/pane is too 

Now you are ready to learn. 

To learn about keybinds that start with <leader>d:

press <leader>d then wait 
and look up the options 

For more info: 
<C-k> search nvim enters
v (enter neovim)
<leader>fg : start rip grep, 
search for the description string
finda  match, go to the file 
find which plugins its for 

copy nearby content to chatgpt, and ask question about plugins and what the keybind does exactly and what its for


