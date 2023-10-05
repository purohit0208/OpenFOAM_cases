
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


## 3) compressible-sonicFoam-shockTube tutorial:

This case contains a famous shockTube tutorial available in OpenFOAM tutorials. Simulation and result files for this tutorial are available in "compressible-sonicFoam-laminar-shockTube.zip" files. Using sonicFoam solver this tutorial simulates 0.06 s of flow inside a shock tube. 

By looking at the "blockMeshDict" file, it is obvious that it is a 1D mesh because the number of mesh cells in the Y and Z directions is 1. The mesh density can be set in the part of the block by changing X direction mesh size(e.g. change it from 100 to 1000 to 10000). Another important file is "setFieldsDict", which is used by the tool setFields for patching(assigning an amount to a region) in the simulation. 
In the defaultFeildValues, a value is assigned to the whole domain, while in the regions sub-section a specific value is patched to a certain region of the domain. In this example, the region is defined as a cube, by the coordinates of one of its diagonals in boxToCell. After choosing the region, the new values are assigned to the parameters for this region.

## Results

The figure below shows a 1D mesh of the shockTube tutorial, which has 10000 cells. Geometry and Mesh for this case were generated using the blockMeshDict file, by using the blockMesh command. setFields command was used to set fields in a particular region of the mesh.
The simulation was done using a sonicFoam solver, which is a transient solver used for compressible flow simulation for Laminar/Turbulent flow and for Transonic/Supersonic flow by using the PIMPLE algorithm. Since this tutorial is a 1D problem and OpenFOAM requires your geometries to be in 3D, the mesh in Y and Z directions has 1 unit length cell size. 

![00](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/0e383807-dc34-48d4-b629-c64a60378cad)

In the 10,000 cells case with 10 bar and 0.1 bar case setup, the simulation crashes with the default deltaT(1e-5) hence it has been set to 1e-6 to adjust Courant Number. shockTube.foam file is a .foam file that can be opened in Paraview to analyze the results. The figure below shows velocity, pressure, and temperature contours at t=0.007 s for 10 bar/0.1 bar and 10000 cells. Shock travel for the entire 0.6 sec can be seen in the video format in the 00.mp4 file in "compressible-sonicFoam-laminar-shockTube.zip" files.

![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/29fb2f36-4858-4449-9103-039d0179e1a1)

![02](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/13706b41-c961-4fee-97aa-042f3f0ec28f)

![03](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/4f61d966-d9a1-4423-a7dc-87912a596447)

## Lessons Learned

The objectives of this tutorial were to understand the setFields utility of the OpenFOAM environment as well as to investigate the effect of grid resolution. The number of cells used in this tutorial is 10,000 but a different mesh can be generated by changing the no of cells in the blockMeshDict file to study the effects of grid resolution. For initial values in this tutorial, 10 bar/0.1 bar was used which can also be changed to 1 bar/0.1 bar. At the end of this tutorial, the simulation results were analyzed in Paraview software. 


## 4) incompressible-simpleFoam-pitzDaily tutorial:

This case contains the famous pitzDaily tutorial available in OpenFOAM tutorials. Simulation and result files for this tutorial are available in "incompressible-simpleFoam-pitzDaily.zip" files. Using simpleFoam solver this tutorial runs a steady-state simulation with kEpsilon(RAS) turbulence model. 

When a turbulence model is chosen, the value of its constants and its boundary values should be set in the appropriate files in the 0 folder. For kEpsilon model k and epsilon, files need to be modified, for kOmega model k and omega files need to be modified. In the "turbulenceProperties" file, the simulationType can be set as either RAS, LES, or laminar. Then the corresponding sub-dictionary of the chosen simulation type needs to be defined. Since this is a steady-state simulation, endTime in controlDict shows the number of iterations instead of time, and deltaT should be 1. 

## Results

The figure below shows a 2D mesh for the pitzDaily case. The geometry and mesh for this tutorial were generated using the blockMeshDict file, by using the blockMesh command. Since this tutorial is a 2D problem and OpenFOAM requires your geometries to be in 3D, the mesh in the Z direction has 1 unit length cell size. Velocity-Inlet BC was chosen at inlet and at Outlet pressure-outlet BC was chosen. For upper and lower walls noSlip BC was assigned while both front and back planes were assigned empty BC. For k, epsilon and nut wall function was applied on upper and lower walls. 

![Bild1](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/cb5e0f1f-fa55-479a-81e2-23f833d64d5f)

The simulation was done using simpleFoam solver, which is a steady-state solver used for incompressible flow simulation for Laminar/Turbulent flow that uses the SIMPLE algorithm. 
pitzDaily.foam file is a .foam file that can be opened in Paraview to analyze the results. The figure below shows the converged results in the form of contour plots of the velocity magnitude and turbulent viscosity by using kEpsilon model.

![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/ec9952f9-afd2-46f3-b5c8-b160cc025685)

![02](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/466befdf-937a-417b-9a4a-a106ba837582)

## Lessons Learned

The objective of this tutorial was to understand turbulence modeling in OpenFOAM and to understand steady-state simulation in the OpenFOAM environment. At the end of this tutorial, the simulation results were analyzed in Paraview software. 


## 5) incompressible-pisoFoam-LES-pitzDaily tutorial:

This case contains the famous pitzDaily tutorial available in OpenFOAM tutorials. Simulation and result files for this tutorial are available in "incompressible-pisoFoam-LES-pitzDaily.zip" files. Using pisoFoam solver this tutorial runs a backward-facing step case for 0.6 s with kEqn(LES) turbulence model.  

When a turbulence model is chosen, the value of its constants and its boundary values should be set in the appropriate files in the 0 folder. For kEpsilon model k and epsilon, files need to be modified, for kOmega model k and omega files need to be modified. In the "turbulenceProperties" file, the simulationType can be set as either RAS, LES, or laminar. Then the corresponding sub-dictionary of the chosen simulation type needs to be defined. 

## Results

The figure below shows the 2D mesh for the pitzDaily case. The geometry and mesh for this tutorial were generated using the blockMeshDict file, by using the blockMesh command. Since this tutorial is a 2D problem and OpenFOAM requires your geometries to be in 3D, the mesh in the Z direction has 1 unit length cell size. Velocity-Inlet BC was chosen at inlet and at Outlet pressure-outlet BC was chosen. For upper and lower walls noSlip BC was assigned while both front and back planes were assigned empty BC. For k, epsilon and nut wall function was applied on upper and lower walls. 

![Bild1](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/cb5e0f1f-fa55-479a-81e2-23f833d64d5f)

The simulation was done using a pisoFoam solver, which is a transient solver used for incompressible flow simulation for Laminar/Turbulent flow that uses the PISO algorithm. pitzDaily.foam file is a .foam file that can be opened in Paraview to analyze the results. The figure below shows results in the form of contour plots of the velocity magnitude at t=0.2, 0.4, and 0.6 sec. The entire simulation for 0.6 sec in video format can be seen in the 00.mp4 file in "incompressible-pisoFoam-LES-pitzDaily.zip" files.

![03](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/a77cc1fb-b511-43a9-9be6-775d978fea90)

![02](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/94210379-ac98-42a1-847b-ae997e8f44ee)

![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/06ea776b-8a23-4ec7-8bed-ffa0d15755cd)

For the kEpsilon model after 0.2 sec, the results are similar to the steady-state simulation. Therefore, it can be assumed it has reached a steady state. Other models do not have a steady situation and fluctuate all the time, so they require averaging to obtain steady-state results. LES does not use averaging to obtain the turbulence values, therefore LES simulations should use a higher grid resolution and smaller time steps.

## Lessons Learned

The objective of this tutorial was to understand turbulence modeling in OpenFOAM and to understand the difference between transient and steady-state simulation in the OpenFOAM environment. Additionally, different turbulence models like Smagorinsky(LES) or kEpsilon(RAS) turbulence models can be tried with this tutorial.
At the end of this tutorial, the simulation results were analyzed in Paraview software. 


## 6) multiphase-interFoam-laminar-damBreak tutorial:

This case contains the famous damBreak tutorial available in OpenFOAM tutorials. Simulation and result files for this tutorial are available in "multiphase-interFoam-laminar-damBreak.zip" files. Using interFoam solver this tutorial simulates the breaking of a dam for 60 sec.

In the 0 directory, alpha.water, p_rgh and U files exist. In the alpha.water and p_rgh files, the initial values and boundary conditions for the water phase and pressure are set. In the turbulenceProperties file in the constant directory, simulationType can be set which is set to laminar for this case. In the transportProperties, there is the list of phases in the simulation(in this case air and water) and sigma is the surface tension between two phases. In the g file, the gravitational field and its direction are defined.  

## Results

Figure below shows the 2D mesh for the damBreak case. The geometry and mesh for this tutorial were generated using the blockMeshDict file, by using the blockMesh command. Since this tutorial is a 2D problem and OpenFOAM requires your geometries to be in 3D, the mesh in the Z direction has 1 unit length cell size. On leftwall, rightWall, and lowerWall noSlip BC was applied while inletOutlet BC was applied to the atmosphere. inletOutlet BC is used when the flow direction is not known. When the flux direction is toward the outside of the domain, it works like a zeroGradient BC and when the flux is toward inside the domain it is like a fixedValue BC. 

![Bild1](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/25bd2f80-1e0e-4579-8777-b1623c0d269f)

The simulation was done using interFoam solver, which is for two incompressible, isothermal immiscible fluids using a VOF(volume of fluid) approach using the PIMPLE algorithm. damBreak.foam file is a .foam file that can be opened in Paraview to analyze the results. The entire simulation result for 60 sec in video format can be seen in the 00.mp4 file in "multiphase-interFoam-laminar-damBreak.zip" files. The figure below shows results in the form of contour plots of the alpha.water at t=0.0, 0.1, 0.3, 0.35, 0.5, 0.6, 0.7, 1.0, 1.5, 2.0 and 3.0 sec.

![01](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/e32c4f5f-871a-4a85-98ee-1fcfa20c9516)

![02](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/68c4536c-ecf7-4262-ba7d-d4a76e6fb4aa)

![03](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/93c69cae-0cbe-49d4-93c0-fe1cfcaf7b20)

![04](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/63db435c-8419-458c-a1d8-abae8b634e06)

![05](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/cacde7f1-a77a-4409-b679-9715a62bc815)

![06](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/f94645d3-a3b4-4c34-af8d-5e1e26523876)

![07](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/59b58b01-3ec9-4b4b-a1b9-e185befa65b9)

![08](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/6d8ccecd-34c5-48eb-a2be-c087b3f2f067)

![09](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/8b3aa21e-7b82-4319-a051-c2e2233c5e95)

![10](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/b1bbc200-cabf-4548-a161-d9fa501984b6)

![11](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/68680717-f5d4-4fa3-bcdd-929788fcc96c)

![12](https://github.com/purohit0208/OpenFOAM_cases/assets/85656918/1c3ff468-b0f0-46f0-a676-16dd69347eb2)

## Lessons Learned

The objective of this tutorial was to understand multiphase modeling in OpenFOAM and to understand how to set viscosity, surface tension, and density for two phases. At the end of this tutorial, the simulation results were analyzed in Paraview software. 




