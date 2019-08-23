# Documentation For Making a GAN Paint Scratch Block


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
Hi, I'm Philip, the UROP who was working on this project during summer 2019. The project is effectively to take [GAN Paint](http://gandissect.res.ibm.com/ganpaint.html?project=churchoutdoor&layer=layer4) and put it in a Scratch block. I got a lot of the work done, but there is still more to do, which I will outline here. I will also explain how to get started making Scratch extensions in the first place, and some other relevant information. If you have any questions about anything, feel free to contact me at my Kerberos email (ptegmark at mit dot-edu), and I'll be happy to help. 

If you are going to work on completing the GAN Paint extension, please go through all sections of this document. If, however, you're only here to learn how to make Scratch extensions, you need only go through the sections "What is Scratch?" and "How to make Scratch extensions", as well as "The blocks playground" and "How to make custom field types" if you plan on creating your own field type(s) as well. 

Also, a quick note: as you are probably aware, when you follow up something in quotes with a punctuation mark, the English language dictates that the punctuation mark must also be included within the quotation marks, even if said punctuation mark was not part of the quote to begin with. For example, if I wanted to tell you that "orange" was the only word that my friend said, the English language dictates that I write: 

>My friend only said the word "orange." 

with the period included inside the quotation marks, even though the period is not part of what I am actually quoting. 

For clarity, I will be disregarding this rule, and keeping all punctuation that is not part of the quote outside of the quotation marks. So, for example, if "field_ganpaint.js" is a file that I want you to open, I will type: 

>Please open "field_matrix.js". 

instead of typing: 

>Please open "field_matrix.js." 

which is what English grammar would dictate that I do. 


## What is GAN Paint? 
[GAN Paint](http://gandissect.res.ibm.com/ganpaint.html?project=churchoutdoor&layer=layer4) is a tool that has used GANs (Generative Adversarial Networks) to generate 16 photorealistic images of churches. By using the various brushes provided, and then shading in the image, the you can tell GAN Paint to add or remove certain features to/from different parts of the image, and GAN Paint will alter the image accordingly. I recommend that you play around with it for a few minutes to see what I'm talking about. 



## What is Scratch? 
I would describe Scratch as a programming language for kids, developed by the Lifelong Kindergarten Group at the MIT Media Lab. It uses blocks instead of lines of code (which is nice because that eliminates syntax errors), and is overall more intuitive to understand than most other programming languages. You can make all sorts of projects in Scratch, and then share them on the [Scratch website](scratch.mit.edu). Scratch can do most of what other programming languages can do, although a Scratch file can only be run inside the Scratch editor. Scratch's other downsides are that it is very slow at math when compared to other programming languages, and that (as far as I am aware) it cannot read or write to outside files. 

For more information, check out Scratch's About page [here](https://scratch.mit.edu/about). 

Or try using Scratch [here](https://scratch.mit.edu/projects/editor/?tutorial=getStarted). If you have never used Scratch before, I would highly recommend that you play around with it for an hour, and at least learn what the following are: blocks, sprites, costumes/backdrops, and the Stage. Try creating at least one new sprite, write at least 1 script for it, and draw a costume for it. Also try importing an image file from your computer as a new costume, since I think this feature may be of interest down the line for the GAN Paint extension. 

As of when I wrote this, the latest version of Scratch (and the one that we'll be working with) is Scratch 3. Scratch is written primarily in JavaScript, and has both an [online editor](https://scratch.mit.edu/projects/editor/?tutorial=getStarted) and an [offline editor](https://scratch.mit.edu/download/). The repositories for the code to Scratch's online editor are publicly available on GitHub, at [https://github.com/LLK/](https://github.com/LLK/). 

Scratch has various different types of blocks. They are: Motion, Looks, Sound, Events, Control, Sensing, Operators, Variables, and My Blocks. However, you can make extensions to Scratch. An extension adds a new set of blocks with their own functionality. For example, the Translate extension lets you use Google Translate to translate text into different languages. 

Only 11 extensions are officially supported by Scratch, so any extensions you make (unless later incorporated into Scratch by the Scratch team) can only be used on your computer. For more information, see the [Scratch 3 Extensions Documentation](https://github.com/LLK/scratch-vm/blob/develop/docs/extensions.md). 


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
The goal of my project was to make a Scratch block that would let you use the GAN Paint editor inside of Scratch, and then save the image that you created either as a sprite costume or as a background to the Stage. 


[Repository Links]


During my time working on the project, I created a new Scratch extension called GAN Paint, which has only 1 block. This block says "save [EDITOR] as a costume" where [EDITOR] is a clickable dropdown that contains the GAN Paint editor. Here's a picture of the block with the dropdown opened: 


[Image of GAN Paint block and dropdown]


The block's opcode (the opcode is the function runs when the block gets activated) currently does nothing besides print some stuff to the console (this is not important, and you can remove my "console.log" statement with no repercussions). Once completed, however, the block's opcode is supposed to save the GAN Paint editor's main image either as a backdrop of the Stage, or as a costume of the sprite that owns the block. 

What The Block Currently Does: 

* It displays a dropdown GUI for the GAN Paint editor. This dropdown field is of the type "ganpaint", a new field type that I created for this project. 

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

* Continuing off of the previous point, the ganpaint field will also have to get a response from the GAN Paint server. This response should contain the new main image, which the ganpaint field will then display as the new main image. The function "Blockly.FieldGANPaint.prototype.setValue" (in the file "scratch-blocks/core/field_ganpaint.js") might be of use in displaying the image from the GAN Paint server as the new main image, although you will need to modify the function first to make it better suit your needs. 

* When activated, the GAN Paint block should (it does not currently do this) save its main image as either a sprite costume or as a Stage backdrop. To accomplish this, you will need to add code to the GAN Paint block's opcode (i.e. the function "saveGANPaintImage" within the file "scratch-vm/src/extensions/scratch3_ganpaint/index.js"). Scratch does let the user import an external image to use as a costume--if you can figure out what JavaScript function it is that does this, you can probably use that function to save the main GAN Paint image as a costume or backdrop. 


[Where should they look for this function? What should they do about your commented out code in index.js?]


* The SVG images that I have used to create the GAN Paint field don't display properly in Safari. In Safari, you just get this instead: 


[Include the appropriate picture here]


This needs to be fixed. You will need the GAN Paint extension to function properly in Firefox, Chrome, Safari, and Microsoft Edge (possibly also Internet Explorer and Opera--ask whoever is in charge (presumably Katherine Gallagher) about what browsers the GAN Paint extension needs to function properly in). Right now, the SVG images in question do display properly in Firefox though, I can guarantee that much. 

[What about Chrome and Edge?]

* On the [GAN Paint website](http://gandissect.res.ibm.com/ganpaint.html?project=churchoutdoor&layer=layer4), the main image is visibly shaded as the user drags their mouse over it. Currently, however, the ganpaint field in Scratch does not do so. So, if you have time, this should be implemented in the ganpaint field. To accomplish this, you will probably need to add code to the functions "Blockly.FieldGANPaint.prototype.onMouseDown" and "Blockly.FieldGANPaint.prototype.onMouseMove" in the file "scratch-blocks/core/field-ganpaint.js". 

* Optional: Depending on the circumstances for which it is to be used, the GAN Paint extension might eventually need to be viewable in other languages. This, however, is completely optional at this point, as it is not at all an immediate concern. 

Please read the section of this document called "The blocks playground" before you start making alterations to scratch-blocks/core/field_ganpaint.js, as the blocks playground will save you a lot of time. 

Good luck! And feel free to contact me if you have any questions (especially if I explained something poorly and/or forgot to mention something important). 


## The blocks playground

As you may remember from [this tutorial](https://scratch.mit.edu/discuss/topic/336496/) from the section "How to make Scratch Extensions", if you make a change to the scratch-blocks directory and want that change to be reflected in your local version of Scratch, you'll need to: 

* 1: Open the terminal and run the command "npm run prepublish" within the scratch-blocks directory. 
* 2: Also in the terminal, run the command "npm start" within the scratch-gui directory. 

This typically takes me about 3 minutes to do on my laptop, can be a pretty long time to have to wait just to see what effect your latest change to scratch-blocks had. But thankfully, the Scratch team has also created the blocks playground, which lets you view the changes you've made to scratch-blocks almost immediately. 

The blocks playground is a tool that lets you test out your Scratch blocks without having to run "npm run prepublish" on scratch-blocks and without you having to load scratch-gui. To access it, just open the file 




## How to make custom field types

First off, what is a field type? A field type is 
NOT DONE




## Other notes

This section will contain various potentially useful pieces of information. 

[Include list of resources (including stuff like MDN Docs and W3 Schools, Inspect Element, console.log, Argument Types and Block Types)]

[Include List of All Hyperlinks from previous sections]








index.jsx help link should be changed





UNFINISHED




