# Sci_Simulation_Models
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

## Ising Model : ##
Ising model is one of the more famous models in statistical physics. The system studied in the model has 'spins' located at vertices of a (possibly infinite) lattice, and spins interact with their neighbours using a specific rule (like spins stabilize the energy and unlike spins destabilize the energy) and iteract with external field B; thus the energy of the system is given as: U=−∑iBσi−12∑⟨i,j⟩Jσiσj
 
In the simple version of the model,  σi=±1 , and system is maintained at temperature  T ; the probability of a particular configuration is given by the Boltzmann Probability Law: P({σi}Ni=1)∝exp[−βU({σi})]
 
Clearly the probability is then given by: P({σi}Ni=1)∝exp⎡⎣BkT∑iσi+J2kT∑⟨i,j⟩σiσj⎤⎦ and hence depends on numerical values of  BkT  and  J2kT .

Periodic Boundary Conditions: To simulate a infinite system, it is common to use Periodic Boundary Conditions (PBC). As illustraition consider 1-dimensional (1D) lattice, which is nothing but a straight line, with  N  spins placed with equal spacing between two contigious spins. This chain of spins has left-end and right-end making this a finite system; however if we place this chain of spins on a circle such that in addition to requiring that distance between contigious spins is 1 unit, we require the distance betwen left-end and right-end of chain is 1 unit. We now see that the chain becomes infinite. We can imagine similar trick in 2 dimensions, by requiing PBC in x-direction and y-directions. And, in 3-dimensions, requiring PBC in x-direction, y-direction and z-directions.

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

## Prey Predator Model : ##
Prey-Predator (also known in literature as Lotka-Volterra model) is a popular model to study dynamics of a system consisting of two antogonists, in this case rabbits (prey) and foxes (predator).

The dynamics of the sytem are determined by interactions within and between the prey and predator populations. The intra-species interactions are (natural) birth and (natural) death rates, while inter-species interactions are the predation of prey (i.e. predator 'eats' prey for its survival!). Let  X  denote the population size of prey and  Y  denote the popluation size of predator.

For the population dynamics of the prey: prey replicates at a rate that is controlled by abundance of the natural resources (rabbits need grass); we assume that these natural resources are abundant and remain at the same level throughout. Prey might die of natural causes (old age) or is eaten by predator. Thus the dynamics are reasonably modeled as:
dXdt=αX−βXY
 
For the population dynamics of predator: population of predator is expected increase linearly with its own size, and also on the population size of prey (since it needs prey as food). The natural death rate of the population depends on its own population size. Thus prey population size dynamics may be modeled as:
dYdt=γXY−δY
 
Clearly the dynamics of the model are dependent on the four positive constants  α, β, γ , and  δ , which are to be inferred from the feild data.

We study and understand the population dynamics of this model (i.e.  X(t)  and  Y(t) ). We will set these four parameters to value of 1.

## Coin Toss Random Walks : ## 
If a coin has a probability of  p  for showing heads and  q=1−p  for showing heads, then the probability of seeing  M  heads when coin is tossed  n>M  times is given by:
P(M;n)=n!M!(n−M)!pMqn−M
 
If the average the number of heads is denoted  Mn≡M/n , then clearly  0≤Mn≤1  and we expect that  Mn→∞=p . For  Mn  being in the range  (x,y) , we have:
Prob(x<Mn<y)=∑r∈Z ∧ x<rn<yP(r;n)

Let  c(t)  be the result of coin toss, tossed at time  t . Then Random Walk is given by
x(t+1)=x(t)+δc(t),H−δc(t),T with  x(0)=0 .

## Integration Without Integration : ## 
Computing integrals (numerically) is an important task in many computational fields. We will explore two schemes:

1. Finite difference schemes / Grid schemes
2. Monte Carlo scheme : Analogy- To find the area of a circle on a ground, we can do the following. Create a square tangential to the circle and randomly throw a penny inside the square till infinity and keep a count of the number of coins that fell inside the circle. The area of the circle simply is #coins inside the circle/ #total coins thrown * Area of square ( which is easy )
