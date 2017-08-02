# AutoCAD LISP Commands for automating tedious tasks
A tool which has been developed to automate some of the tedious and time consuming tasks in AutoCAD. If you have any feature requests get in touch and I will try to add it in.

## Important Note
### TL;DR - Don't change the layer names
The functionality of this tool has been built around a pre-determined set of layer names. Many of the commands rely on the layer names to perform their intended function. Hence if you change a layer name, either within the code or manually within AutoCAD, there is a chance you will break some / all of the commands. If you feel a layer is badly named or could be improved, please get in touch. Other properties of the layers, such as their colour, can be changed without having any adverse effect on the tool.

## Table of Contents
  1. [Installation](#installation)
  2. [Commands](#commands)
     1. [sts-layers](#sts-layers)
     2. [sts-layers-ext](#sts-layers-ext)
     3. [sts-200](#sts-200)
     4. [sts-500](#sts-500)
     5. [sts-1000](#sts-1000)
     6. [sts-lock](#sts-lock)
     7. [sts-unlock](#sts-unlock)
  3. [Layers](#layers)
     1. [Standard Layers](#standard-layers)
     2. [Extended Layers](#extended-layers)
___
## Installation
To use the tool, download a copy of the `.LSP` file and save it somewhere on your machine.

Within AutoCAD click on;

  - Tools
  - Load Application
  - Contents... (lower right of the window, part of the "Startup Suite")
  - Add...
  - Locate the file
  - Open
  
The script should now load everytime you start AutoCAD.
___
## Commands
### `sts-layers`
#### This command can be used anywhere within the drawing (modelspace, paperspace, within a viewport).
Creates a 'standard' set of [layers](#layers) in AutoCAD which you would expect to need in a typical design drawing. 

### `sts-layers-ext`
#### This command can be used anywhere within the drawing (modelspace, paperspace, within a viewport).
Creates an extended set of [layers](#layers) for more complex design drawings. It includes layers for items such as existing equipment
which is to be retained or reused. It also creates layers for non-standard text, such as roadnames in a 1:200 viewport.

### `sts-200`
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.
The command will freeze (switch off) any layers which are not deemed to be required in a 1:200 viewport (such as roadnames).

### `sts-500`
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.
The command will freeze (switch off) any layers which are not deemed to be required in a 1:500 viewport (such as pole numbers).

### `sts-1000`
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.
The command will freeze (switch off) any layers which are not deemed to be required in a 1:1000 viewport (such as pole numbers).

### `sts-lock`
#### This command can only be used in paperspace, not inside an active viewport.
The command will lock all viewports on the active layout, and freeze (switch off) the layer `STS_LAYOUT-VP2` as this layer is 
often used for viewports where the border should be hidden for aesthetic purposes. 

### `sts-unlock`
#### This command can only be used in paperspace, not inside an active viewport.
The command will thaw (switch on) layer `STS_LAYOUT-VP2` on the active layout, as this is commonly used for viewports with hidden borders. It will then unlock (_Display Locked Off_) all viewports on the active layout. This command relies on proper use of layer names, as it will only thaw the `STS_LAYOUT-VP2` layer. If you have frozen any other layers within the paperspace, these will stay frozen and thus not be unlocked (AutoCAD can only unlock thawed viewports).
___
## Layers

### Layers

The tables list the layer names, their colours, and whether or not they appear in a specific viewport type after running one of the viewport scale commands (eg, [sts-200](#sts-200)).

#### Standard Layers
|Layer Name|Colour|Visible in 1:200 VP|Visible in 1:500 VP|Visible in 1:1000 VP|Expected Use|
|-|-|:-:|:-:|:-:|-|
|`SETOUT`|cyan||||General setting out|
|`LAYOUT-VP1`|white|||X|Viewports which will have their border visible (eg drawing detail)|
|`LAYOUT-VP2`|white|||X|Viewports which will have their border hidden (eg notes)|
|`LAYOUT-NORTHPOINT`|white||X|X||
|`LAYOUT-SCALE`|white|X|X|X|Scale bar|
|`DUCTBOXES`|green|X|X|X||
|`DUCTS`|green|X|X|X||
|`HARDSTANDING`|white|X|X|X||
|`HFS-BUFF`|42|X|X|X||
|`LINES`|white|X|X|X||
|`LOOPS`|red|X|X|X||
|`SIGNALS`|blue|X|X|X||
|`SOCKETS`|green|X|X|X||
|`STDDET-CABLEDIA`|white|||X|Cable diagram|
|`STDDET-CROSSING-TIMES`|white|||X|Crossing times table|
|`STDDET-LOOPS`|white|||X|Loop standard detail|
|`STDDET-POLE-DETAIL`|white|||X|Pole setting out /passive pole table|
|`STDDET-STAGING`|white|||X|Staging diagram|
|`TACTILES`|red|X|X|X||
|`TEXT-DETECTORS-1.200`|white|X||X||
|`TEXT-DUCTS-1.500`|green||X|X||
|`TEXT-KEY`|white|||X||
|`TEXT-LEADER-1.500`|white||X|X||
|`TEXT-LOOPS-1.500`|red||X|X||
|`TEXT-NOTES`|white|||X||
|`TEXT-PHASES-1.200`|white|X||X||
|`TEXT-POLE-NUMBER-1.200`|white|X||X||
|`TEXT-ROADNAMES-1.500`|white||X|X||

#### Extended Layers
|Layer Name|Colour|Visible in 1:200 VP|Visible in 1:500 VP|Visible in 1:1000 VP|Expected Use|
|-|-|:-:|:-:|:-:|-|
|`SETOUT1`|yellow|||X|Alternative setout|
|`CUTLINE`|13|X|X|X|Cutline to another viewport|
|`SECONDARY-VISIBILITY`|white|||X|"Secondary visibility" block|
|`DUCTBOXES-EXISTING`|magenta|X|X|X|Existing ductboxes|
|`DUCTBOXES-REMOVE`|8|X|X|X|Ductboxes to be removed|
|`DUCTBOXES-UTILISE`|30|X|X|X|Ductboxes to be re-used|
|`DUCTS-EXISTING`|magenta|X|X|X||
|`DUCTS-REMOVE`|8|X|X|X||
|`DUCTS-UTILISE`|30|X|X|X||
|`HFS-GREY`|8|X|X|X||
|`LOOPS-EXISTING`|magenta|X|X|X||
|`LOOPS-REMOVE`|8|X|X|X||
|`LOOPS-UTILISE`|30|X|X|X||
|`SIGNALS-EXISTING`|magenta|X|X|X||
|`SIGNALS-REMOVE`|8|X|X|X||
|`SIGNALS-UTILISE`|30|X|X|X||
|`SOCKETS-EXISTING`|magenta|X|X|X||
|`SOCKETS-REMOVE`|8|X|X|X||
|`SOCKETS-UTILISE`|30|X|X|X||
|`TACTILES-EXISTING`|magenta|X|X|X||
|`TACTILES-REMOVE`|8|X|X|X||
|`TACTILES-UTILISE`|30|X|X|X||
|`TEXT-DETECTORS-1.500`|white||X|X||
|`TEXT-DUCTS-1.200`|green|X||X||
|`TEXT-LEADER-1.200`|white|X||X||
|`TEXT-LOOPS-1.200`|red|X||X||
|`TEXT-PHASES-1.500`|white||X|X||
|`TEXT-POLE-NUMBER-1.500`|white||X|X||
|`TEXT-ROADNAMES-1.200`|white|X||X||
