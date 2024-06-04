Thread groups  64 wide group-> Warps/Waves  32 wide-> 

What is the point of building waves/warps: It directly maps to the architecture of the GPU, and that warp can be used to run a SIMD or compute shader
* The programming model is used so we can map it efficiently and cleanly to the architecture
	* A WorkGroup in OpenCL
	* Grid Cuda
	* Threadblock/Warp/Thread
	* Direct X Dispatch/Thread Group/Waves/Thread

We can take 32 instances of a shader and map it to a 32 Wide SIMD Stream Processing Unit
* They stay unique, but it allows us to grab a group
	* The shader compiler
* Everything is compiled into ASM 
	* The `v_variable` syntax means vector
		* This denotes an assembly instruction on the GPU allowing for 32 instances to be spawned on the GPU and only 4 on the CPU
	* They are all considered different programs and each containing its own memory, and lane, but the instructions are being applied to all of the program instances (process)

How does it tell what thread it is:
* it loads the program to the compute unit, and the dispatch will pause the pointer onto the register
* Basically the id is stored in a register already because it is designed knowing we are going to want that information

What happens when you have a conditional statement?
* Uses blocks to use this
* Execution Mask: Hovers over the SIMD lanes, and if there is a 1 you will execute the code, if there is a 0 you do not execute the code.
* Each line represents a mask, and the following line is an example of how it can change as you are running through conditional statements

| 1   | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 0   | 1   | 1   | 0   | 0   | 0   |
| 0   | 0   | 0   | 1   | 1   | 0   | 0   | 0   |
Then when you are finished, you flip the mask and then execute the other half of the code
* This is inefficient if the code has a ton of branching
* What does this mean s a programmer?
	* If you are putting too many if statements in your kernel you should ask you WHY you need it? because it destroys the efficiency of the code

Scheduling:
* you typically dispatch a thread group to a single Dual Compute Unit
* Thread groups are then broken down into waves/warps
* And each Shader instance gets mapped to a single lane