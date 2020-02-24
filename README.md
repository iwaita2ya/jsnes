# JSNES

A JavaScript NES emulator.  
forked from https://github.com/bfirsh/jsnes  
'require' -> 'import/export'  

## Embedding JSNES in a web page

see [index.html](https://taisukef.github.io/jsnes/)  

## Usage

```javascript
// Initialize and set up outputs
var nes = new jsnes.NES({
  onFrame: function(frameBuffer) {
    // ... write frameBuffer to screen
  },
  onAudioSample: function(left, right) {
    // ... play audio sample
  }
});

// Read ROM data from disk (using Node.js APIs, for the sake of this example)
const fs = require('fs');
var romData = fs.readFileSync('path/to/rom.nes', {encoding: 'binary'});

// Load ROM data as a string or byte array
nes.loadROM(romData);

// Run frames at 60 fps, or as fast as you can.
// You are responsible for reliable timing as best you can on your platform.
nes.frame();
nes.frame();
// ...

// Hook up whatever input device you have to the controller.
nes.buttonDown(1, jsnes.Controller.BUTTON_A);
nes.frame();
nes.buttonUp(1, jsnes.Controller.BUTTON_A);
nes.frame();
// ...
```

## Maintainers

- [Ben Firshman](http://github.com/bfirsh)
- [Ben Jones](https://github.com/BenShelton)
- [Stephen Hicks](https://github.com/shicks)
- [Alison Saia](https://github.com/allie)
- [Taisuke Fukuno](https://github.com/taisukef)

JSNES is based on [James Sanders' vNES](https://github.com/bfirsh/vNES), and owes an awful lot to it. It also wouldn't have happened without [Matt Wescott's JSSpeccy](http://jsspeccy.zxdemo.org/), which sparked the original idea. (Ben, circa 2008: "Hmm, I wonder what else could run in a browser?!")
