# Introduction

This project is about the presentation of an interactive 3D model of an armchair. The page is composed by two elements: a canvas, where stand the armchair, and a menu, through which the users can modify the color and the material of the model.

The project source code is entirely contained in the "index.html" file.  

# Development

1.  First, we choose the model according to the requirements: it has 36.000 vertices and was founded online, available for non-commercial use.
We choose an armchair because it can be made of several materials and all possible colors, so we could give the users lot of alternatives.
    
2.  Then, we focused on the context. We decided to put the armchair in the center of an empty room, made only by white walls and a parquet, to make sure the attention of the user will be captured by the armchair, and not disturbed by other things.

3.  We added a sfot white environmetal light but, since it was still too "grey", we decided to add two supplementar directional lights
towards the walls of the room. These lights were "outside" the shaders and that's the main reason why later we removed them. 
At this point we were using shaders only for rendering the armchair.
    
4.  Using "B2M" program, we create all the necessary normal maps, expecially those for leather and fabric.

5.  We wrote down our personal shaders focusing on normals, roughness, specular and diffuse terms for both the materials. Using the
shaders we added to the scene three point lights: one on the right of the armchair, one on the left side, and the last above it. In this way we wanted to make sure that the 3D model was well illuminated. 
    
    The shader equations we used are those studied during the course but, at this point, only the armchair was using these.

6.  To justify the presence of the three point lights we modeled three lamps and then place them in the scene, according to light positions. 

7.  We build a very basic GUI to allow the user change material between leather and fabric, and change the color between all possible combinations of RGB.

8.  Since the ambient and directional lights added at point 3 were given an uniform and innatural illumination to the scene, we decided to remove them and render EVERY object using the three point lights in our vertex and fragment shaders. 

9.  We create a special material for each object using the diffuse maps as values for cdiff, so that now is not necessary to set them manually. 
   
10.  We focused on the ambient occlusion: we first create the AO maps with "B2M" and then apply each map to the corresponding object using shaders. 

11. We improved the GUI and added some element in the page to make it seem an e-commerce site.



# ProductVisualization

![Image from Ford Configurator, developed in three.js](images/ford-configurator.jpg)

READ CAREFULLY this document BEFORE you start!

## Prerequisites

- read carefully all slides and notes up to lecture 15 before you start. Try the proposed exercises. As you progress in the project, read also lectures up to 18 (post processing).

## Hints

- Try to work out a basic project which satisfies all requirements well before the deadline and as soon as possible: you will then use the remaining time to refine, improve and polish.
- If you are stuck for too much time on a problem, ask for help, preferably in the forum.
- the process is as important as the result. Use this project to learn a workflow, and how to use tools effectively. Experiment, and try to come up with efficient, elegant, and well commented code.
- commit often in your git repository and with meaningful comments.
- do not choose too complex products with many materials. 2-4 materials are enough.


## Goals

The well-known ACME company has asked you to build a product **Web visualizer / configurator** for its new e-commerce site. Before giving you the job, ACME wants to evaluate how faithfully you can visualize and configure products.  ACME sells everything, so you can choose whatever kind of product you want for the demonstration.

Your goal is to build a Web application (a HTML page) that:

- visualizes a product in 3D using three.js, using PBR equations and materials;
- allows the user to inspect the product (e.g. by orbiting the camera around it), and change some material on it by choosing from a few alternatives.

Try to make it look like a simple, but real portion of an e-commerce site, not a three.js example: choose carefully colors, fonts, images, and icons, also taking inspiration from real web sites.

## Steps (read CAREFULLY)

3. Prepare, and add to the repository, a journal.md file for logging your progress and choices.

1. Choose a product for which: (i) you can easily build a 3D model, or (ii) you can download a 3D model which you have the right to use in non-commercial applications. The model should not be too complex (not more than 50k vertices) and in some format that three.js can read. [Three.js examples](https://threejs.org/examples/) provide a list of loaders for different formats: beware that not all of them work perfectly, and you might have to try with different formats.

2. Design the lighting for the product. Products in web sites and catalogues are photographed using strategically placed lights that enhance details and shape. For example, [searching google images for product photography lighting](http://www.google.com/images?q=product+photography+lighting) will show you a number of real-world lighting setups that are used for products. In your lighting setup, you can use whatever you want, from punctual lights, to environment lighting, or light maps, or any combination of them.

3. Design the PBR materials for the product. You can use PRB textures found anywhere, or produce them, e.g. with Substance Designer or B2M. If you use textures authored by someone else, just make sure you have the rights for using them in our context (non-commercial application). At least one of the materials must have 2-3 alternatives (e.g. different colors, or materials).

4. Build the application that renders the chosen 3D model, with the designed lighting setup and materials, and an user interface for selecting the material between the alternatives. **Important: you can implement this step in two different ways**:

    a. using three.js built-in lights and materials (MeshStandardMaterial or MeshPhysicalMaterial), without writing any shader. In this case, your final report **must include** the equations of the BRDF and rendering equations that you are using. In other words, you have to dig into three.js shaders to find which equations are used, and write them (in mathematical form, not using code);

    b. using shaders written by you, e.g. by extending the shaders we saw in the classroom. In this case, your report needs just to mention the kind of BRDF / lights you have implemented (no need to report the equations, unless you are using different BRDF or adding some new equation).

4. If possible, try to take into account implicit requirements as well. For example, you cannot use textures with file sizes of dozens of megabytes for a Web site; and also, your page should render at least at 30 fps on average smartphones. You will get bonus points for a result that could be deployed to a Web site with few or no modifications.

5. Write a concise report by overwriting this file.

## Starting code

There is no specific starting code for this project. If you choose to use your own shaders, choose from our examples the one that uses the lighting techniques you want to use, or combine from more examples for a specific set of techniques. If you want to use
three.js provided materials and lights, you can start from some three.js built-in example.

## Documenting and report

For project documentation and reporting, we use the [markdown format](https://daringfireball.net/projects/markdown/syntax), which is also the format of this document. Markdown is a lightweight markup language with plain text formatting syntax which is easy and quick to write, very human-readable, and that can be converted to HTML.

If you need more features than the ones that markdown provides (e.g. writing equations), you can use one of its extensions called [markdeep](https://casual-effects.com/markdeep/).

You are required to document your project in two ways:

- maintain a journal (in a file called journal.md) describing key design decisions, changes, bug symptoms and solutions, including screenshots.
- create a report (by overwriting this file).

The report should be as brief as possible while covering the following points:

- overall description: what your project is about and the files it uses.
- results, including images of the scenes created, taken in a way that clearly illustrates that they satisfy the specification.
- brief explanation of the process that you used to make your scene. Include tools, assets, and planning steps.

## Constraints

If you use textures / 3D models / substances / ..., make sure that you have the rights to include them. For example, search for images that come with a [CC Attribution, ShareAlike or NonCommercial licences](https://creativecommons.org/share-your-work/licensing-types-examples/).

In this project, you are allowed to re-use assets taken elsewhere, but **entirely copying** others' work, even with slight modifications, is forbidden and will have serious consequences beyond the deletion of your project. In any case, mention any source of inspiration in your journal and final report.

## Follow-up

You are welcome to extend your project after the deadline, in any way your think is interesting. For example, you could add javascript libraries that analyze music and derive values in real-time that can be fed to three.js for animation purposes, or you could extend your terrain generation software such that hidden cube faces are not created in three.js. If you do that before the final exam, you might get bonus points for this kind of activies - just let me know any progress you make.

## Credits

The image above comes from a [Ford car configurator built in three.js](http://www.ford.com/cars/mustang/customizer/#!/customize).
