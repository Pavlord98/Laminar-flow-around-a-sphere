#!/bin/bash

cp -r ../Mesh/polyMesh Simulation/constant

cd Potential-simulation-for-initialization/

rm -rf 0
cp -r 0.orig 0

potentialFoam -writep> potfoam.log


cp  -r 0/* ../Simulation/0 



cd ../Simulation

decomposePar > decom.log

mpirun -np 6 pisoFoam -parallel
