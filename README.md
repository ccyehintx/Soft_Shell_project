# Soft_Shell_project
This project is inspired by the publication by Singh & Hernandez (2018), an extended Hard Sphere model with soft shell to consider various softness exist on a particle. This model is applicable to real systems such as metallic clusters with ligands on the surface as a full particle and its interactions with other particles. It is computationally infeasible to simulate the entire system down to the atomic scale (namely the atomistic modeling) as the quantum interactions between each atoms required extensive computing power to solve. Therefore it is this project's nature to lump the atoms or molecules into a particle with representative properties and the interactions between these identical particles will be simulated. 

**Hard Sphere Model**

Hard sphere model is a statistical mechanical model to describe the simplest non-overlapping interactions between particles. And it can be served as a coarse grain model. 
Phase transition has been observed in HS system where compressing the system (practically by shrinking the box size) transform the system from liquid state to crystalline, passing through freezing point and melting point. 
![image](https://github.com/ccyehintx/Soft_Shell_project/assets/124641066/70e5c577-7f41-43a8-a5a7-4c1750b6dae8)
However, the simplicity of the HS model limits the usage in the real world system, therefore a more realistic model is introduced and implemented in this project

**Soft-Shell Hard Sphere Model**

This model adds a soft shell to the system corresponds to the ligands around the metallic cluster. 
![image](https://github.com/ccyehintx/Soft_Shell_project/assets/124641066/229831e2-2fd4-4856-97ba-f7653667649e)
![image](https://github.com/ccyehintx/Soft_Shell_project/assets/124641066/e703de2c-d3dc-4b08-8c49-742b9075de5b)

If the two particles overlap within the soft-shell region, a random number will be generated to determine if the two will behave elastic collision or remain the position. 

In analogy with the HS system, it is worth investigating whether similar phase transition can be observed in the soft-shell HS system.

**Computational Scheme:**

![image](https://github.com/ccyehintx/Soft_Shell_project/assets/124641066/fe8f9628-9088-49f6-8018-2cb1f2028a22)

The algorithm works as follows:

1. The system is initialized with positions and velocities following Boltzmann distribution

2. The positions are updated based on the given time step and the velocities

3. All the pair distances are checked and random numbers are generated to model the probability:
   If distance > outer radius: No change on the velocities
   If Outer > distance > Inner & softness > random number: No change on the velocities
   If Outer > distance > Inner & softness < random number: Elastic collision (velocities swap)
   If distance < Inner: Elastic collision (velocities swap)

4. Update the velocities and go back to step 2 until N cycles are completed

5. After the cycles are completed, analyse the radial distribution functions and fluxes.

6. Restart with a box size (different packing fractions)

**Analysing the Results:**

We will calculate the radial distribution function, $g(r)$, from our simulation and focus on the location of the first minimum of $g(r)$ $i.e.$ $g(r=r_{min})$, because $r_{min}$ represents the average distance between particles and can be used as a good physical quantity characterising the macroscopic state of the system. In this project, we will change the packing fraction and the temperature and record the position of $r_{min}$. By tracking the position of $r_{min}$, we are able to find the phase transition point of the system.

1. Changing the packing fraction

To find the first minimum of $g(r)$, we use a polynomial function to fit $g(r)$. It is shown that a fifth-degree polynomial is good enough to fit our data, and we can use this function to find the minimum.
<img width="1004" alt="polynomial fitting" src="https://github.com/ccyehintx/Soft_Shell_project/assets/121147391/dc2e50a8-92b0-409c-82e9-313f22edf1a2">
<img width="432" alt="minimum" src="https://github.com/ccyehintx/Soft_Shell_project/assets/121147391/35f8ac28-7424-4f07-a494-9f6807e0c3c8">

We can use this method to find $r_{min}$ of different packing fraction. A $r_{min}$ vs packing fraction plot is shown below. It shows that the linearity is broken while the packing fraction approches 0.58, and this point can be regarded as the phase transition point.

![change phi gr](https://github.com/ccyehintx/Soft_Shell_project/assets/121147391/75a13f74-38ea-4bb4-9952-93a41c0c4f52)

![change phi rmin](https://github.com/ccyehintx/Soft_Shell_project/assets/121147391/f2df82ab-9132-4e85-b8ab-90911a676f42)

2. Changing the temperatuer

In this part, we will change the temperature and find the corresponding phase transition point. Our data shows that when the temperature goes to 5.2, a phase transition happens. Since $r_{min}$ increases rapidly with the temperature, we think it's a phase transition from liquid to gas.
![change t gr](https://github.com/ccyehintx/Soft_Shell_project/assets/121147391/2cbeab5f-64bc-4b6e-a351-cbf3ad916ae0)
![cahnge t rmin](https://github.com/ccyehintx/Soft_Shell_project/assets/121147391/8fb91e14-5618-4766-8b13-b765d933fde0)



Another theoretical approach to identify the phase transition point is via plotting the pressure-packing fraction plot. The pressure can be computationally obtained from logging the flux of the particles (how many particles jump out of the simulation box). And this flux can be statistical mechanically treated to compute pressure.




**References:**

[1] Kumar, Rajesh et al. Springer Nature Singapore, 2022. 205-215.

[2] William’s course materials: https://www.wgilpin.com/cphy/talks/html_static/monte_carlo_metropolis.html

[3] Singh, Rakesh S., and Rigoberto Hernandez. Chemical Physics Letters 708 (2018): 233-240.

[4] Ojovan, Michael I., and Dmitri V. Louzguine-Luzgin. The Journal of Physical Chemistry B 124.15 (2020): 3186-3194


