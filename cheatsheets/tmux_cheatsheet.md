# Tmux cheatsheet  

My personal cheat sheet for **[tmux](https://github.com/tmux/tmux/wiki)**, one of my favorite tools. Tmux is a terminal multiplexer that can be detached and later reconnected to, which gives you the ability to "run things on the background" on a remote server.  

## Starting sessions:  
```
tmux                       # start a new session
tmux new -s myname         # start a new session with a specific name
```

## Interacting with tmux sessions using "bind-key" shortcuts  
Within a tmux session, press **control** + **b** (the default "bind-key") then the following shortcuts
| shortcut | description                 |
| -------- | --------------------------- |
| d        | detach from current session |
| [        | enter copy mode             |
| q        | quit copy mode              |
| ?        | list all shortcuts          |


## Session management:  
```
tmux ls                    # list exisiting sessions
tmux a -t myname           # attach to exisiting session named myname
tmux kill-ses -t myname    # kill session named myname
```

## Resources:
- Michael Lihs's **[tmux shortcuts & cheatsheet](https://gist.github.com/michaellihs/b6d46fa460fa5e429ea7ee5ff8794b96)**
- Andy Acer's **[tmux cheatsheet](https://github.com/andyacer/tmux-cheatsheet)**
