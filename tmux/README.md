# tmux

## session

```bash
# generate session
tmux

# generate session with naming
tmux new -s [session_name]
tmux new-session -s [session_name]

# rewrite session name
[crtl] + b, $

# session detach
[ctrl] + b, d

# session list
tmux ls

# session attach
tmux attach -t [session number or session name]

# exit
exit

# exit session 
tmux kill-session -t [session_name]
```

## window

```bash
# generate window
[ctrl] + b, c

# generate session and window
tmux new -s -n

# rename window
[ctrl] +b, ,

# exit window
[ctrl] + b, &
[ctrl] + d

# move next window
[ctrl] + b, n

# move previous window
[ctrl] + b, p

# move last window
[ctrl] + b, l

# move specific window using number
[ctrl] + b 0-9

# move specific window using name
[ctrl] + b, f

# window list
[ctrl] + b, w
```

## pen

```bash
# split vertical
[ctrl] + b, %

# split horizontal
[ctrl] + b, "

# move pen using number
[ctrl] + b, q

# move pen in order
[ctrl] + b, o

# move pen using 방향키
[ctrl] + b, [방향키]

# delete pen
[ctrl] + d
[ctrl] + d, x

# pen resize
[ctrl] + b, z

# pen resize
[ctrl] + b, :, resize-pane -L or -R or -U -D

# change pen layout
[ctrl] + b, [spacebar]
```
