# cs-lisp - AutoCAD LISP Commands for automating tedious tasks
CS LISP Commands

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
     1. [Importance of Layer Names](#importance-of-layer-names)
     2. [Layer Name List](#layer-name-list)

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
The way the layers are named is important, as other commands within this tool refer to specific layer names.
Changing the names of layers within the code can have an adverse effect on other commands so care should be taken if you decide
to rename any of the pre-defined layers.

### `sts-layers-ext`
#### This command can be used anywhere within the drawing (modelspace, paperspace, within a viewport).
Creates an extended set of [layers](#layers) for more complex design drawings. It includes layers for items such as existing equipment
which is to be retained or reused. It also creates layers for non-standard text, such as roadnames in a 1:200 viewport.

### `sts-200`
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.
The command will switch off (freeze) any layers which are not deemed to be required in a 1:200 viewport (such as roadnames). This command uses layer names to determine whether a layer should be switched off, hence it is important to use layers correctly, and not to rename layers which have been created using this tool.

### `sts-500`
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.
The command will switch off (freeze) any layers which are not deemed to be required in a 1:500 viewport (such as pole numbers).
This command uses layer names to determine whether a layer should be switched off, hence it is important to use layers
correctly, and not to rename layers which have been created using this tool.

### `sts-1000`
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.
The command will switch off (freeze) any layers which are not deemed to be required in a 1:1000 viewport (such as pole numbers).
This command uses layer names to determine whether a layer should be switched off, hence it is important to use layers
correctly, and not to rename layers which have been created using this tool.

### `sts-lock`
#### This command can only be used in paperspace, not inside an active viewport.
The command will lock all viewports on the active layout, and switch off (freeze) the layer `STS_LAYOUT-VP2` as this layer is 
often used for viewports where the border should be hidden for aesthetic purposes. 

### `sts-unlock`
#### This command can only be used in paperspace, not inside an active viewport.
The command will switch on (thaw) layer `STS_LAYOUT-VP2` on the active layout, as this is commonly used for viewports with hidden borders (for aesthetic value). It will then unlock (Display Locked Off) all viewports on the active layout. This command relies on proper use of layer names, as it will only thaw the `STS_LAYOUT-VP2` layer. If you have frozen any other layers within the paperspace, these will stay hidden and thus not be unlocked.
___
## Layers
### Importance of Layer Names
The names of the layers in the table below should not be changed. If you feel a layer name is not appropriate, issue a pull request or email jonny[dot]wright[at]siemens[dot]com. Most of the commands within this tool refer directly to the layer names, so if a layer name is updated then there is a high chance the command will break. Layer colours can be changed if absolutely necessary, without risk of breaking the tool, however this does lead to inconsistency between designs. It is understood that in certain circumstances, such as a direct customer request, this may be unavoidable.

### Layer Name List
The table below lists all of the layers currently built into this tool. If you feel you could improve this list, issue a pull request or email jonny[dot]wright[at]siemens[dot]com.

The table lists the layer name, it's colour, whether it is created as part of the [sts-layers](#sts-layers) (Standard) command, or as part of the [sts-layers-ext](#sts-layers-ext) (Extended) command. It also specifies whether or not it will be visible in specific viewport types, after running one of the viewport scale commands.

|Layer Name|Colour|Layer Set|Visible in 1:200 VP|Visible in 1:500 VP|Visible in 1:1000 VP|Expected Use|
|-|-|-|:-:|:-:|:-:|-|
|`SETOUT`|cyan|Standard||||General setting out|
|`LAYOUT-VP1`|white|Standard|||X|Viewports which will have their border visible (eg drawing detail)|
|`LAYOUT-VP2`|white|Standard|||X|Viewports which will have their border hidden (eg notes)|
|`LAYOUT-NORTHPOINT`|white|Standard||X|X||
|`LAYOUT-SCALE`|white|Standard|X|X|X|Scale bar|
|`DUCTBOXES`|green|Standard|X|X|X||
|`DUCTS`|green|Standard|X|X|X||
|`HARDSTANDING`|white|Standard|X|X|X||
|`HFS-BUFF`|42|Standard|X|X|X||
|`LINES`|white|Standard|X|X|X||
|`LOOPS`|red|Standard|X|X|X||
|`SIGNALS`|blue|Standard|X|X|X||
|`SOCKETS`|green|Standard|X|X|X||
|`STDDET-CABLEDIA`|white|Standard|||X|Cable diagram|
|`STDDET-CROSSING-TIMES`|white|Standard|||X|Crossing times table|
|`STDDET-LOOPS`|white|Standard|||X|Loop standard detail|
|`STDDET-POLE-DETAIL`|white|Standard|||X|Pole setting out /passive pole table|
|`STDDET-STAGING`|white|Standard|||X|Staging diagram|
|`TACTILES`|red|Standard|X|X|X||
|`TEXT-DETECTORS-1.200`|white|Standard|X||X||
|`TEXT-DUCTS-1.500`|green|Standard||X|X||
|`TEXT-KEY`|white|Standard|||X||
|`TEXT-LEADER-1.500`|white|Standard||X|X||
|`TEXT-LOOPS-1.500`|red|Standard||X|X||
|`TEXT-NOTES`|white|Standard|||X||
|`TEXT-PHASES-1.200`|white|Standard|X||X||
|`TEXT-POLE-NUMBER-1.200`|white|Standard|X||X||
|`TEXT-ROADNAMES-1.500`|white|Standard||X|X||
|`SETOUT1`|yellow|Extended|||X|Alternative setout|
|`CUTLINE`|13|Extended|X|X|X|Cutline to another viewport|
|`SECONDARY-VISIBILITY`|white|Extended|||X|"Secondary visibility" block|
|`DUCTBOXES-EXISTING`|magenta|Extended|X|X|X|Existing ductboxes|
|`DUCTBOXES-REMOVE`|8|Extended|X|X|X|Ductboxes to be removed|
|`DUCTBOXES-UTILISE`|30|Extended|X|X|X|Ductboxes to be re-used|
|`DUCTS-EXISTING`|magenta|Extended|X|X|X||
|`DUCTS-REMOVE`|8|Extended|X|X|X||
|`DUCTS-UTILISE`|30|Extended|X|X|X||
|`HFS-GREY`|8|Extended|X|X|X||
|`LOOPS-EXISTING`|magenta|Extended|X|X|X||
|`LOOPS-REMOVE`|8|Extended|X|X|X||
|`LOOPS-UTILISE`|30|Extended|X|X|X||
|`SIGNALS-EXISTING`|magenta|Extended|X|X|X||
|`SIGNALS-REMOVE`|8|Extended|X|X|X||
|`SIGNALS-UTILISE`|30|Extended|X|X|X||
|`SOCKETS-EXISTING`|magenta|Extended|X|X|X||
|`SOCKETS-REMOVE`|8|Extended|X|X|X||
|`SOCKETS-UTILISE`|30|Extended|X|X|X||
|`TACTILES-EXISTING`|magenta|Extended|X|X|X||
|`TACTILES-REMOVE`|8|Extended|X|X|X||
|`TACTILES-UTILISE`|30|Extended|X|X|X||
|`TEXT-DETECTORS-1.500`|white|Extended||X|X||
|`TEXT-DUCTS-1.200`|green|Extended|X||X||
|`TEXT-LEADER-1.200`|white|Extended|X||X||
|`TEXT-LOOPS-1.200`|red|Extended|X||X||
|`TEXT-PHASES-1.500`|white|Extended||X|X||
|`TEXT-POLE-NUMBER-1.500`|white|Extended||X|X||
|`TEXT-ROADNAMES-1.200`|white|Extended|X||X||

