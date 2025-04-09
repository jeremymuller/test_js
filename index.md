# Hello
## This is a test

<script src="loader.js"></script>


```javascript
// here's some javascript:
console.log("hello world");

const audioCtx = new AudioContext();

const osc = audioCtx.createOscillator();
osc.frequency.setValueAtTime(440, audioCtx.currentTime);

osc.connect(audioCtx.destination);
osc.start();
osc.stop(audioCtx.currentTime + 2);

```

