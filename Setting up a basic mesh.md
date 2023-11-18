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

Next, set up the fluid domain