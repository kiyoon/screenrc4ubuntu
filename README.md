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
- Ctrl+a + \<number\>: jump to the window number

## Detach and resume
- Ctrl+a + d: detach screen
- `screen -r`: resume screen
- `screen -r \<number\>`: resume screen (specified by the number)
- `screen -r -d`: detach and resume screen. Use it when above fails.

## Divide
- Ctrl+a + |: divide screen (vertical)
- Ctrl+a + S: divide screen (horizontal)
- Ctrl+a + \<Tab\>: move between divided screen
- (Custom binding) Ctrl+a + \<ArrowKey\>: move between divided screen
- Ctrl+a + X: close divided screen

## Copy / scroll
- Ctrl+a + \<ESC\>: Copy mode (to scroll)
- In copy mode, \<Space\> to select region. \<Space\> again to copy.

## Other tips
- If you press Ctrl+s by mistake, it will freeze. Ctrl+q to unfreeze.
