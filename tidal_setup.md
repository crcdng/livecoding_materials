
# How to install TidalCycles on a Mac

A short guide on how to install a working livecoding setup with [TidalCycles](https://tidalcycles.org/) including SuperCollider, the Haskell language, TidalCycles itself and the VSCode editor.

Install the individual components by following the instructions on their websites. 

### 1. SuperCollider

Install SuperCollider, sc3-plugins, SuperDirt, Vowel Quark, and the DirtSamples quark 
https://supercollider.github.io/downloads     
https://supercollider.github.io/sc3-plugins/    
https://github.com/musikinformatik/SuperDirt     

### 2. Haskell

Open the Mac Terminal and install ghcup - this step will take a while and asks you to confirm some of the steps 
https://www.haskell.org/ghcup/     

If you don't have already XCode installed you will be also prompted to install the XCode command line tools, which may take a long time to install

### 3. TidalCycles

After the previous step has finished, close the Mac Terminal and reopen it.
Then run the following commands 
`cabal update`    
`cabal v1-install tidal`

### 4. VSCode

Install VSCode and the TidalCycles VSCode Extension
https://code.visualstudio.com/     
https://marketplace.visualstudio.com/items?itemName=tidalcycles.vscode-tidalcycles     


### Testing the Setup

1. Start Supercollider 
2. In VSCOde create a new file and save it as "hello.tidal"

Enter this line into the file 

```
d1 $ sound "bd hh sn hh"

```

Keep the cursor in the line and press control + Return. The line will be highlighted and after a few seconds the sound should come.   

If you hear the drums ... done. Congratulations. If not, check your audio setup carefully, make sure you followed all instructions and check for error messages.

Enter `hush` on a new line and do control + Return to silence the drummer.

If you are new to TidalCycles I rcommend to go through the [tutorial called "workshop"](https://tidalcycles.org/docs/patternlib/tutorials/workshop) on the TidalCycles website. Then keep practicing - there are lots of videos, tutorials and reference material to learn from.

## FAQ

Q: What are the prerequisites?

A: a fairly up-to date Macbook (Pro) and you should know how to use the Terminal on your Mac. Fairly up-to date means you should have a recent macOS on your machine - some of the components above will not work on very old hardware or operating system. Maybe you can find older versions of them but this is beyond the scope of this guide.   

Q: What is the difference between this and the [official installation guide](https://tidalcycles.org/docs/getting-started/macos_install)?

A: Method: For installations like these my preferred method is installing individual components by following the instructions on their own websites. The alternative is be to provide detailed instructions which go quickly out of date.

The official installation guide features an additional [install script](https://github.com/tidalcycles/tidal-bootstrap), which in theory is a good idea because you could run the script and it would do all the steps above for you. In practice the script comes whith [its own issues](https://github.com/tidalcycles/tidal-bootstrap/issues) and the components it installs are currently not up-to date.  

This guide covers macOS only - which I use - wheras the website has instructions for Windows and Linux too.  

I use the VSCode editor whereas the official installation guide recommends Pulsar, a community-led fork of the Atom editor.



