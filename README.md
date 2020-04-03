# nano-4.8 (modified)

**Ctrl + Backspace** is a modern keybinding that has already been widely supported in most browsers, text editors, search bars, file explorers, etc. However, the `nanorc` file has very limited adjustabily on keybindings, so it's time for us to compile it ourselves!

## How it works

1. From the [nanorc](https://www.nano-editor.org/dist/latest/nanorc.5.html) manual, it read that:  

   > If your terminal produces ^H for <Ctrl+Backspace>, you can make <Ctrl+Backspace> delete the word to the left of the cursor by rebinding ^H to this (chopwordleft) function.  

   - If this is your case, then congratulations! You can map `^H` to `chopwordleft` already.  
   - On some terminals, unfortunately, `<Backspace>` emits `^H`, while `<Ctrl+Backspace>` emits `KEY_BACKSPACE`.  
   *(Although some of the terminals allow you to change the keycode emitted by `<Backspace>`)*

2. In order to switch back the reversed mapping above, we need to be able to map the key `<Backspace>`.

   To do so, I added two keys in [global.c](https://github.com/davidhcefx/nano-4.8_modified/blob/9d730daa626df98deb55600e3f49573d1b37baad/src/global.c#L518-L567) that can be bound.  
   - `Bsp`: stands for `KEY_BACKSPACE`.
   - `^Bsp`: stands for `^H`, also known as `BS_CODE`.

3. After compilation, we could then put these lines in our `.nanorc`:  

   ```nanorc
   bind ^H backspace main
   bind Bsp chopwordleft main
   ```
   
   and finally make `<Ctrl+Backspace>` delete the word before the cursor! :)


## How to compile

*Please refer to [README.GIT](/README.GIT) for more details.*

1. Install the dependencies: `apt install autoconf automake autopoint gcc gettext git groff make pkg-config texinfo`

2. Run `./autogen.sh`.

3. After that, just do the normal `./configure` and `make; make install`.


## I am lazy

Here are some binary files I compiled within Docker. However, I don't guarantee they will work on YOUR machine! I suggest you compile it yourself in case something went wrong.

- [Ubuntu 18.04](/bin/ubuntu_18.04)
- [Ubuntu 16.04](/bin/ubuntu_16.04)
