
# Live Coding / Algorave tools

An discussion of some tools for Live Coding / Algorave and tipps how to start.

Note that the following "pros and cons" are purely based on personal experience and experimentation. Your opinions may differ. Also, there are many other environments. An overview is here https://github.com/toplap/awesome-livecoding 

## I. Selected Audio tools

### TidalCycles “Tidal”
https://tidalcycles.org/ 

\+ concise syntax     
\+ adoption in the Livecoding / Algorave scene     
\+ resources / documentation / continuously developed    
\+ connectivity (MIDI, OSC, DAW) https://tidalcycles.org/docs/configuration/MIDIOSC/midi     
\+ versatility    
\- complex installation (Mac), for instructions see ["How to install TidalCycles on a Mac"](tidal_setup.md)    

### SonicPi
https://sonic-pi.net/ 

\+ easy setup    
\+ accessibility    
\+ flat learning curve    
\+ friendly devs    
\+ good resources / documentation    
\- performance (computation heavy on Mac)    
\- limits, e.g.  “save” saves a single buffer only, no save function for the whole set, no way to stop a single buffer playing (?)    

### Supercollider 
https://supercollider.github.io/ 

Supercollider provides the sound engine for SonicPi, Tidal and others

\+ deep sound shaping / generating capabilities     
\- very steep learning curve    
\- verbose and sometimes confusing syntax    
\- multiple different ways to simplify livecoding       

### Strudel
based on Tidal but running online and in JavaScript 
https://strudel.tidalcycles.org/

\+ runs in the browser, no installation necessary    
\+ good for workshops    
\- requires internet connection during performance      
\- under heavy development which means breaking changes      
\- using own samples requires a bit more setup       
\- performance less stable than Tidal     

### Chuck
https://chuck.stanford.edu/ 

\+ strong realtime and concurrency model    
\+ setup    
\- steep learning curve    
\- stability issues (Mac)    
\- a bit dated ui (Mac)     
\- developed but unclear roadmap    
\- little adoption in the livecoding scene    

### Orca
https://100r.co/site/orca.html  

\+ cool and different     
\+ interesting experience     
\- steep learning curve    
\- incompatibilities between different versions     
\- current code maintainers not particular welcoming     

## II. Selected Visual tools

### Hydra
https://hydra.ojack.xyz/

support for MIDI, Text, Video and others through 3rd party extension

\+ syntax derived from connecting modular synths     
\+ wide adoption in the Livecoding / Algorave scene     
\+ continuously developed     

### p5.js
https://p5js.org/

widely used creative coding tool    

\+ large userbase, many libraries     
\+ resources / documentation / continuously developed    
\+ versatility    
\- not particularly created for livecoding    
\- no code on top of canvas mode    

## III. Selected AudioVisual integration / collaborative editors / servers for shared performances

### flok
https://flok.cc/    
https://github.com/munshkr/flok    

browser-based collaborative live coding editor / server that integrates several livecoding tools: foxdot, hydra, mercury, remote_sclang, sardine, sclang, strudel, tidalcycles 

\+ can be installed locally       
\+ very clean UI with minimal distractions      
\- security issues when run on a public website       

### gibber / gabber
https://gibber.cc/playground/     
https://github.com/gibber-cc/gibber    

audiovisual browser-based environment with a server for shared performances, can also integrate hydra, p5.js for visuals

\+ well-made tutorial     

### Estuary 
https://estuary.mcmaster.ca/     

browser-based tool collaboration and communication in networked ensembles. integrates several livecoding tools: TidalCycles, Punctual, CineCer0, TimeNot, Seis8s, Hydra

\- ui can become a bit overwhelming    

## Tipps where to start

A) in the browser / no installation

- to start making sounds right away: Strudel 
- to start making visuals right away: Hydra  
- to jam live with others: Gibber / Gabber 

b) with tools installed locally

- to work with rhythmic structures: TidalCycles 
- to combine Live Coding with deep sound design: Supercollider (watch 
Eli Fieldsteel's video https://www.youtube.com/watch?v=6W8XRiFMiCs)
- to sequence a hardware synthesizer with different approach: Orca 
- to make sounds on a Raspberry Pi: Sonic Pi (or Supercollider)


