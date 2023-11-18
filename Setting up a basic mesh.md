This section covers setting up a basic model, scenes, and automated mesh.

#### Importing and preparing CAD
[[Make a new file]], then select the "import CAD model into 3D-CAD" to bring in your chosen model, which should be a fully filled in (no hollow inside to avoid internal meshing) SolidWorks model, saved as a [[parasolid]] or similar, with as fine a tessellation on the rounded edges as possible (check [[Ideal CAD Models]] for more information)
![[Pasted image 20231113195631.png]]
Once the model is imported, you should see a new [[scene]] open up, displaying your model as it was imported by STAR-CCM+ into the file. Inspect it to make sure everything transferred correctly, and to make sure the axes are lined up as you would like. For this wiki, the flow direction will be assumed to be in the positive x-direction, so to follow along exactly it will help to rotate the model as needed. 


![[Pasted image 20231113195714.png]]

To rotate the model, once inside the scene right-click "Body 1", "Transform", then "Rotate", and set directions accordingly.

Once all necessary changes are made, click on "Update 3D-CAD" and reopen the main menu (do not close this scene).
#### Setting up surfaces

Once back in the main screen, open the newly populated "3D-CAD Models" drop-down, right-click the model, and select "New Geometry Part". Turn "Tessellation Density" to Very Fine, then click OK.

In Geometry --> Parts --> Body 1 --> Surfaces, right-click the "Default" surface and select "Split by Patch". This will allow for [[Surface Controls]] when meshing later and for other diagnostics/control on specific regions of the body.

![[Pasted image 20231113201308.png]]
*Rocket body split by patch*

Now, go through the individual part surfaces, clicking them on the body or on the lefthand menu (Control + click and Shift + click both apply) and assign correct names to each item, clicking Create after each named group. Recommended parts/names are: Nosetip, Nose Cone, Body, Fin Can, Boattail, Base, Fin 1/2/3/etc., and so on. Note that the surface marked with a star cannot be "created", and must be renamed later. Once finished, close the menu and combine (multi-select, right-click, 'combine') the surfaces as needed to finalize.

![[Pasted image 20231113202123.png]]
*Example set of surfaces*

#### Fluid Domain and Region Preparation

Next, set up the fluid domain. Typically, a sphere of radius 20 times the rocket body is used. So make a new Sphere Part (right click Parts --> Sphere), centered at the origin or otherwise on/as near to the rocket body as possible.

Then, multi-select the "Body 1" and the "Sphere" parts, right-click and select Boolean --> Subtract, and use CAD subtraction with the target part being the sphere. This will help form the mesh, allowing the rocket body and its parts to be interpreted as [[boundaries]]. From there right click your new "Subtract" object (It's recommended to rename it Domain, Fluid Domain, etc.) and select "Assign Parts to Regions"
![[Pasted image 20231118151634.png]]


Be sure to leave the first setting as-is, and to set the second to "Create a Boundary for Each Part Surface". This will help you add [[Surface Controls]] later, and also get individual diagnostics on all of the surfaces that we defined earlier. 


Once your Region is made, we are ready to make a mesh! Under the Parts menu, right-click Operations and make a new Automated Mesh (in the Mesh category). Select your fluid domain as the part, and enable the Surface Remesher, Trimmed Cell Mesher, and Prism Layer Mesher settings. Automatic Surface Repair is optional and will not be used in this tutorial. (If you're curious about the other types, see [[Mesh Geometries]]).
![[Pasted image 20231118151917.png]]

#### Basic Mesh Configuration

Feel free to poke around these settings (and read [[Mesh Controls]] for more info), but for this intro tutorial, we won't modify more than the basics. 

First, look at the [[Prism Layers]] settings (under [[Default Controls]]) and change the Thickness from "Relative to base" to Absolute. The thickness is impacted by the boundary layer thickness, and we don't want it to depend on the base size, which we may alter a lot. For this model, set the thickness to around 1-1.5 cm. In reality, you can use the tools found in the `tools` folder of the FS files to get accurate boundary layer thicknesses and other run-conditions (see [[Running your simulation]]). In addition, increase the number of prism layers to 10, to get more accurate simulation.
