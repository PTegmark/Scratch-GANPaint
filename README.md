# Additional Documentation For Making a GAN Paint Scratch Block


## Contents
* Introduction
* What is GAN Paint? 
* What is Scratch? 
* How to make Scratch extensions
* The current state of the GAN Paint block
* The blocks playground
* How to make custom field types
* Other notes


## Introduction
Hi, I'm Philip, the UROP who was working on this project during summer 2019. The project is to take [GAN Paint](http://gandissect.res.ibm.com/ganpaint.html?project=churchoutdoor&layer=layer4) and put it in a Scratch block. I got a lot of the work done, but there is still more to do, which I will outline here. I will also explain how to get started making Scratch extensions in the first place, and some other relevant information. If you have any questions, feel free to contact me at my Kerberos email (ptegmark at mit dot-edu), and I'll be happy to help. 

A quick note: for clarity, I will be disregarding the English grammar rule of including punctuation from outside a quote within the quotation marks should it immediately follow the quote. I will instead by leaving all punctuation that is not part of the quote outside the quotation marks. For example, if "field_ganpaint.js" is a file that I want you to open, I will type: 
>Please open "field_matrix.js". 

instead of typing: 

>Please open "field_matrix.js." 

which is what English grammar would dictate that I do. 


## What is GAN Paint? 
GAN Paint is a tool that has used GANs (Generative Adversarial Networks) to generate 16 photorealistic images of churches. By using the various brushes provided, and then shading in the image, the you can tell GAN Paint to add or remove certain features to/from different parts of the image, and GAN Paint will alter the image accordingly. I recommend that you play around with it for a few minutes to see what I'm talking about. 



## What is Scratch? 
I would describe Scratch as a programming language for kids, developed by the Lifelong Kindergarten Group at the MIT Media Lab. It uses blocks instead of lines of code (which is nice because that eliminates syntax errors), and is overall more intuitive to understand. You can make all sorts of projects in Scratch, and then share them on the [Scratch website](scratch.mit.edu). Scratch can do most of what other programming languages can do, although a Scratch file can only be run inside the Scratch editor. Scratch's other downsides are that it is very slow at math when compared to other programming languages, and that (as far as I am aware) it cannot read or write to outside files. 

For more information, check out Scratch's about page [here](https://scratch.mit.edu/about). 

Or try using Scratch [here](https://scratch.mit.edu/projects/editor/?tutorial=getStarted). If you have never used Scratch before, I would highly recommend that you play around with it for an hour, and at least learn what the following are: blocks, sprites, costumes/backdrops, and the Stage. Try creating at least one new sprite, write at least 1 script for it, and draw a costume for it. Also try importing an image file from your computer as a new costume, since I think this feature may be of interest down the line for the GAN Paint extension. 

The latest version of Scratch (and the one that we'll be working with) is Scratch 3. Scratch is written primarily in JavaScript, and has both an [online editor](https://scratch.mit.edu/projects/editor/?tutorial=getStarted) and an [offline editor](https://scratch.mit.edu/download/). The repositories for the code to Scratch's online editor are publicly available on GitHub, at [https://github.com/LLK/](https://github.com/LLK/). 

Scratch has various different types of blocks. They are: Motion, Looks, Sound, Events, Control, Sensing, Operators, Variables, and My Blocks. However, you can make extensions to Scratch. An extension adds a new set of blocks with their own functionality. For example, the Translate extension lets you use Google Translate to translate text into different languages. 

Only 11 extensions are officially supported by Scratch, so any extensions you make (unless later incorporated into Scratch by the Scratch team) can only be used on your computer. For more information, see the Scratch 3 Extensions Documentation [here](https://github.com/LLK/scratch-vm/blob/develop/docs/extensions.md). 


## How to make Scratch Extensions

To set up everything you need to make Scratch extensions, follow the instructions given in [this tutorial](https://scratch.mit.edu/discuss/topic/336496/). Before you begin the tutorial, however, you will need to make sure that you have both Git and npm (Node Package Manager) installed on your computer. If they are not installed and you need help installing them, consult your supervisor for help, or try to figure it out yourself. 

Of the 4 directories listed in the tutorial, you will at least need to download and set up scratch-gui, scratch-vm, and scratch-blocks in order to be able to work on the GAN Paint extension. 

Also, in order to be able to use the "npm run prepublish" command listed in step 8 of the tutorial, you will need to be using Python 2 on your computer. This may require you setting up a virtual environment on your computer to run Python 2. If you don't know how to do this, talk to your supervisor, or try to figure it out yourself. 


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


Alright, provided that you're not planning on making your own field types, you should now be set up to make your own Scratch extensions, and be acquainted with how to do so. If you do need to create your own field types (or if you don't know what that means and would like to know), see the section below on how to do so. While the GAN Paint extension does use a new field type, I already set that up, so you shouldn't have to worry too much about it. 


## The current state of the GAN Paint block
The goal of my project was to make a Scratch block that would let you use the GAN Paint editor inside of Scratch, and then save the image that you create as either a sprite costume or as a background to the Stage. 

[Repository Links]

During my time working on the project, I created a new extension called GAN Paint, with 1 block. This block says "save [EDITOR] as a costume" where [EDITOR] is a clickable dropdown that contains the GAN Paint editor. 

[Image of GAN Paint block and dropdown]

The block's opcode (what happens when the block gets activated) currently does nothing. Once operational, however, the block's opcode should save the GAN Paint editor's main image either as a backdrop of the Stage, or as a costume of the sprite that owns the block. 

What The Block Currently Does: 

* Displays a dropdown GUI for the GAN Paint editor. This dropdown field is of the type "ganpaint", a new field type that I created for this project. 
* The dropdown GUI has: 11 buttons with text on its left hand side (I will inventively refer to these buttons as "text buttons"), the main image that is being edited in the middle, and 16 buttons on the right hand side for selecting which starting church image to use (I will creatively refer to these buttons as "church selection buttons"). 
* The first 7 of the text buttons (labeled "tree" through "dome") are used to select which brush you are using. They act as a set of radio buttons (so that only 1 of the 7 can be selected at any given time). A string called "brushState" records which of the 7 brush buttons is currently selected (see scratch-blocks/core/field_ganpaint.js). 
* The 8th and 9th text buttons (labeled "draw" and "remove", respectively) are for the user to select whether they are adding or removing a given feature from the main image. These two buttons act like radio buttons (so that only one of two can be selected at any given time). A string called "drawingState" records which of these two buttons is currently selected (see scratch-blocks/core/field_ganpaint.js). 
* When clicked, the 11th text button (labeled "reset") resets the main image to display the original version of the image currently being edited. 
* If the user drags the mouse across the main image, the coordinates of all points within the image that the mouse drags over will be stored in an array called "selectedPoints". selectedPoints is reset every time that the main image is clicked on or dragged. Currently, selectedPoints is simply being printed to the console once the user releases the mouse after dragging it across the main image. However, in the future, this should instead cause selectedPoints to be sent to the GAN Paint server, along with brushState, drawingState, and the current main image. 
* When any given church selection button is clicked, the main image will be set to display the corresponding image. 

What The Block Still Needs To Do: 

* The 10th text button (labeled "undo"), can be clicked, but currently doesn't do anything besides print the message "Undo button clicked. " to the console. It needs to be properly implemented as an undo button. This undo button will ideally function by storing previous versions of the main image on the user's computer, and accessing them as necessary when the undo button is clicked. Of course, the actual implementation of the undo button will be up to you (assuming that you are the one who will finish this project). Insert the code for the undo button within the function "Blockly.FieldGANPaint.prototype.onButtonClick" in the file "scratch-blocks/core/field_ganpaint.js", at the spot that says: 

```
// ***
// Undo button NOT YET IMPLEMENTED. Add the necessary code here. 
// ***
```

* The ganpaint field does not yet communicate with the GAN Paint server. Ultimately, the field will have to send the main image, along with the information contained in selectedPoints, brushState, and drawingState, to the GAN Paint server whenever the user finishes dragging the mouse across the main image. To help implement this, you will need to add some code to the function "Blockly.FieldGANPaint.prototype.onMouseUp" within the file "scratch-blocks/core/field_ganpaint.js". Add the code at the part of the function where this comment is found:  

```
// ***
// Send this.selectedPoints, this.brushState, this.drawingState, and the main image to the GAN 
// Paint server, and get the new main image back from the server. NOT YET IMPLEMENTED. 
// ***
```

* The field will also have to get a response from the GAN Paint server containing the new main image, which the field will then display as the new main image. The function "Blockly.FieldGANPaint.prototype.setValue" (in the file "scratch-blocks/core/field_ganpaint.js") might be of use in displaying the image from the GAN Paint server as the new main image, although you will need to modify the function first to make it better suit your needs. 


Undo, talk to server, save image, Safari, highlight dragged part of main image, etc. 



[Image of block?] 






index.jsx help link should be changed
include list of links at bottom




UNFINISHED
