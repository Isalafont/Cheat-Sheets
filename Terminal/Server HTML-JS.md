# Running HTML and JS on Localhost

When we want to run HTML /Css and JS on localhost, here's what to do. 

Make sure you have **Node.js** install in your system.
### First way
-   go to folder where you have html file:
    -   In CMD, run the command to install http server- `npm install http-server -g`
    -   To load file in the browser run - `http-server`
-   If you have specific html file. Run following command in CMD.- `http-server fileName`
-   by default port is `8080`
-   Go to your browser and type `localhost:8080`. Your Application should run there.
-   If you want to run on different port: `http-server fileName -p 9000`
   
> Note : To run your .js file run: `node fileName.js`

## 2nde Way
==If you have [Node.js](https://nodejs.org/) installed then from the folder you want to share you can simply run:==

```shell
npx http-server
```

To add CORS you can run:

```shell
npx http-server --cors
```

## On mac Os: 
Open Terminal (or iTerm) install [Homebrew](https://www.brew.sh/) then run `brew install live-server` and run live-server.

You also can install [Python 3](https://python.org/) and run `python3 -m http.server PORT`.

## On Windows
If you have VS Code installed open it and install extension liveserver, then click Go Live in the bottom right corner.

Alternatively you can install WSL2 and follow the macOS steps via apt (`sudo apt-get`).

## On linux
Open your favorite terminal emulator and follow the macOS steps via apt (`sudo apt-get`).
