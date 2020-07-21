# CIS_2_PythonScripts
Contains html files for jupyter notebooks with python codes for different models written for CIS2(S'19)

The various models coded are described below briefly:

## MolecularDynamics : ##
Molecular Dynamics is essentially the application of the Newtons Second Law to molecules, where the force acting on each part of the molecule is computed by modelling its interaction with every other part of the system.

Total potential energy of the system: U=∑i∈{bonds}12ki(di−d0,i)2+∑i∈{angles}12ki(θi−θ0,i)2+∑i∈{dihedrals}ϕ(cos(nθi)−1)+∑i,j∈{non−bond pairs}(ULJ(i,j)+UColumbic(i,j))
 
Equations of motion given by: dp⃗ idt=F⃗ idr⃗ idt=p⃗ i/mi

Euler Method: p⃗ i(t+dt)=p⃗ i(t)+dt F⃗ i(t)r⃗ i(t+dt)=r⃗ i(t)+dtp⃗ i/mi

Check on accuracy: constant total energy, total linear momentum 

Argon atom is electrically neutral and a good model for the pair-wise interaction between two Argon atoms is given by __Lennard-Jones potential__, whose functional form is given by:

ULJ(r⃗ i,r⃗ j)=4ϵ((σr)12−(σr)6), where  r⃗ =r⃗ i−r⃗ j  and  r=|r⃗ | .
 
Using the Euler method mentioned above, the trajectory of the system was computed!

## Balancing Equations : ## 
We need to form equations for all the variables in the equation each variable can be expressed in terms of the other variables

for example if i have the following equation: __A(XY)+B(ZY) -> CY + D(ZX)__

it can be solved by saying equation for X is A=D equation for Y is A+B=C equation for Z is B=D.

We need to create equation matrices for these. Lets say the RHS forms the matrix M and the LHS forms a matrix N. The solution is the matrix X such that MX=N where X is composed of B,C,D with assumption of A being 1 we get three such equations and three variables (B,C,D) as A=1 assumed, and we can solve them to get the balanced equation in terms of A

equation matrix for X would be [0,0,1]=[1]
equation matrix for Y would be [-1,1,0]=[1]
equation matrix for Z would be [-1,0,1]=[0]

Now we would solve MX=N to get a certain X. But we cannot yet be sure that X is a possible solution of MX=N or not hence we multiply X by M and check if we get back N or not


## Logistical Map Bifurcations : ##

Logistic map is a quadratic map; i.e.  f(x)  is a quadratic ploynomial. It shows a particularly interesting phenomena of 'deterministic chaos' i.e. a deterministic map showing apparently random behaviour. Logistic map has a single parameter, named  α , and is given by:
f(x)=αx(1−x) 
When  0≤α≤4 , the map takes an input  0≤x≤1  to give an output in the same range. For a particular value of the parameter  α , we want to find the behaviour of the map. For such systems, plot of  xn  vs  xn+1  is called phase plot and is a important tool for visualising and analysing such systems.

We will explore this using phase plots.

You can find good detail on Logistic Map at: https://en.wikipedia.org/wiki/Logistic_map
