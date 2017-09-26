# Hung-yu's implementation of [*Robot Fun Police*](http://graphics.cs.cmu.edu/courses/15-466-f17/game2-designs/jmccann/) for game2 in 15-466-f17

![alt text](https://github.com/heyimglory/15-466-f17-base2/blob/master/screenshots/move.png)

## Asset Pipeline

The asset pipeline of this game is based on export-meshes.py provided in Base2. It reads out the data of the vertices from a blender file and writes them into binary blob files, which are the data of the meshes and the data of the scene. The blob files can be read by the main program directly because their format are adjusted to meet the loading functions. The part regarding the color of the verices is referencing export-layer.py.

## Architecture

After loading the data of the models from the blob files, a stack of the components of the robot and another stack of balloons are constructed before entering the loop. Inside the loop, the the movement of the robot would be up dated according to user input, and then whether the balloons are poped and the bouncing of the balloons are also handled.

## Reflection

The part that I spended most time in this assignmet is trying to figure out how to export the models from blender. There were something needed to pay attention to regarding the path. Another part that took much time is trying to render the models with color. Adjustments were required in many files. Trying to recall how to detect the keyboard movement without relying on polling also took me quite a while. I kind of like the way that the balloons bounce although I only apply really simple computation to control their tranlation. The part I'm not really satisfied with is that I didn't remove the balloons from the scene when they are poped. I just scaled the dimensions to 0 so that it can't be seen. I would try to figure out how to remove them from the scene if I get more time.

I think the design document is brief but covered almost everything about the game since it not a complicated one. The only part I need to guess is what shoud I do when it says "the game is over."

# About Base2

This game is based on Base2, starter code for game2 in the 15-466-f17 course. It was developed by Jim McCann, and is released into the public domain.

## Requirements

 - modern C++ compiler
 - glm
 - libSDL2
 - libpng
 - blender (for mesh export script)

On Linux or OSX these requirements should be available from your package manager without too much hassle.

## Building

This code has been set up to be built with [FT jam](https://www.freetype.org/jam/).

### Getting Jam

For more information on Jam, see the [Jam Documentation](https://www.perforce.com/documentation/jam-documentation) page at Perforce, which includes both reference documentation and a getting started guide.

On unixish OSs, Jam is available from your package manager:
```
	brew install ftjam #on OSX
	apt get ftjam #on Debian-ish Linux
```

On Windows, you can get a binary [from sourceforge](https://sourceforge.net/projects/freetype/files/ftjam/2.5.2/ftjam-2.5.2-win32.zip/download),
and put it somewhere in your `%PATH%`.
(Possibly: also set the `JAM_TOOLSET` variable to `VISUALC`.)

### Bulding
Open a terminal (on windows, a Visual Studio Command Prompt), change to this directory, and type:
```
	jam
```

### Building (local libs)

Depending on your OSX, clone 
[kit-libs-linux](https://github.com/ixchow/kit-libs-linux),
[kit-libs-osx](https://github.com/ixchow/kit-libs-osx),
or [kit-libs-win](https://github.com/ixchow/kit-libs-win)
as a subdirectory of the current directory.

The Jamfile sets up library and header search paths such that local libraries will be preferred over system libraries.
