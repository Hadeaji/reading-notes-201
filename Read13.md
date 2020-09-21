# Local Storage

Persistent local is one of the areas where native client applications have held an advantage over web applications.

the operating system typically provides an abstraction layer for storing and retrieving application-specific data like preferences or runtime state. These values may be stored in the registry, INI files, XML files, or some other place according to platform convention.

Historically, web applications have had none of these luxuries. Cookies were invented early in the web’s history, and indeed they can be used for persistent local storage of small amounts of data.
But they have three potentially dealbreaking downsides:

- Cookies are included with every HTTP request, thereby slowing down your web application by needlessly transmitting the same data over and over

- Cookies are included with every HTTP request, thereby sending data unencrypted over the internet (unless your entire web application is served over SSL)

- Cookies are limited to about 4 KB of data — enough to slow down your application (see above), but not enough to be terribly useful

### What we really want is

- a lot of storage space

- on the client

- that persists beyond a page refresh

- and isn’t transmitted to the server

## A BRIEF HISTORY OF LOCAL STORAGE HACKS

### **There was only Internet Explorer.**

![ex](Read13-1.jpg)

Or at least, that’s what Microsoft wanted the world to think.

**Microsoft** invented a great many things One of these things was called DHTML Behaviors, and one of these behaviors was called userData.

**userData** allows web pages to store up to 64 KB of data per domain, in a hierarchical XML-based structure. (Trusted domains, such as intranet sites, can store 10 times that amount.

**In 2002, Adobe** introduced a feature in Flash 6 that gained the unfortunate and misleading name of “Flash cookies.” Within the Flash environment, the feature is properly known as Local Shared Objects. Briefly, it allows Flash objects to store up to 100 KB of data per domain.

**By 2006,** with the advent of ExternalInterface in Flash 8, accessing LSOs from **JavaScript became an order of magnitude easier and faster**

**In 2007, Google launched Gears,** an open source browser plugin aimed at providing additional capabilities in browsers.
Gears provides an API to an embedded SQL database based on SQLite. After obtaining permission from the user once, **Gears can store unlimited amounts of data per domain in SQL database tables**.

## INTRODUCING HTML5 STORAGE

From your JavaScript code, you’ll access HTML5 Storage through the localStorage object on the global window object. Before you can use it, you should detect whether the browser supports it.


`function supports_html5_storage() {`
  `try {`
   `return 'localStorage' in window && window['localStorage'] !== null;`
  `} catch (e) {`
    `return false;`
  `}`
`}`

and instead of writing it yourself you can use Modernizr

#### USING HTML5 STORAGE

HTML5 Storage is based on named key/value pairs.
You store data based on a named key, The data can be any type supported by JavaScript,  However, the data is actually stored as a string. If you are storing and retrieving anything other than strings, you will need to use functions like `parseInt()` or `parseFloat()` to coerce your retrieved data into the expected JavaScript datatype.

#### TRACKING CHANGES TO THE HTML5 STORAGE AREA

you can trap the storage event. The storage event is fired on the window object whenever setItem(), removeItem(), or clear() is called and actually changes something.

#### HTML5 STORAGE IN ACTION

Recall `the Halma game`.
There’s a small problem with the game: if you close the browser window mid-game, you’ll lose your progress. But with HTML5 Storage, we can save the progress locally, within the browser itself

How does it work? Every time a change occurs within the game, we call this function:

`function saveGameState() {`
    `if (!supportsLocalStorage()) { return false; }`
    `localStorage["halma.game.in.progress"] = gGameInProgress;`
    `for (var i = 0; i < kNumPieces; i++) {`
 `localStorage["halma.piece." + i + ".row"] = gPieces[i].row;`
 `localStorage["halma.piece." + i + ".column"] = gPieces[i].column;`
   `}`
    `localStorage["halma.selectedpiece"] = gSelectedPieceIndex;`
    `localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;`
    `localStorage["halma.movecount"] = gMoveCount;`
    `return true;`
`}`

On page load, instead of automatically calling a newGame() function that would reset these variables to hard-coded values, we call a resumeGame() function instead.

`function resumeGame() {`
    `if (!supportsLocalStorage()) { return false; }`
`gGameInProgress = (localStorage["halma.game.in.progress"] == "true");`
    `if (!gGameInProgress) { return false; }`
`gPieces = new Array(kNumPieces);`
    `for (var i = 0; i < kNumPieces; i++) {`
 `var row = parseInt(localStorage["halma.piece." + i + ".row"]);`
 `var column = parseInt(localStorage["halma.piece." + i + ".column"]);`
 `gPieces[i] = new Cell(row, column);`
   `}`
    `gNumPieces = kNumPieces;`
    `gSelectedPieceIndex = parseInt(localStorage["halma.selectedpiece"]);`
    `gSelectedPieceHasMoved = localStorage["halma.selectedpiecehasmoved"] == "true";`
    `gMoveCount = parseInt(localStorage["halma.movecount"]);`
    `drawBoard();`
    `return true;`
`}`

***Data is stored as strings. If you are storing something other than a string, you’ll need to coerce it yourself when you retrieve it.***

`localStorage["halma.game.in.progress"] = gGameInProgress;`

But in the resumeGame() function, we need to treat the value we got from the local storage area as a string and manually construct the proper Boolean value ourselves:

`gGameInProgress = (localStorage["halma.game.in.progress"] == "true");`

Similarly, the number of moves is stored in gMoveCount as an integer. In the saveGameState() function, we just stored it:

`localStorage["halma.movecount"] = gMoveCount;`

But in the resumeGame() function, we need to coerce the value to an integer, using the parseInt() function built into JavaScript:

`gMoveCount = parseInt(localStorage["halma.movecount"]);`



### BEYOND NAMED KEY-VALUE PAIRS: COMPETING VISIONS

> While the past is littered with hacks and workarounds, the present condition of HTML5 Storage is surprisingly rosy. A new API has been standardized and implemented across all major browsers, platforms, and devices.

