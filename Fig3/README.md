## [Figure 3]Semi-Parametric Contextual Bandits with Graph-Laplacian Regularization

This repository provides codes for the reproduction of Figure 3 in the paper "Semi-Parametric Contextual Bandits with
Graph-Laplacian Regularization".

### Requirements

`numpy`
`networkx`
`sklearn`
`scipy`
`os`
`random`
`matplotlib`
`time`
`datetime`

### Components

* `SYNTH_functions.ipynb` This file contains:
 
     * **Functions for generating graphs and Laplacian matrix**   
     `set_graph_and_lapl_for_experiment(user_num, dimension, prob, threshold, our_graph_type, lap_type, gamma)`  
     * **Functions for generating arm features and user features**   
     `create_arms_features_normal(ARM_NUM,DIMENSION)`, `create_arms_features_sparse(ARM_NUM,DIMENSION)`,
     `create_users_features(USER_NUM, DIMENSION, LAPLACIAN, GAMMA)`  
     * **Class for each algorithm**  
     `SemiRidgeGraphThompson()` (Proposed), `IndividualThompson()`, `GUCB_local()`, `CLUB()`, `LinTS_Single()`, `SemiTS_Single()`, `IndividualSemiRidgeGraphThompson()`    
     Each class contains 2 main functions, one for choosing arms and another for updating the parameter estimates.  
     `run_all_algo_with_best_v_lam(...)`   
     * **Function for computing the runtime of each algorithm**  
     `RUNTIME_for_selected_model_SYNTH(...)`

     

* `Fig3_main_scalability.ipynb`  
This file runs the main experiment using the functions and classes defined in `SYNTH_functions.ipynb`. The user varies the number of users and the number of features and calculates the time required by each algorithm.


### References

* https://github.com/yang0110/GraphUCB-and-GraphUCB-Local-Algorithms
