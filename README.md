# screenrc4ubuntu
The .screenrc file that enables intuitive GNU screen UI & commands.  
Unlike what the name says, it's not only for Ubuntu, but also for any OS really.

![Example screen](https://user-images.githubusercontent.com/12980409/123901028-2ba50b80-d9a5-11eb-9332-5bba6285c76b.png)


Make symbolic link in the home directory.  

```bash
cd ~
ln -s /path/to/screenrc4ubuntu/.screenrc
```




# Useful screen commands

First of all, launch screen: `screen`

## Create and navigate
- Ctrl+a + c: create window
- `echo $WINDOW`: see window number
- `exit`: exit window
- Ctrl+a + n: next window
- Ctrl+a + p: previous window
- Ctrl+aa: toggle two windows
- Ctrl+a + \<number\>: jump to the window number
- Ctrl+a + A: change window title
- Ctrl+a + :number \<number\>: change window number

## Detach and resume
- Ctrl+a + d: detach screen
- `screen -r`: resume screen
- `screen -r <number>`: resume screen (specified by the number)
- `screen -r -d`: detach and resume screen. Use it when above fails.

## Divide
- Ctrl+a + |: divide screen (vertical)
- Ctrl+a + S: divide screen (horizontal)
- Ctrl+a + \<Tab\>: move between divided screen
- (Custom binding) Ctrl+a + \<ArrowKey\>: move between divided screen
- Ctrl+a + X: close divided screen
- Ctrl+a + :resize -h 30%: set width of the divided window to 30%. (if you drop %, it will be line number)
- Ctrl+a + :resize -v 30%: set height of the window to 30%. (if you drop %, it will be line number)

## Copy / scroll
- Ctrl+a + \<ESC\>: Copy mode (use vim commands to scroll)
  - Ctrl+f: page down (front page)
  - Ctrl+b: page up (back page)
  - Ctrl+d: half page down
  - Ctrl+u: half page up
- In copy mode, \<Space\> to select region. \<Space\> again to copy. Then Ctrl+a + ] to paste.

## Kill window / session
- Ctrl+a + k or Ctrl+a + :kill : kill window
- Ctrl+a + \\ or Ctrl+a + :quit : kill all windows and quit session 

## Other tips
- If you press Ctrl+s by mistake, it will freeze. Ctrl+q to unfreeze.
- On a nested screen, use Ctrl+a + a + \<command\>.
- `screen -X eval "chdir $PWD"`: change default directory for new windows.

# Advanced: scripting with screen
- `screen -dmS <session_name>`: create a session in detached mode.
- `screen -S <session_name> -p <window> -X screen`: create window in the session.
- `screen -S <session_name> -p <window> -X stuff "command\n"`: execute command in the window session.
- `screen -S <session_name> -p <window> -X kill`: kill window
- `screen -S <session_name> -X quit`: kill all windows and quit session

## Example: run batch job

Below will create 3 windows and run python commands like:  
- `CUDA_VISIBLE_DEVICES=0 python train.py --arg 1`
- `CUDA_VISIBLE_DEVICES=1 python train.py --arg 2`
- `CUDA_VISIBLE_DEVICES=2 python train.py --arg 3`

```bash
#!/bin/bash

sess="session_name"

screen -dmS "$sess"

for window in {0..2}
do
    # Window 0 already exists so don't make it again
    if [ $window -ne 0 ]
    then
        screen -S "$sess" -X screen $window
    fi

    command="CUDA_VISIBLE_DEVICES=$window python train.py --arg $((window+1))\n"
    screen -S "$sess" -p $window -X stuff "$command"
done
```
