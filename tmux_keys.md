Kitty is the terminal. Check i3 for basic keybinds


Tmux keybinds works by doing 

press {prefix key}, release the key, wait, press next key.

The major prefix is Control+s 

Hence, you do: 

Ctrl+s, h           :   Horizontal Split (Panes)
ctrl+s, v           :   Vertical   Split (Panes)


Ctrl+s, x           :   Close/Kill pane.

---------------------------------------------
Will destroy the tab if it has only this pane
IT will also exit tmux if there's just one pane and tab.
Kitty is tied with tmux, so it will kill the terminal. Use kitty if you need

Ctrl+s, c           :   Create new tab/window
Ctrl+s, b/n         :   Move between tabs (before/next)

Ctrl+s, w           :   see existing tmux sessions. 
Then press enter to switch to it. NOTE: Using it to switch sessions is made nearly useless by Tmux-sessionizer


ctrl+s, t           :   Show Time 
ctrl+s, q           :   Show pane Number (Kinda useless)


Then there's the media player Control, like music or youtube video
-----------------------------
Ctrl+shift+n, arrow keys 
Ctrl+shift+n, numpad arrow keys 



----
# Tmux Sessionizer 
To switch between tmux sessions: 
Do: 
<C-k>, then type, use arrow key, and press enter. 


To configure which directory you can easily start a new session in modify 
~/.config/tmux-sessionizer-config/tmux-sessionizer.conf.bash 
and change 
```
TS_SEARCH_PATH=( 
...
# add a path on a new line
)
```
by adding the path to that dir in on a new line

Tmux sessionizer can also be used to send command to other existing tmux sessions.
Runner, Editor, and Debugger.  
Runner is a target to recieve commands. 

One terminal window is in the Editor session. 
Andother on second screen is in the runner session. 

From editor session, a keybind will send a command to the editor session. 
Commands like: Compile project, run it, do some test, send the code to the hardware, print the result... 

You need to create a build.sh script that does it. 

Then you'll need to ask me questions about the other stuff for more details on how to use it



