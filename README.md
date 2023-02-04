# Laminar-flow-around-a-sphere

This set of OpenFOAM simulations concerns laminar flows around a sphere at various values of Reynold's numbers. This case has been done with air as a working fluid and around a sphere with a diameter of 1 meter. For validation on the simulations I kept track of the drag coefficients and compared them to [experimental values](https://pages.mtu.edu/~fmorriso/DataCorrelationForSphereDrag2016.pdf). 

## Pre-analysis

The scope of this set of simulations is just the laminar range of flows, so no turbulence modelling is needed. Thus, I only completed simulations in which the Reynold's number dosen't exceed more than a couple of hundreds. 

A great way of validating simulations is measuring a certain flow value of intrest, which in this case is the drag coefficient, and comparing those values to experimental ones. 
The drag coefficient commonly denoted as $Cd$ is a dimensionless quantity that is used to quantify the drag or resistance of an object in a fluid environment.

It is mathematically defined as:
$Cd=2Fd/\rho u^2 A $.

The picture below represents the relationship of the drag coefficient and the Reynold's number.


![Drag_coefficient_of_a_sphere_as_a_function_of_Reynolds_number](https://user-images.githubusercontent.com/84512701/216652882-d4c6538b-f66c-4e6e-9128-afeee3e2c9b4.png)

The region of intrest for this project is up to about the Reynold's number of 300. The rest will be the topic of a different project that will be up here on github hopefully soon. 


## Geometry and Mesh

The geometry consists of a sphere with a diameter of 1 meter in the centre of a square with sides of 10 meters. I created this simple geometry in Blender and exported it as a set of .STL files. Each .STL file coresponds to a patch with distinct boundary conditions, and this format is very well optimized for work with OpenFOAM and particularly with the snappyHexMesh meshing tool it provides.

<p align="center">
  <img src="https://user-images.githubusercontent.com/84512701/216657800-ecafa7f4-00d6-40fa-b3f5-6d4730e16171.png"/>
</p>

I made the mesh with the snappyHexMesh utilitty, and all of the parameters i used can be found in the Mesh folder. 

In short, I added a bit of refinement to the walls and more refinement to the region close to the sphere, and on top of that added some inflation layers to the sphere (this will be more usefull in the turbulent set of simulations). 
Here's a view of a slice of the mesh in the proximity of the sphere:
<p align="center">
  <img src="https://user-images.githubusercontent.com/84512701/216659317-2bde5309-4092-412e-ba88-e1895a9c0e45.png"/>
</p>

The mesh consists of 173368 hexahedral cells, 6488 polyhedral cells and 72 prismatic cells. The average and maximum non-orthogonality values of the mesh are 6.53 and 41.58 respectfully, so there will be no need to use non-orthogonal correctors while solving the simulations. The maximum skewness is 0.49, which is completely fine. 

## Numerical Model





## Results and postprocessing

For tracking the values of the drag coefficient I used runtime postprocessing with a function object forceCoeffs (can be found in the system folder). I used a jupyter notebook (also available in this repo) to plot theese values.




