# st-maru
My build of st (stimple terminal by suckless)
https://st.suckless.org/


WORK IN PROGRESS
### Update 2021-05-09:
- I have reworked this build and based it on more recent patches and st releases.
- The keyboard shortcuts in this repo are now vanilla st keyboard shortcuts. Feel free to adjust them


## Info
This simple build is based on st version 0.8.4 (original version can be downloaded here from the official suckless website https://dl.suckless.org/st/st-0.8.4.tar.gz )

These st patches are included in the build for convenience:

- **vertcenter** - Just a cosmetic change to vertically center lines if larger chscale is set in config (https://st.suckless.org/patches/vertcenter/)
- **keyboard-select** - enabled urxvt like keyboard selection in the terminal
- **st-font2** - Allows settings of the second font in config.h (for special characters in airline/powerline or emoji)
- **scrollback** - Enables scrollback in suckless terminal.



## Keyboard shortcuts
* **Scrollback**: Shift + Page Up/Page Down
* **Start keyboard movement mode:** Ctrl + Shift + S
	* move with h, j, k, l
	* toggle/untoggle select mode: s
	* input mode and search up/down: / or ?
	* copy selection and quit selection mode (keep selection highlighted): Enter
	* copy selection and quit selction mode (no highlight): Esc

Other keyboard shortucts from keyboard_select patch remain unchanged, see:
https://st.suckless.org/patches/keyboard_select/

## Mouse
Mouse selection is automatically copied to the SELECT clipboard
~~Use right click to paste (yes putty style paste is enabled)~~

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

## TODO:

