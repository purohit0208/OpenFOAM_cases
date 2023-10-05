
# OpenFOAM_cases:

This repository contains OpenFOAM tutorials and their brief description. Some of these tutorials are standard test cases available in OpenFOAM tutorials, while others are self-made.

## 1) incompressible-icoFoam-elbow tutorial:

This case contains a famous elbow tutorial available in OpenFOAM tutorials. Simulation and result files for this tutorial are available in "incompressible-icoFoam-elbow.zip" files.
Using icoFoam solver this tutorial simulates 300 s of flow in an elbow. The tri-mesh was generated for this case using GAMBIT. 
The mesh available from GAMBIT was in .msh format, which can be converted into .foam format using the "fluentMeshToFoam" command, to make it compatible with the OpenFOAM environment. This command generates an additional polyMesh folder in a constant directory, which contains all the mesh data necessary to perform simulations in OpenFOAM.
Since this tutorial is a 2D problem and OpenFOAM requires your geometries to be in 3D, the mesh in the Z direction has 1 unit length cell size.



## Results

The figure below shows the 2D mesh of the elbow tutorial. It is clear from the figure that it is a tri mesh. This geometry has 2 inlets and 1 outlet, which can be seen in the figure. Flow enters from Inlet 1 with 1 m/s velocity in the +X direction and from Inlet 2 with 3 m/s velocity in the +Y direction. The BC for the outlet was pressure-outlet BC.
Both the left and right edges of the elbow were treated as a NoSlip wall BC, while both front and back planes were treated as empty. These initial and Boundary Conditions can be seen in folder "0" in the "incompressible-icoFoam-elbow.zip" files. 

![Bild1](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/e34d3f02-b75e-4ed8-96e3-36277bb86296)

The solver used for this case is the icoFoam solver, which is a Transient solver used for Laminar and Incompressible flow, which uses the PISO algorithm. elbow.foam file is a .foam file that can be opened in Paraview to analyze the results. The figure below shows velocity contours at t=300 s. 

![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/f00650e6-7786-4367-891a-9520aa94acc0)
## Lessons Learned


The objectives of this tutorial were to learn how to do basic case setup in OpenFOAM, and how to set up initial conditions for p and U. The mesh for this tutorial was generated in GAMBIT(which is also available in the OpenFOAM resources folder). The mesh was converted from .msh to .foam format, to run this in an OpenFOAM environment. At the end of this tutorial, the simulation results were analyzed in Paraview software. 



## 2) compressible-sonicFoam-forwardStep tutorial:

This case contains the famous forwardStep tutorial available in OpenFOAM tutorials. Simulation and result files for this tutorial are available in "compressible-sonicFoam-laminar-forwardStep.zip" files. Using sonicFoam solver this tutorial simulates 60 s of flow over a forward step. 

The file T in the "0" directory includes the initial temperature values. Internal pressure and temperature fields are set to 1, and the initial velocity in the domain as well as the inlet boundary is set to 3. Symmetryplane BC was applied to the bottom and top, while noSlip BC was applied to the obstacle.

Different properties of a compressible gas can be set in the "thermoPhysicalProperties" file. After defining the models for different thermo-physical properties of the gas, the constants and coefficients of each model can be defined in the sub-dictionary mixture in the same file. In the "turbulenceProperties" file, the appropriate turbulent mode can be set(in this case it is laminar).





## Results

The figure below shows the 2D mesh of the forwardStep tutorial. Geometry and Mesh for this case were generated using the blockMeshDict file, by using the blockMesh command. The simulation was done using a sonicFoam solver, which is a transient solver used for compressible flow simulation for Laminar/Turbulent flow and for Transonic/Supersonic flow by using the PIMPLE algorithm. Since this tutorial is a 2D problem and OpenFOAM requires your geometries to be in 3D, the mesh in the Z direction has 1 unit length cell size. These initial and Boundary Conditions can be seen in folder "0" in "compressible-sonicFoam-laminar-forwardStep.zip" files. 

![Bild1](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/350eb614-8406-4980-a31c-03064c1455cc)

forwardStep.foam file is a .foam file that can be opened in Paraview to analyze the results. The figure below shows velocity and pressure contours at t=60 s. 


![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/f37f3d9a-6cef-4566-95ec-45aef07b594e)

![02](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/7ff23404-a3ea-4ee8-97d2-818b31b14425)
## Lessons Learned


The objective of this tutorial was to learn blockMesh utility of the OpenFOAM environment. Vertices were defined via coordinates as well as surfaces and volumes were defined via vertices. At the end of this tutorial, the simulation results were analyzed in Paraview software. 



