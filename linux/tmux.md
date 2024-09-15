tmux is a way to open multiple terminals in one window, it essentially
group your terminals in sessions, you can create multiple windows inside
a sessions

# commands 

to see the tmux sessions:

```zsh
 tmux ls
```

to connect to a specific session:
```zsh
 tmux a -t 0
```
a == attach
0 == is the session name

to kill all sessions:
```zsh
 tmux kill-server 
```

# shortcuts

Create new window ==> Ctrl+b+c
Rename current window ==> Ctrl+b+,
List window ==> Ctrl+b+w
exit session without saving ==> Ctrl+d
Detach from session ==> Ctrl+b+d


