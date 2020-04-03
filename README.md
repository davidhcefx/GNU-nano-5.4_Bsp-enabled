# nano-4.8 (modified)

**Ctrl + Backspace** is a modern keybinding that has already been widely supported in most browsers, text editors, search bars, file explorers, etc. However, the nanorc file has very limited adjustabily on keybindings, so it's time for us to compile it ourselves!

## How it works



## Compile

- Please refer to [README.GIT](/README.GIT).
1. Install the dependencies: `apt install autoconf automake autopoint gcc gettext git groff make pkg-config texinfo`
2. Run `./autogen.sh`.
3. After that, just do the normal `./configure` and `make; make install`.

## Binary file

Here are some binary files I compiled within Docker. However, I don't guarantee they will work on YOUR machine! I suggest you compile it yourself in case something went wrong.

- [Ubuntu 18.04](/bin/ubuntu_18.04)
- [Ubuntu 16.04](/bin/ubuntu_16.04)
