Front-end hacking guide
=======================

Setting up a linter
-------------------

Please set up a linter first. A linter is a program that checks your files for correct style and syntax – it's like spellcheck and grammar check for your code, and you'll be warned of many common errors before you even save your file.

Instructions for Sublime Text 3:

 1. Install [Package Control](https://packagecontrol.io/installation)
 2. Tools » Command Palette » Install Package » `SublimeLinter`
 3. Tools » Command Palette » Install Package » `SublimeLinter-jshint`
 4. Make sure you have Node.js installed.  
    If not: `brew install node` (Mac) or [read here](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions) (Ubuntu)
 4. `npm install -g jshint`



Organization of JS files in `static`
------------------------------------

| Filename             | Class          | Purpose                                                                                                                                                                                                                              |
| :--------            | :-----         | :-------                                                                                                                                                                                                                             |
| app.js               |                | Starts the app.                                                                                                                                                                                                                      |
| bounds.js            | `Bounds`       | `Bounds` indicates the position and dimensions of a rectangle. This file has a spec for `Bounds` objects and has functions for manipulating bounds.                                                                                  |
| datasources.js       | `DataSources`  | Functions for interacting with external data sources (URLs and JSON).                                                                                                                                                                |
| misc.js              | `Misc`         | Utility functions that aren't deeply related to this app.                                                                                                                                                                            |
| player.js            | `Player`       | Player controller code. Binds together `Thing` and `PlayerView`.                                                                                                                                                                     |
| thing.js             | `Thing`        | Thing model. This is an object that sits there and does nothing. It does not know about any of the views. It cannot do anything on its own. However, when you change its keyframes, it will trigger an event that you can listen to. |
| views/               |                | Here lie the views. Views show things and maintain some internal state (a scrubber maintains its current position). They do not interact with anything other than sub-views, but they trigger events that you can listen to.         |
| views/keyframebar.js | `Keyframebar`  | Displays keyframes. Clicking a keyframe triggers an event.                                                                                                                                                                              |
| views/player.js      | `PlayerView`   | View for the entire player. It comes with a `Keyframebar`, a `CreationRect`, and has methods for adding `Rect`s.                                                                                                                     |
| views/rect.js        | `Rect`         | A rectangle/box on-screen.                                                                                                                                                                                                           |
| views/rect.js        | `CreationRect` | A special rectangle/box that normally sits behind all the other rects. When it is dragged, it changes shape to form a new rect. When the drag is finished, it triggers and event and reverts to its initial state.                   |