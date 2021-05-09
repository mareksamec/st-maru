# st-maru
My build of st (stimple terminal by suckless)
https://st.suckless.org/


WORK IN PROGRESS
### Update 2021-05-09:
- I have reworked this build and based it on more recent patches and last st stable release [0.8.4](https://dl.suckless.org/st/st-0.8.4.tar.gz).
- The keyboard shortcuts in this repo are now vanilla st keyboard shortcuts. Feel free to adjust them


## Info
This simple build is based on st version 0.8.4 (original version can be downloaded here from the official suckless website https://dl.suckless.org/st/st-0.8.4.tar.gz )

These st patches are included in the build for convenience:

- **keyboard-select** - enabled urxvt like keyboard selection in the terminal
- **scrollback** - Enables scrollback in suckless terminal with mousewheel support.
- **clipboard** - selection is automaticaly copied to the main clipboard
- **alpha** - Terminal supports transparency (you will need some compositor like picom or compton)
- **xresources** - You can configure colors, transparency, termname, cursor and other things in .Xresources. In case of problems see Troubleshooting below


## Keyboard shortcuts
* **Scrollback**: Shift + Page Up/Page Down  or mousewheel
* **Start keyboard movement mode:** Ctrl + Shift + S
	* move with h, j, k, l
	* toggle/untoggle select mode: s
	* input mode and search up/down: / or ?
	* copy selection and quit selection mode (keep selection highlighted): Enter
	* copy selection and quit selction mode (no highlight): Esc

Other keyboard shortucts from keyboard_select patch remain unchanged, see:
https://st.suckless.org/patches/keyboard_select/

## Mouse
- Mouse selection is automatically copied to the PRIMARY clipboard
- Use right click to paste (yes putty style paste is enabled)

Set the paste to middle-button:

Open up config.h in your favourite editor and change the button to here to Button2:
```c
static MouseShortcut mshortcuts[] = {
	/* mask                 button   function        argument       release */
	{ XK_ANY_MOD,           Button3, selpaste,       {.i = 0},      1 },

```
Now recompile with:
```
sudo make clean install
```

## Compiling and installing
- Just go to the repo folder and run `make` to compile.
- To install run `sudo make install`


## Troubleshooting
**tput errors at start** -  You might need to add some variables to your ~/.Xresources file you can use sample variables in the file `Xresource_sample`. Don't forget to run `xrdb -merge ~/.Xresources` to merge the changes. After that recompile st.

**When you ssh into a server it complains that the "terminal is not fully functional"** - Check if terminfo was correctly added for your user. If not, go to the repo folder and run `tic -sx st.info`
