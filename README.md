# Playbook.js

Playbook.js is a Javascript American football/gridiron play designer.

![Playbook.js](http://nathandavison.com/images/playbook-field.png)

## Install

Playbook.js requires Raphael to work. However, Playbook.js is not a Raphael plugin as such. 
There are a few Raphael plugins in the Playbook.js code, but these are mostly directly 
related to stuff you'd expect on a football play designer (like using paths as routes etc). 
If using with require.js or similar, Playbook.js expects Raphael to be mapped to the 'raphael' 
alias.

The easiest way to get Playbook.js is with bower, via:

`bower install playbook.js`

Or by cloning this repo:

`git clone https://github.com/ndavison/playbook.js`

## Usage

Simply include Raphael and Playbook.js, and then execute the following:

```javascript
playbook().build();
```

Or for something more practical:

```javascript
var myPlaybook = playbook();
myPlaybook.build();
```

So you have easy access to the playbook instance for changing the mode, importing and exporting etc.

The 'mode' of the playbook determines behaviour when you drag on a player circle. There are currently 
two modes: 'move' and 'design'. The 'move' mode means dragging on the player circles moves them around 
the field. The 'design' mode means dragging on the player circles creates a route, spawning from the 
circle you drag from. From there, the design mode lets you create further segments of the route by 
dragging out from the route itself. To delete a route, you just drag from the player again. If you 
switch back to move mode after routes have been designed, then you are able to move the players and 
each point in the route.

To change the mode on an instance, you call:

```javascript
var myPlaybook = playbook();
myPlaybook.build();

// changing to 'design' mode
myPlaybook.changeMode('design');
```

## Options

The following options are available when passed in an object to the `playbook()` call:

 - `element`: The element the canvas goes into. This value is passed straight to Raphael.
 - `gridSize`: The size in pixels of the invisible grid squares. Effectively changes how accurate snapping players is.
 - `fieldWidth`: The size in pixels of the field width.
 - `fieldHeight`: The size in pixels of the field height.
 - `yardLineGap`: The size in pixels between the major yard lines.
 - `yardLineHeight`: The size in pixels of the yard lines.
 - `yardMarkerWidth`: The size in pixels of the yard marker widths.
 - `routeWidth`: The size in pixels of the route path widths.
 - `colors`: An object (with 'offense' and 'defense' properties) to change the offense and defense colors.
 - `routeOpacity`: An object (with 'offense' and 'defense' properties, number values) to change the opacity of each side's routes.
 - `mode`: A string ('move' or 'design') to set the default mode of the playbook instance when it is created.

## API

### playbook([options])

Creates and returns a new Playbook.js object.

**Available since**: v0.1.0

**Parameters:**
 - options : Object (optional)
   An object of options (see above for available options).

**Returns:**
 - Playbook object.

**Example:**
```javascript
var myPlaybook = playbook();
var myPlaybook = playbook({element: 'field', fieldWidth: 1300, fieldHeight: 600});
````

### playbook.build()

Builds the field and players.

**Available since**: v0.1.0

**Returns:**
 - Playbook object.

**Example:**
```javascript
var myPlaybook = playbook();
myPlaybook.build();
```

### playbook.changeMode(mode)

Changes the active 'mode' of the instance.

**Available since**: v0.1.0

**Parameters:**
 - mode : String

**Returns:**
 - Playbook object.

**Example:**
```javascript
var myPlaybook = playbook();
myPlaybook.build();

// changing to 'design' mode
myPlaybook.changeMode('design');
```

### playbook.exportPlay()

Exports an object representing the state of the instance's players and routes.

**Available since**: v0.1.0

**Returns:**
 - An object with offense and defense properties, each containing coordinates etc for players and routes.

**Example:**
```javascript
var myPlaybook = playbook();
myPlaybook.build();
var currentState = myPlaybook.exportPlay();
```

### playbook.importPlay(play)

Imports an object representing a play, changing the current state of the instance's players and routes.

**Available since**: v0.1.0

**Parameters:**
 - play : An object with offense and defense properties, each containing coordinates etc for players and routes.

**Example:**
```javascript
var myPlaybook = playbook();
myPlaybook.build();
myPlaybook.importPlay(newState);
```

### playbook.playersToFront()

Brings all the player circles to the front.

**Available since**: v0.1.0

**Returns:**
 - Playbook object.

**Example:**
```javascript
var myPlaybook = playbook();
myPlaybook.playersToFront();
```

## License

Playbook.js is open-sourced software licensed under the MIT License.
