# flatpack
There is not a lot to unpack. Like... for real.

https://user-images.githubusercontent.com/66600478/183345870-d31b0fc4-497d-4f51-bbe5-db83cf9a2b46.mp4

https://user-images.githubusercontent.com/66600478/183403170-353edabf-4271-400f-9db7-fafc17dc54a0.mp4

https://user-images.githubusercontent.com/66600478/183500945-2cf039b2-9133-45dd-af40-6a08152f20f8.mp4

(flatpack and flathead printing gridfinity parts; flatpack with the old hotendsetup (4010 hotend, 3010 for partcooling)

###### Small Announcement before we go on here:

Mellow will make a fully machined adaptation of flatpack, this machine will be called the Mellow M1. Apart from still being able to be folded,
it comes with:
- a new board which is basically a Fly D5 and a Fly Pi Lite v2 married together on the size of the D5 (im very much looking forward
to that board, apart from the cnc'ed adaption of my design is running Flipper ofc; they could do rrf, but we will see)
- a 2.8" touchscreen at the bottom, and a 1.3" touchscreen at the hotend for quick filament changes and quick heating

https://youtu.be/e8mjv9e-qzc (you see two prototypes here at TCT Asia)  
https://youtu.be/q5g9Ud7NPts?si=8peJaGWEXCFL_qLP&t=52 (starting at the timestamp you see one prototype again)  
Crowdfounding starts probably in november or decembre of 2023. :)  
Im also in no way affiliated with mellow, i dont get anything out of this EXCEPT one of the finished mellow m1. Which im looking very much forward too.  
And now lets go on with flatpack here:

###### Technical Data:

- folded volume of roughly 220x210x75mm (so, make sure your spoolbox has these
  inner dimensions at a minimum, as there are some with slightly different dimensions)
- buildvolume of 120x114x114mm, so 1.6 liters
- heated bed that can reach up to 110°C
- Hotend capable of temperatures up to 300°C, if you choose the Copper NF Smart 500°C
- powered through an external (!) powerbrick with 150W, uses 100W max
- the design can theoretically use an AC bed, and consequently a small psu
  enabling everything to fit in one box. 
  For safety reasons I deemed mains wiring to be to dangerous and
  as a result I have selected a DC powered bed to make the build more accessible to the average user.
- Flatpack is fully reprap, meaning that you can print every printable part of flatpack on flatpack.
 

###### Firmware:

- Marlin configuration is available at [firmware/Marlin](firmware/Marlin). Tested with the AIO II.

###### Some words of caution:


- As you can imagine, a fixed bed cantilever is not optimal for fast speeds or
  larger printvolumes.
- Thankfully, we dont have to deal with a large printvolume. Speed and Acceleration are however a concern here.
Rapid changes in direction can be challenging for any motion system and even more so with this motion system.
As a result consider setting your print speeds and accelerations conservatively.
- So why the fixed bed cantilever? Because it simply looks cool.
- Dual rails are used for load distribution on both the Y and Z axis; these can be a bit
  tricky to align, and can and will cost you a few grey hairs.
- last word of caution: I encourage you to take your time building flatpack, and make certain everything is square, and all the motion system moves smoothly, while everything that should not move is rigid and secure without much play or flexing. 
- its a (functioning) prototype, and will continue to undergo active development and improvements.
- thanks to the user awesomeka001 we now know, that the xz-joiner is indeed printable on flatpack, so flatpack is now full reprap. Meaning if you have one flatpack, you can print all parts of it on that machine.

## This is free for everyone to download and build, or of course to just look at it and take some inspiration or ideas from it. :)

###### ToDo-List
- the XY-joiner is realtively complicated to print and cleanup. One day ill find an easier way to do that.
- flatpack has no spoolholder. The goal is to design a spoolholder, that can travel along in the spoolbox along side the filament you´re carrying with you
- we now have an adapter to fit a Mellow Orbiter Extruder. One day i will make a new carriage for that, so we dont need an adapter, but for now the adapter works well enough, and its still foldable.
- Further optimization of the fanduct/part cooling. I have encountered difficulties designing the fanduct. I have started a repo for ["caterpillar"](https://www.github.com/eponra/caterpillar), which is a partcoolingsolution I designed using CF tubes, which I intend to merge into flatpack eventually.
- the current 3 point-bedmounting is not optimal, as it is simply drilled and tapped M3 threaded holes. I would like to find a better solution down the road.
- you can twist the base and that's not supposed to happen! One solution is to drill through the aluminium extrusions to get screws into the extrusions under the bed. I am convinced there is probably a better solution.

![prototyping](https://user-images.githubusercontent.com/66600478/183500214-0299970e-6995-443d-a172-a0e379b12d8e.jpg)
(for a break, the latest switch from a totally different hotend/partcooling setup to the actual one. Thats not all steps, just a few)

## Design files

[Fusion 360](https://a360.co/3vLUHdm)

This link is sadly viewable only, as I am using the free version of Autodesk
Fusion 360.

The link to the latest stable .step file (Ver7) is [here](https://drive.google.com/file/d/1a2EOg3HK1r-n8Omy-1yQx4LHCDSig2ma/view)

###### Changelog:
- from V6 to V7 where changes made to the XZ-joiner, the left Frontmount (so that we can use a shorter front extrusion, this lets us use only 4 300mm 1515 extrusions), i added the screwingholes to the drawing so you know where
to add the extra screws for the base, i added a component which only includes all parts that have inserts + the heated inserts (in a slightly exploded configuration, so you can better see where every insert needs to be), slightly changed
X-Tensioner (just to make one M3-head flush with the print)
- from V4 to V6 there are changes in the X and Y tensioner. Both clamps now feature copper pressfit bushings, and M3 rods. If you started printing already, you only have to watch out for "Y-Tensioner Clamp long v2" and "X-Tensioner Clamp v2".


###### A few words of gratitude:

The initial idea of a fixed bed cantilever was not mine, but came from
[apsu](https://github.com/apsu), a constant resident of the
#reprap-and-custombuilds channel in the [3D Printing
discord](https://discord.gg/pQRvDQHk67).  With this i built flathead, the
bigger brother of flatpack, and without [apsu](https://github.com/apsu/) none
of this would have happened.

The initial idea to make this foldable, came from @Ogre.

Also, special thanks to [oliof](https://github.com/oliof/), another extremely
helpful member and Mod of 3D printing, and also a walking dictionary on obscure
3D printing and mechanical knowledge.  And of course, a thank you to everyone
else i forgot from 3D printing and especially the #reprap-and-custombuilds
channel.

Also, everyone nagging me multiple times a day in the super secret
#wheres-flatpack channel...


Flatpack is licensed under [GPL v3.0](/LICENSE).
