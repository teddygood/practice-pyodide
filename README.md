# practice-pyodide

This repository shows a minimal example of running Python code directly in the browser with [Pyodide](https://pyodide.org/en/stable/).

## Overview

[Pyodide](https://pyodide.org/en/stable/) compiles the CPython interpreter to WebAssembly so that Python can run inside modern web browsers. The `index.html` file in this project loads Pyodide from a CDN and executes a short Python snippet that prints the Python version.

## Setup

You only need a web browser to try the example. For local testing it can be convenient to serve the files via a simple HTTP server:

```bash
python3 -m http.server
```

Then open `http://localhost:8000/index.html` in your browser. The page will download Pyodide and run the embedded Python code.

Refer to the [Pyodide documentation](https://pyodide.org/en/stable/) for more details on configuration and advanced usage.

## Minimal example

`index.html` includes the following script that loads Pyodide and executes Python:

```html
<script src="https://cdn.jsdelivr.net/pyodide/v0.25.1/full/pyodide.js"></script>
<script>
  async function main() {
    const pyodide = await loadPyodide();
    const result = pyodide.runPython(`
import sys
sys.version
    `);
    document.getElementById('version').textContent = result;
  }
  main();
</script>
```

When the page finishes loading it will display the Python version detected by Pyodide.

## NumPy calculator

The demo also includes a simple calculator built with NumPy that runs inside the browser. Enter two numbers, select an operation, and press **Calculate** to see the result.
