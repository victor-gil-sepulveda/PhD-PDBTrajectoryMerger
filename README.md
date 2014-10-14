#PDB Trajectory Merger

A very simple Python program to merge trajectories of biomolecules in PDB format. Trajectories can have an arbitrary number of frames, which means that it can be used to merge single PDBs too. The only restriction is that every 
frame (conformation or system) must be encompassed by  *MODEL* / *ENMDL* tags. If the last frame is broken, the merger will automatically skip it.


##Usage


```Shell
> python PDBTrajectoryMerger.py -p prefix -d dir -o output_file  

``` 

#### Prefix
Use the '-p' flag to specify the part of the file name shared by all the files you want to merge. Ex.  

Given that we have *traj_1.pdb*, *traj_2.pdb* and *another.pdb*, using *-p traj_* will merge *traj_1.pdb*, *traj_2.pdb* and skip *another.pdb* 
#### Directory

Use '-d' to specify the working directory (the directory in which the files of interest reside).  

#### Output

Use the '-o' flag to specify the name of the output file.

Ex. *-o merged.pdb*


### Optional flags
#### File list 

Path of a file containing the paths of the pdb files to merge. If used, overrides '-p' and '-d'.

### Remarks
Adding the flag '--remarks' will keep the original remarks in the merged output.

### Skipping frames
Using '--skip_first N' will skip the first N frames of each trajectory.  

### Merging policies
With '--merge_action' the user can specify the way the frames are added to the merged output file:
- __SEQUENTIAL__ : It will first add all the frames of the first trajectory, then the frames of the second and so on. 
 
- __ENTANGLE__ :  It will add all first frames then all second frames and so on.


### Append

If the flag '--append' is used, the merged frames will be appended to the output file (instead of creating a new output file).

