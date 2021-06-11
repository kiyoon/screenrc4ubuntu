# screenrc4ubuntu
.screenrc file for ubuntu

# Useful screen commands

## Create and navigate
- Ctrl+a + c: create window
- echo $WINDOW: see window number
- exit: exit window
- Ctrl+a + n: next window
- Ctrl+a + p: previous window
- Ctrl+a + \<number\>: jump to the window number

## Detach and resume
- Ctrl+a + d: detach screen
- screen -r: resume screen
- screen -r \<number\>: resume screen (specified by the number)
- screen -r -d: detach and resume screen. Use it when above fails.

## Divide
- Ctrl+a + |: divide screen
- Ctrl+a + \<Tab\>: move between divided screen
- Ctrl+a + X: close divided screen

## Copy / scroll
- Ctrl+a + \<ESC\>: Copy mode (to scroll)
- In copy mode, \<Space\> to select region. \<Space\> again to copy.

## Other tips
- If you press Ctrl+s by mistake, it will freeze. Ctrl+q to unfreeze.
