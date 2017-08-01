# cs-lisp - AutoCAD LISP Commands for automating tedious tasks
CS LISP Commands

## Installation
To use the tool, download a copy of the `.LSP` file and save it somewhere on your machine. I may, in future, setup a network share to allow me to push updates without the need to re-download the file.

Within AutoCAD click on;

  - Tools
  - Load Application
  - Contents... (lower right of the window, part of the "Startup Suite")
  - Add...
  - Locate the file
  - Open
  
The script should now load everytime you start AutoCAD.

## Available Commands

  1. [sts-layers](#sts-layers)
  1. [sts-layers-ext](#sts-layers-ext)
  1. [sts-200](#sts-200)
  1. [sts-500](#sts-500)
  1. [sts-1000](#sts-1000)
  1. [sts-lock](#sts-lock)
  1. [sts-unlock](#sts-unlock)

### sts-layers
#### This command can be used anywhere within the drawing (modelspace, paperspace, within a viewport).

Creates a 'standard' set of layers in AutoCAD which you would expect to need in a typical design drawing. 
The way the layers are named is important, as other commands within this tool refer to specific layer names.
Changing the names of layers within the code can have an adverse effect on other commands so care should be taken if you decide
to rename any of the pre-defined layers.

### sts-layers-ext
#### This command can be used anywhere within the drawing (modelspace, paperspace, within a viewport).

Creates an extended set of layers for more complex design drawings. It includes layers for items such as existing equipment
which is to be retained or reused. It also creates layers for non-standard text, such as roadnames in a 1:200 viewport.

### sts-200
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no active viewports.

The command will switch off (freeze) any layers which are not deemed to be required in a 1:200 viewport (such as roadnames). This command uses layer names to determine whether a layer should be switched off, hence it is important to use layers correctly, and not to rename layers which have been created using this tool.

### sts-500
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no 
active viewports.

The command will switch off (freeze) any layers which are not deemed to be required in a 1:500 viewport (such as pole numbers).
This command uses layer names to determine whether a layer should be switched off, hence it is important to use layers
correctly, and not to rename layers which have been created using this tool.

### sts-1000
#### This command can only be used when inside a viewport. It will not work when in modelspace, or within paperspace with no 
active viewports.

The command will switch off (freeze) any layers which are not deemed to be required in a 1:1000 viewport (such as pole numbers).
This command uses layer names to determine whether a layer should be switched off, hence it is important to use layers
correctly, and not to rename layers which have been created using this tool.

### sts-lock
#### This command can only be used in paperspace, not inside an active viewport.

The command will lock all viewports on the active layout, and switch off (freeze) the layer `STS_LAYOUT-VP2` as this layer is 
often used for viewports where the border should be hidden for aesthetic purposes. 

### sts-unlock
#### This command can only be used in paperspace, not inside an active viewport.

The command will switch on (thaw) layer `STS_LAYOUT-VP2` on the active layout, as this is commonly used for viewports with hidden borders (for aesthetic value). It will then unlock (Display Locked Off) all viewports on the active layout. This command relies on proper use of layer names, as it will only thaw the `STS_LAYOUT-VP2` layer. If you have frozen any other layers within the paperspace, these will stay hidden and thus not be unlocked.
