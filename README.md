# Soft_Shell_project
This project is inspired by the publication by Singh & Hernandez (2018), an extended Hard Sphere model with soft shell to consider various softness exist on a particle. This model is applicable to real systems such as metallic clusters with ligands on the surface as a full particle and its interactions with other particles. It is computationally infeasible to simulate the entire system down to the atomic scale (namely the atomistic modeling) as the quantum interactions between each atoms required extensive computing power to solve. Therefore it is this project's nature to lump the atoms or molecules into a particle with representative properties and the interactions between these identical particles will be simulated. 

Hard Sphere Model
Hard sphere model is a statistical mechanical model to describe the simplest non-overlapping interactions between particles. And it can be served as a coarse grain model. 
Phase transition has been observed in HS system where compressing the system (practically by shrinking the box size) transform the system from liquid state to crystalline, passing through freezing point and melting point. 
![image](https://github.com/ccyehintx/Soft_Shell_project/assets/124641066/70e5c577-7f41-43a8-a5a7-4c1750b6dae8)
However, the simplicity of the HS model limits the usage in the real world system, therefore a more realistic model is introduced and implemented in this project
