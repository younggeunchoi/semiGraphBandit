## [Figure 2_right]Semi-Parametric Contextual Bandits with Graph-Laplacian Regularization

This repository provides codes for the reproduction of Figure 2 in the paper "Semi-Parametric Contextual Bandits with
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
     * **Function for tuning the hyperparameters 'v' and 'lambda' for each algorithm**  
     `tuning_v_and_lam_for_SELECTED_algo(v_set, lam_set, .....)`   
     The inputs 'v_set' and 'lam_set' are sets of candidate values of 'v' and 'lambda' respectively: 'v_set=[0.0001, 0.001, 0.01, 0.1, 1.]' and 'lam_set=[0.008, 0.04, 0.2, 1., 5]')  
     * **Function for plotting the cumulative regret of each algorithm for each combination of hyperparameters**  
     `show_tuning_results(MODEL,...)` 
     * **Function for selecting the best combination of hyperparameters for each algorithm**  
     `return_best_v_and_lambda_pair(...)`  
     * **Function for running each algorithm multiple times with the best set of hyperparameters**  
     `run_all_algo_with_best_v_lam(...)`   
     * **Function for plotting the median and quantiles of the cumulative regret of each algorithm**  
     `show_and_save_plot(...)`  
     

* `Fig2_main_prop.ipynb`  
This file runs the main experiment using the functions and classes defined in `SYNTH_functions.ipynb`. The user specifies the number of simulations ('simul_n'), the number of users ('user_num'), the number of arms ('arm_num'), the dimension of contexts ('dimension'), the time horizon ('time_horizon'), the standard deviation of the Gaussian error ('const_R'), the candidate values of hyperparameters ('v_set' and 'lam_set'), the details of the graph ('prob', 'gamma'), the type of Laplacian graph('lap_type'), the graph model ('our_graph_type'), the intercept in the reward model (if 'nu_type' is set to "0", the reward model is stationary with intercept set to 0, otherwise, the reward model is a semiparametric model with a time-varying intercept) etc. **Also, the user specifies the proportion of sign-reversed nodes in the graph.**

### References

* https://github.com/yang0110/GraphUCB-and-GraphUCB-Local-Algorithms
