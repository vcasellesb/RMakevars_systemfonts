# RMakevars_systemfonts
## ~/.R/Makevars required to compile systemfonts from source on a brew-installed r

For me, the problem was manyfold. First, you need to point the C/C++ compilers to the libraries and *includes* that it needs. For me, since I had used brew to install r, they were in homebrew's path. That led me to think that I needed to use my brew-installed gcc-14 compiler, but that was a dead end. It's better to use Apple's clang/clang++. Then, OBJC is to install `FontManagerMac.mm`, which requires C++17 but I don't know why the installation process does not account for it if you've used homebrew.

If I have not made any mistakes, you should put this repo's Makevars in $HOME/.R/ and then installing `systemfonts` from source should work. Please let me know if it doesn't.

[Here](https://www.r-project.org/nosvn/R.check/r-release-macos-arm64/systemfonts-00install.txt) you can see all the commands that are called when compiling `systemfonts` from source, icluding `FontManagerMac.mm`.