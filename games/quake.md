# How to install Quake on ubuntu

NOTICE: you must have the original files from a CD to make this game work. 

## Install darkplaces

To install darkerplaces on ubuntu use the following command
```
sudo apt-get install darkplaces
```

## moving files onto disk

create a home for the game 
```
mkdir -p ~/game/quake
```

copy the files into this folder

## Playing the game

use one of the following basedirs to play the different versions of the game
```
darkplaces -basedir ~/game/quake

darkplaces -basedir ~/game/quake -game malice

darkplaces -basedir ~/game/quake -game qzone
```
