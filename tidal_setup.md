
# How to install TidalCycles on a Mac

A short guide on how to install a working livecoding setup with [TidalCycles](https://tidalcycles.org/) including SuperCollider, the Haskell language, TidalCycles itself and the VSCode editor.

We will install the individual components one by one by following the instructions on their websites. While you are going through the steps check carefully for prompts and error messages.

### 1. SuperCollider

Install the current version of SuperCollider
https://supercollider.github.io/downloads   

Then install the sc3-plugins following the instructions [here](https://github.com/supercollider/sc3-plugins/tree/main?tab=readme-ov-file#installation)
https://supercollider.github.io/sc3-plugins/ 

Start Supercollider. From the Menu select "Language -> Quarks". In the popup window, select the "SuperDirt", "Vowel" and "DirtSamples" quarks. When the "Recompile Class Library" button goes green, click that button. 
When it is finished, close Supercollider.

### 2. Haskell

Open the Mac Terminal and install ghcup following the instructions:
https://www.haskell.org/ghcup/     
This will take a while and it will ask you to confirm some of the steps. 

If you don't have already XCode installed you will be also prompted to install the XCode command line tools, which takes quite a long time to install. You will be prompted for your password during the installation.

### 3. TidalCycles

After the previous step has finished, close the Mac Terminal and reopen it.
Then run the following commands 

`cabal update`    
`cabal v1-install tidal`

### 4. VSCode

Install VSCode 
https://code.visualstudio.com/ 

Finally, install the TidalCycles VSCode Extension
https://marketplace.visualstudio.com/items?itemName=tidalcycles.vscode-tidalcycles     


### Testing the Setup

1. Start Supercollider. The bottom bar will change color a bit going green then yellow then green again.
2. In VSCode, create a new file and save it as "hello.tidal"

Enter this line into the file 

```
d1 $ sound "bd hh sn hh"

```

Keep the cursor in the line and press control + Return. The line will be highlighted and after a few seconds the sound should come. (These few seconds delay only occur when TidalCycles "boots up". Later the sound will be triggered immediately).  

If you hear drums ... done. Congratulations. If not, check your audio setup carefully, make sure you followed all instructions and check for error messages.

Enter `hush` on a new line and do control + Return to silence the drummer.

If you are new to TidalCycles I recommend to go through the [tutorial called "workshop"](https://tidalcycles.org/docs/patternlib/tutorials/workshop) on the TidalCycles website. Then keep practicing - there are lots of videos, tutorials and reference material to learn from.

## FAQ

Q: What are prerequisites for this installation?

A: A fairly up-to date Macbook (Pro). Fairly up-to date means you should have a recent macOS on your machine - some of the components above will not work on very old hardware or operating system. Maybe you can find older versions of them but this is beyond the scope of this guide. You should know how to use the Terminal on your Mac, and how to unzip and move files. Plan for roughly 2 hours, sometime the installation will need your attention while other steps take time while you can do other things. 

Q: What is the difference between this and the [official installation guide](https://tidalcycles.org/docs/getting-started/macos_install)?

A: Method: For installations like these my preferred method is installing the components by following the instructions on the individual websites. The alternative would be to provide detailed instructions which will go out of date quickly.

Manual installation steps: The official installation guide features an additional [install script](https://github.com/tidalcycles/tidal-bootstrap), which in theory is a good idea because you could run the script and it would do all the above steps for you. In practice the script comes whith [its own issues](https://github.com/tidalcycles/tidal-bootstrap/issues) and the components it installs are currently not up-to date. If you not already an expert, it is harder to understand what to do when a long-running script throws an error message than when one of the individual steps described above would fail.  

Code Editor: I use the VSCode editor whereas the official installation guide recommends Pulsar, a community-led fork of the Atom editor.

Scope: This guide covers macOS only - which I use - wheras the website has instructions for Windows and Linux too.  


