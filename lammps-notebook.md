Compile LAMMPS with MPI: "make mpi -j n"
Install package: "make yes=package_name"

sometimes I'll need to compile LAMMPS with different packages, so I can do that by compiling it again (with make mpi...) and then to run in parallel:
"mpirun -np N ./executable -in in.input_file_name"

I'll be using ovito to visualize the system, it can automatically read the LAMMPS files and do a bunch of statistics.

Tips:
- we will mainly work with Temperature=0.05
- beware of the interaction strengths and the skin size
- take into consideration that LAMMPS has a 2 stuff integration process and that is why, for instance, we first turn off all of the forces before applying new ones