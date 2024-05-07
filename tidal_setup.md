
# How to install TidalCycles on a Mac or Windows 10

A short guide on how to install a working livecoding setup with [TidalCycles](https://tidalcycles.org/) including SuperCollider, the Haskell language, TidalCycles itself and the VSCode editor.

We will install the individual components one by one by following the instructions on their websites. While you are going through the steps check carefully for prompts and error messages.

## How to install TidalCycles on a Mac

### 1. SuperCollider

Check your Mac OS Version is 10.14 ("Mojave") or Higher
Install the current version of SuperCollider universal binary 
https://supercollider.github.io/downloads   

Then install the [sc3-plugins](https://supercollider.github.io/sc3-plugins/ 
) following the instructions [here](https://github.com/supercollider/sc3-plugins/tree/main?tab=readme-ov-file#installation)

Note: To download the plugins click on "Releases" in the right-hand column and select the one for macOS.

Note: To find the directory in which the extracted ZIP file needs to be moved, start Supercollider, enter `Platform.userExtensionDir` into the window and press Shift and Return. While you are at it, you can test if Supercollider makes sound. Enter 

```
{ SinOsc.ar(220, 0, 0.5) }.play;
```

and press Shift and Return again. There should be sound coming out. If not there are problems with the audio setup on your machine.  

Close Supercollider before proceeding then start Supercollider again. 

From the Menu select "Language -> Quarks". In the popup window, select "SuperDirt". It will add "Vowel" and "DirtSamples" by itself. When the "Recompile Class Library" button goes green, click that button. 

Select `File > Open startup file`, paste the following content into it and save the file. 

```
(
s.reboot { // server options are only updated on reboot
    // configure the sound server: here you could add hardware specific options
    // see http://doc.sccode.org/Classes/ServerOptions.html
    s.options.numBuffers = 1024 * 256; // increase this if you need to load more samples
    s.options.memSize = 8192 * 32; // increase this if you get "alloc failed" messages
    s.options.numWireBufs = 64; // increase this if you get "exceeded number of interconnect buffers" messages 
    s.options.maxNodes = 1024 * 32; // increase this if you are getting drop outs and the message "too many nodes"
    s.options.numOutputBusChannels = 2; // set this to your hardware output channel size, if necessary
    s.options.numInputBusChannels = 2; // set this to your hardware output channel size, if necessary
    // boot the server and start SuperDirt
    s.waitForBoot {
        ~dirt = SuperDirt(2, s); // two output channels, increase if you want to pan across more channels
        ~dirt.loadSoundFiles;   // load samples (path containing a wildcard can be passed in)
        // for example: ~dirt.loadSoundFiles("/Users/myUserName/Dirt/samples/*");
        // s.sync; // optionally: wait for samples to be read
        ~dirt.start(57120, 0 ! 12);   // start listening on port 57120, create two busses each sending audio to channel 0

        // optional, needed for convenient access from sclang:
        (
            ~d1 = ~dirt.orbits[0]; ~d2 = ~dirt.orbits[1]; ~d3 = ~dirt.orbits[2];
            ~d4 = ~dirt.orbits[3]; ~d5 = ~dirt.orbits[4]; ~d6 = ~dirt.orbits[5];
            ~d7 = ~dirt.orbits[6]; ~d8 = ~dirt.orbits[7]; ~d9 = ~dirt.orbits[8];
            ~d10 = ~dirt.orbits[9]; ~d11 = ~dirt.orbits[10]; ~d12 = ~dirt.orbits[11];
        );
    };

    s.latency = 0.3; // increase this if you get "late" messages
};
);
```

When this is done, close Supercollider.

### 2. Haskell

Open the Mac Terminal and install ghcup following the instructions:
https://www.haskell.org/ghcup/     
This will ask you to confirm some steps and the installation will take a while. 

If you don't have already XCode installed, you will be also prompted to install the XCode command line tools, which takes quite a long time to install. You will be prompted for your password during the installation.

### 3. TidalCycles

After the previous step has finished, close the Mac Terminal and reopen it.
Then run the following commands 

`cabal update`  

then 

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

Keep the cursor in the line and press control and Return. The line will be highlighted and after a few seconds the sound should come. (These few seconds delay only occur when TidalCycles "boots up". Later the sound will be triggered immediately).  

If you hear drums ... done. Congratulations. If not, check your audio setup carefully, make sure you followed all instructions and check for error messages.

Enter `hush` on a new line and do control + Return to silence the drummer.

If you are new to TidalCycles I recommend to go through the [tutorial called "workshop"](https://tidalcycles.org/docs/patternlib/tutorials/workshop) on the TidalCycles website. Then keep practicing - there are lots of videos, tutorials and reference material to learn from.

## How to install TidalCycles on Windows 10

A short guide on how to install a working livecoding setup with [TidalCycles](https://tidalcycles.org/) including SuperCollider, the Haskell language, TidalCycles itself and the VSCode editor.

During the Installation you might get various Pop-Ups to confirm access for the element you are installing. 

### 1. SuperCollider

Install the current version of SuperCollider for Windows 64 bit
https://supercollider.github.io/downloads   

Then install the sc3-plugins following the instructions [here](https://github.com/supercollider/sc3-plugins/tree/main?tab=readme-ov-file#installation)
https://supercollider.github.io/sc3-plugins/ 

To download the plugins click on "Releases" in the right-hand column and select the one for Windows-64bit.

To find the directory in which the extracted ZIP file needs to be moved, start Supercollider, enter `Platform.userExtensionDir` and press Shift and Return. In the "Post window" a folder name will be displayed.

While you are at it, you can test if Supercollider makes sound. 

First check the color of the numbers in the bottom bar right of "Server". 

* Green: all fine, proceed. 
* White: click on them and select "Boot Server". 
* Yellow: Wait until they turn green. Read the output of the "Post window" closely, e.g. the message saying "Windows defender" might delay the start by a minute. In my test, this happened only the first time I was running Supercollider.

Then enter  

```
{ SinOsc.ar(220, 0, 0.5) }.play;
```

and press Shift and Return again. There should be sound coming out. If not, then there are problems with the audio setup on your machine.  

In the Windows File Explorer, select the "View" tab and activate "Hidden Items". Then you can navigate to the  `Platform.userExtensionDir` folder above.

Close Supercollider before proceeding, then start Supercollider again. 

From the Menu select "Language -> Quarks". In the popup window, select "SuperDirt". It will add "Vowel" and "DirtSamples" by itself. When the "Recompile Class Library" button goes green, click that button. 

Select `File > Open startup file`, paste the following content into it and save the file. 

```
(
s.reboot { // server options are only updated on reboot
    // configure the sound server: here you could add hardware specific options
    // see http://doc.sccode.org/Classes/ServerOptions.html
    s.options.numBuffers = 1024 * 256; // increase this if you need to load more samples
    s.options.memSize = 8192 * 32; // increase this if you get "alloc failed" messages
    s.options.numWireBufs = 64; // increase this if you get "exceeded number of interconnect buffers" messages 
    s.options.maxNodes = 1024 * 32; // increase this if you are getting drop outs and the message "too many nodes"
    s.options.numOutputBusChannels = 2; // set this to your hardware output channel size, if necessary
    s.options.numInputBusChannels = 2; // set this to your hardware output channel size, if necessary
    // boot the server and start SuperDirt
    s.waitForBoot {
        ~dirt = SuperDirt(2, s); // two output channels, increase if you want to pan across more channels
        ~dirt.loadSoundFiles;   // load samples (path containing a wildcard can be passed in)
        // for example: ~dirt.loadSoundFiles("/Users/myUserName/Dirt/samples/*");
        // s.sync; // optionally: wait for samples to be read
        ~dirt.start(57120, 0 ! 12);   // start listening on port 57120, create two busses each sending audio to channel 0

        // optional, needed for convenient access from sclang:
        (
            ~d1 = ~dirt.orbits[0]; ~d2 = ~dirt.orbits[1]; ~d3 = ~dirt.orbits[2];
            ~d4 = ~dirt.orbits[3]; ~d5 = ~dirt.orbits[4]; ~d6 = ~dirt.orbits[5];
            ~d7 = ~dirt.orbits[6]; ~d8 = ~dirt.orbits[7]; ~d9 = ~dirt.orbits[8];
            ~d10 = ~dirt.orbits[9]; ~d11 = ~dirt.orbits[10]; ~d12 = ~dirt.orbits[11];
        );
    };

    s.latency = 0.3; // increase this if you get "late" messages
};
);
```

When this is done, close Supercollider.

### 2. Haskell

Open a Powershell window and install ghcup following the instructions:
https://www.haskell.org/ghcup/     
This will ask you to confirm some steps and the installation will take a while. It will open a second Window named "MinGW x64", make sure the installation has finished in that window as well. This one can take a long time. 

### 3. TidalCycles

After the previous step has finished, close both the Powershell window and the MinGW and open a new Powershell window "Run as Administrator".

Then run the following commands 

`cabal update`    

then 

`cabal v1-install tidal`

### 4. VSCode

Install VSCode 
https://code.visualstudio.com/ 

Finally, install the TidalCycles VSCode Extension
https://marketplace.visualstudio.com/items?itemName=tidalcycles.vscode-tidalcycles    

### Testing the Setup

1. Start Supercollider. The bottom bar will change color a bit going green then yellow then green again.
2. In VSCode, create a new file and save it as "hello.tidal". Select "TIDAL" as the "Save as type".

Enter this line into the file 

```
d1 $ sound "bd hh sn hh"

```

Keep the cursor in the line and press control and Return. The line will be highlighted and after a few seconds the sound should come. (These few seconds delay only occur when TidalCycles "boots up". Later the sound will be triggered immediately).  

If you hear drums ... done. Congratulations. If not, check your audio setup carefully, make sure you followed all instructions and check for error messages.

Enter `hush` on a new line and do control + Return to silence the drummer.

If you are new to TidalCycles I recommend to go through the [tutorial called "workshop"](https://tidalcycles.org/docs/patternlib/tutorials/workshop) on the TidalCycles website. Then keep practicing - there are lots of videos, tutorials and reference material to learn from.

## FAQ

Q: What are prerequisites for this installation?

A: A fairly up-to date Macbook (Pro) or a Windows computer running Windows 10 (it should work on Windows 11 but I don't have a device to test). "Fairly up-to date" means you should have a recent macOS on your machine (10.14 or later) - some of the components above will not work on very old hardware or operating system. Maybe you can find older versions of them but this is beyond the scope of this guide. You should know how to use the Terminal or PowerShell window and how to unzip and move files. Plan for roughly 2 hours, sometime the installation will need your attention while other steps take time while you can do other things. 

Q: What is the difference between this and the official installation guides for [Mac](https://tidalcycles.org/docs/getting-started/macos_install) and [Windows](https://tidalcycles.org/docs/getting-started/windows_install)?

A: Method: My preferred method is to suggest installing components by following the instructions on their individual websites. The alternative would be to provide detailed step-by-step instructions which get  outdated quickly.

Manual installation: The official installation guide features an additional [install script](https://github.com/tidalcycles/tidal-bootstrap), which in theory is a good idea because you could run the script and it would do all the above steps for you. In practice the script comes whith [its own issues](https://github.com/tidalcycles/tidal-bootstrap/issues) and the components it installs are currently not up-to date. If you not already an expert, it is harder to understand what to do when a long-running script throws an error message than when one of the individual steps described above would fail. 

Minimal Dependencies: For Windows, the official installation guide recommends using the Chocolatey package manager whereas I follow a manual approach in order to reduce the number of dependencies. 

Code Editor: I use the VSCode editor whereas the official installation guide recommends Pulsar, a community-led fork of the Atom editor.

Scope: This guide only covers macOS and Windows 10 - which I have tested - whereas the TidalCycles website has instructions for other options too.  


