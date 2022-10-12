# tmux
## script your tmux-session
If one is like me and wants a tmux-session an a certain machine to look the same and have the same open windows for specific folders and with some initial command, then you can use this template for a shell-Script to do that for you. It will create (if needed) and attach to a tmux session with the defined name and populate it with the defined windows in defined folders and execute an initial command: 

```shell
#!/bin/sh

# Set Session Name
SESSION="mycustomname"
SESSIONEXISTS=$(tmux list-sessions | grep $SESSION)

# Only create tmux session if it doesn't already exist
if [ "$SESSIONEXISTS" = "" ]
then
    # Start New Session with our name
    tmux new-session -d -s $SESSION

    tmux rename-window -t 0 'tab-1'
    tmux send-keys -t 'tab-1' 'cd /to/my/folder/1/' C-m  'clear' C-m 'echo tab-1' C-m

    tmux new-window -t $SESSION:1 -n 'tab-2'
    tmux send-keys -t 'tab-2' 'cd /to/my/folder/2/' C-m  'clear' C-m 'echo tab-2' C-m

    tmux new-window -t $SESSION:2 -n 'tab-3'
    tmux send-keys -t 'tab-3' 'cd /to/my/folder/3/' C-m  'clear' C-m 'echo tab-3' C-m

    # repeat for all needed windows
fi

# Attach Session, on the Main window
tmux attach-session -t $SESSION:0


```
## Links
- [tmux cheatsheet](https://tmuxcheatsheet.com/)