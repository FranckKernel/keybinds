I3 Key binds are the general keybinds, that always runs. i3 is the window manager. On windows, it would be part of the OS. 
Btw, I use the french canadian keyboard.


windows key = win = mod
left alt key = alt = mod2


Lots of simple window+1key works with alt+1key in case you fat finger


## win + enter             :   Open terminal (Kitty) with tmux.     Kitty is tied with tmux, exiting tmux will kill the terminal. 
win + <(left of enter)  :   Open terminal (Alacritty) (Another terminal, not inside tmux) Useful when kitty or tmux bugs/break
## win + ;                 :   Kill active window (Green border). Like Alt+f4. There's no (x) in the right corner {CLOSE ACTIVE WINDOW} {CLOSE WINDOW}
win + q/Q               :   Kill active window (Green border). Like Alt+f4. There's no (x) in the right corner
## win + f                 :   Toggle window full screen
## win + r                 :   Start/Stop windows resize, then win + arrows to change size


## win + d                 :   Open application launcher (rofi modified for wayland). Then type or use shift+left/right to change mode.
There's applications, executable programs, files and even active windows. 

win + F10               :   Lock the sessions. Then press backspace untill the whole circle is red. (To see theres nothing written)
--Then you can type the password and press enter

## Win+shift+r          : Reload the i3 configuration


For fat finger
## win + o/p               :   Open the powermenu (lock, logout, suspend (ram), hibernate (disk), reboot, shutdown) # IMPORTANT
win + c                 :   Open file manager
win + w                 :   Open firefox (Web browser)
win + W                 :   Open firefox (Web browser, Incognito mode)
win + t                 :   Open screenshot menu
win + u                 :   Open Volume menu
win + y                 :   Open ThunderBird (Mail)
win + b                 :   Open battery menu
win + Shift + b         :   Open brightness menu
win + m                 :   Open broken emoji menu (I should bind something useful to it)


Win+ctrl+t : Toggle top bar 
Win+Ctrl+b : Toggle bottom bar



----------------------------------
# Navigation

-- The arrow keys or left hand awsd
win + i/Up              :   Select window above
win + k/Bellow          :   Select window bellow
win + j/Right           :   Select window right
win + l/Left            :   Select window left

## win + e                 : Back to tiling window mode (useful if did space, g or s) 
win + space             : Floating Window mode 
win + g                 : Group window
win + s                 : Stack window (Like group, but different)
win + a/z               : Select window Parent/Child (Kinda useless i never really use it). For window one above another in toggling mode i think

## win + 1234567890        :   Switch to workspace (1-10)
## win + shift + number    :   Send active window to workspace (1-10)


alt + number            :   Same thing, but on different screen (11-20)
alt + shift number      :   Same thing, but on different screen (11-20)

alt+win + number        :   Same thing but for third screen
alt+win + shift+ number :   Same thing but for third screen

## win + h                 :   Next window created will be in Horizontal Split  (Left/Right)
## win + v                 :   Next window created will be in Vertical   Split  (Bellow/Above)




win+ctrl+n              :   Start default slideshow
win+ctrl+shift+k        :   Kill any slideshow


picture = {b,B, n,N, m,M}
alt+ctrl+picture               :   Set background picture   


# Music control and voluem control
win + m                 :   Music control Menu

win+ctrl+left           :   previous song
win+ctrl+right          :   next song
win+ctrl+up             :   play/pause song
win+ctrl+down           :   Stop playing song


alt + home/end          :   Volume up/down 1%
alt + shift + home/end  :   Volume up/down 5%

alt + page{up/down}     :   Music Volume up/down 1%
(With shift)            :   Music Volume up/down 5%


win + e                 :   Tiling window mode (Windows side to side)
win + g                 :   Tabbed window mode (Name appears top to bottom)
win + s                 :   Stack window mode (Name appears left to right)
win + shift + space     :   Toggle floating window
win + space             :   Switch between floating windows






