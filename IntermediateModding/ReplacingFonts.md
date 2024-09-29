# Replacing Fonts
Fonts are easy to replace, and there are 2 methods for it which I will cover in this guide.

1. Direct FontFace replace - just like a texture swap, but you import your font (`.ttf` or `.otf` file) into the correct folder and name it accordingly.
2. Font dummy (font family) - dummy the Font asset and set our own fonts for each type.

## Method 1 - Direct Replace
Direct font replacement is exactly the same as a texture swap, where the modified/new asset is imported into UE, named and placed in the correct folder to match the game files.

### Identify the Font and/or FontFace
First, we want to find the Font and the actual FontFace.
In this instance, the found Font has multiple types, and the one we're particularly interested is `Default`.

![](/Media/FontReplace/1.png)

### Import New Asset
1. Drag the font file into the Content Browser tab inside the UE project.

![](/Media/FontReplace/2.png)

2. A window prompt will appear, press `No All` to avoid generating a Font asset for each imported FontFace.

![](/Media/FontReplace/3.png)

3. Ensure the folders and asset name(s) match with the game files.

![](/Media/FontReplace/4.png)

### Pack it
Package the asset and test results.

![](/Media/FontReplace/5.png)

For more information about how to package your mod, view [Cooking Content guide](/IntermediateModding/CookingContent.md).<br>

(don't forget to name your mod with `_P` in its name)

## Method 2 - Font Asset
Each font type has to be contained in a `Font` asset, similarly to Font Family with optional styles like Italic, Bold, and others. <br>And each type is called FontFace (the imported `.ttf` or `.otf`).

### Font Asset
1. Right click -> User Interface -> Font

![](/Media/FontReplace/6.png)

2. Name it to match with the game files (look in FModel).

![](/Media/FontReplace/7.png)

Font assets will contain a handful of FontFace assets with a named style.<br>
In this instance, it contains different styles like Default, Black, BlackItalic, Bold, and others.

3. Import any corresponding/related fonts that would fit with those styles or names.

> [!NOTE]  
> You decide where each font goes into which style/category.<br>
> And you can set the same one to all of them if you want.

![](/Media/FontReplace/8.png)

4. Open the Font asset and click `Add Font`, name it the same as in FModel and specify your own FontFace to it (could be custom or actual one).

5. Repeat step 4 until all Font Family items are set.

![](/Media/FontReplace/9.png)

### Pack it
Package the asset and test results.

![](/Media/FontReplace/10.png)

For more information about how to package your mod, view [Cooking Content guide](/IntermediateModding/CookingContent.md).<br>

(don't forget to name your mod with `_P` in its name)