# Attractor-Sequence-Paper
To get started using the model network, extract the .m files from the simulation_code.zip and use the following functions:
  1. p=make_params()          
  This will return a parameter structure (p) that uses the default ('fiducial') parameter set used in the paper
  
  2. Iapp = make_Iapp(p,seq)  
  This will return a matrix (Iapp) that has one row for each unit in the network (and ntimesteps columns). p is the parameter 
  structure returned by make_params() and seq is a vector of integers, each specifying the ID of one of the stimuli. Note that
  if length(seq) does not equal p.sequence_length, then not all of the stimuli in seq will be represented in Iapp.
  
  3. [r,D,s] = run_network(p,Iapp,init_type,memoptimize)
  
      Inputs:
      p -> parameter structure returned by make_params()
      
      Iapp -> Matrix of input currents returned by make_Iapp()
      
      init_type -> can be 'silent', 'random', or 'constant'. Determines how the initial state of the network (before the
      sequence of stimuli) is initialized
      
      memoptimize -> If 'yes', then the returned variable r will be a (Ngroups x nTimesteps) matrix with a value of firing rate
      for each unit for each timestep. D and s however will only be 1D vectors giving the value of D and s (for each unit) on
      the last timestep. This option saves memory and can speed up the simulation. If 'no', all 3 output variables will be
      (Ngroups x nTimesteps) matrices with one value of each dynamical variable per unit per timestep
      
      Outputs:
      r -> Firing rate variables for each unit
      D -> Synaptic depression variables for each unit
      s -> Synaptic output variables for each unit
