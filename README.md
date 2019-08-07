# Additional Documentation For Making a GAN Paint Scratch Block

----
## Contents
* Introduction
* What is GAN Paint? 
* What is Scratch? 
* How to make Scratch extensions
* The current state of the GAN Paint block
* How to make custom field types
* Other notes

----
## Introduction
Hi, I'm Philip Tegmark, the UROP who was working on this project during summer 2019. The project is to take [GAN Paint](http://gandissect.res.ibm.com/ganpaint.html?project=churchoutdoor&layer=layer4) and put it in a Scratch block. I got a lot of the work done, but there is still more to do, which I will outline here. I will also explain how to get started making Scratch extensions in the first place, and some other relevant information. If you have any questions, feel free to contact me at my Kerberos email (ptegmark at mit dot-edu), and I'll be happy to help. 

----
## What is GAN Paint? 
GAN Paint is a tool that has used GANs (Generative Adversarial Networks) to generate 16 photorealistic images of churches. By using the various brushes provided, and then shading in the image, the you can tell GAN Paint to add or remove certain features to/from different parts of the image, and GAN Paint will alter the image accordingly. I recommend that you play around with it for a few minutes to see what I'm talking about. 


----
## What is Scratch? 
I would describe Scratch as a programming language for kids, developed by the Lifelong Kindergarten Group at the MIT Media Lab. It uses blocks instead of lines of code (which is nice because that eliminates syntax errors), and is overall more intuitive to understand. You can make all sorts of projects in Scratch, and then share them on the [Scratch website](scratch.mit.edu). Scratch can do most of what other programming languages can do, although a Scratch file can only be run inside the Scratch editor. Scratch's other downsides are that it is very slow at math when compared to other programming languages, and that (as far as I am aware) it cannot read or write to outside files. 

For more information, check out Scratch's about page [here](https://scratch.mit.edu/about). 

Or try using Scratch [here](https://scratch.mit.edu/projects/editor/?tutorial=getStarted). If you have never used Scratch before, I would highly recommend that you play around with it for an hour, and at least learn what the following are: blocks, sprites, costumes/backdrops, and the Stage. Try creating at least one new sprite, write at least 1 script for it, and draw a costume for it. Also try importing an image file from your computer as a new costume, since I think this feature may be of interest down the line for the GAN Paint extension. 

The latest version of Scratch (and the one that we'll be working with) is Scratch 3. Scratch is written primarily in JavaScript, and has both an [online editor](https://scratch.mit.edu/projects/editor/?tutorial=getStarted) and an [offline editor](https://scratch.mit.edu/download/). The repositories for the code to Scratch's online editor are publicly available on GitHub, at [https://github.com/LLK/](https://github.com/LLK/). 

Scratch has various different types of blocks. They are: Motion, Looks, Sound, Events, Control, Sensing, Operators, Variables, and My Blocks. However, you can make extensions to Scratch. An extension adds a new set of blocks with their own functionality. For example, the Translate extension lets you use Google Translate to translate text into different languages. 

Only 11 extensions are officially supported by Scratch, so any extensions you make (unless later incorporated into Scratch by the Scratch team) can only be used on your computer. For more information, see the Scratch 3 Extensions Documentation [here](https://github.com/LLK/scratch-vm/blob/develop/docs/extensions.md). 

----
## How to make Scratch Extensions

To set up everything you need to make Scratch extensions, follow the instructions given in [this tutorial](https://scratch.mit.edu/discuss/topic/336496/). Before you begin the tutorial, however, you will need to make sure that you have both Git and npm (Node Package Manager) installed on your computer. If they are not installed and you need help installing them, consult your supervisor for help, or try to figure it out yourself. 

Of the 4 directories listed in the tutorial, you will at least need to download and set up scratch-gui, scratch-vm, and scratch-blocks in order to be able to work on the GAN Paint extension. 

Also, in order to be able to use the "npm run prepublish" command listed in step 8 of the tutorial, you will need to be using Python 2 on your computer. This may require you setting up a virtual environment on your computer to run Python 2. If you don't know how to do this, talk to your supervisor, or try to figure it out yourself. 

----
Once you've successfully completed the tutorial, you can start making extensions! I highly recommend that you read through the Scratch 3 Extension documentation [here](https://github.com/LLK/scratch-vm/blob/develop/docs/extensions.md). 

If you want, there's also this tutorial on how to make a very basic Scratch extension [here](https://medium.com/@hiroyuki.osaki/how-to-develop-your-own-block-for-scratch-3-0-1b5892026421). It's not the best tutorial though, since the author omits a few steps. 

If you do use the tutorial, skip to the part called "Method #2. On your development environment". You should have also already done step 1 when you completed the previous tutorial, so you can skip step 1 too. 

Some information that the author of the tutorial omitted: 

* The first 3 code snippets and trees that he shows (namely block3.tree, index.js, and extension-manager.js) are all within the scratch-vm directory. 
* The next 2 code snippets/trees that he shows (namely index.jsx and block7.tree) are within the scratch-gui directory. 
* Add this code: 
```
import newBlockImageURL from './newblocks.png';
import newBlockButtonImageURL from './newblocks-small.png';
```
to the list of import statements at the top of scratch-gui/src/lib/libraries/extensions/index.jsx. 

* Ignore the next code snippet (block8.sh). In the terminal, cd into the scratch-gui directory, and then type "npm start" (without the quotation marks). 
* In case you're new to JavaScript, all that the function console.log() does is print its argument to the console. It's JavaScript's version of the print statement. 

----
Alright, provided that you're not planning on making your own field types, you should now be set up to make your own Scratch extensions, and be acquainted with how to do so. If you do need to create your own field types (or if you don't know what that means and would like to know), see the section below on how to do so. While the GAN Paint extension does use a new field type, I already set that up, so you shouldn't have to worry too much about it. 

----
## The current state of the GAN Paint block
The goal of my project was to make a Scratch block that would let you use the GAN Paint editor inside of Scratch, and then save the image that you create as either a Sprite costume or a background to the Stage. 

[Repository Links]

During my time working on the project, I created a new extension called GAN Paint, with 1 block. This block says "save [EDITOR] as a costume" where [EDITOR] is a clickable dropdown that reveals the GAN Paint editor. The block is supposed to save the GAN Paint editor's main image either as a backdrop of the Stage, or as a costume of the sprite that owns the block. However, the block does not yet do that. 



[Image of block?] 





Notes:
index.jsx help link should be changed
include list of links at bottom




UNFINISHED
