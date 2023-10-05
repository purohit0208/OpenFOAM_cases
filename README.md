
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

The solver used for this case is the icoFoam solver, which is a Transient solver used for Laminar and Incompressible flow, which uses the PISO algorithm. elbow.foam file is a .foam file that can be opened in paraview to analyze the results. The figure below shows velocity contours at t=300 s. 

![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/f00650e6-7786-4367-891a-9520aa94acc0)
## Lessons Learned


The objectives of this tutorial were to learn how to do basic case setup in OpenFOAM, and how to set up initial conditions for p and U. The mesh for this tutorial was generated in GAMBIT(which is also available in the OpenFOAM resources folder). The mesh was converted from .msh to .foam format, to run this in an OpenFOAM environment. At the end of this tutorial, the simulation results were analyzed in Paraview software. 



