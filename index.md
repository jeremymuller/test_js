---
layout: default
title: Yay
---

# Hello
## This is a test



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

<script src="https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.29.1/min/vs/loader.min.js"></script>
<script>
// Proxy Monaco Editor workers using a data URL (adapted from: https://github.com/microsoft/monaco-editor/blob/main/docs/integrate-amd-cross.md)
require.config({ paths: { "vs": "https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.29.1/min/vs/" }});

window.MonacoEnvironment = {
    getWorkerUrl: function(workerId, label) {
        return `data:text/javascript;charset=utf-8,${encodeURIComponent(`
            self.MonacoEnvironment = { baseUrl: "https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.29.1/min/" };
            importScripts("https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.29.1/min/vs/base/worker/workerMain.min.js");`
        )}`;
    }
};

require(["vs/editor/editor.main"], function () {
    // Create the editor with some sample JavaScript code
    var editor = monaco.editor.create(document.getElementById("editor"), {
        value: "// code goes here\n",
        language: "javascript"
    });

    // Resize the editor when the window size changes
    const editorElement = document.getElementById("editor");
    window.addEventListener("resize", () => editor.layout({
        width: editorElement.offsetWidth,
        height: editorElement.offsetHeight
    }));
});
</script>
