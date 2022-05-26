## [Figure 4]Semi-Parametric Contextual Bandits with Graph-Laplacian Regularization

This repository provides codes for the reproduction of Figure 4 in the paper "Semi-Parametric Contextual Bandits with
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

* `lastfm-preproc.ipynb`   
This file performs preprocessing of the lastfm data and stores the preprocessed data (`item_features_full.npy`, `item_IDs_full.npy`, `user_IDs_full.npy`, `adjmtx_full.npy`, `list_items_rwd1.npy`, `list_items.npy`, `list_item_features.npy`, `list_user_history.npy`) in a folder named "preproc_output". These data will be used in `Fig4_main_lastfm.ipynb`.

* `REAL_functions.ipynb` This file contains:
 
     * **Function for generating Laplacian matrix**   
     `graph_to_laplacian(ADJOINT_MTX, LAPLACIAN_TYPE)`    
     LAPLACIAN TYPE can be set as either "random_walk" or "symmetric_normalized"
     * **Class for each algorithm**  
     `SemiRidgeGraphThompson()` (Proposed), `IndividualThompson()`, `GUCB_local()`, `CLUB()`, `LinTS_Single()`, `SemiTS_Single()`, `IndividualSemiRidgeGraphThompson()`    
     Each class contains 2 main functions, one for choosing arms and another for updating the parameter estimates.  
     * **Function for tuning the hyperparameters 'v' and 'lambda' for each algorithm**  
     `tuning_v_and_lam_for_SELECTED_algo(v_set, lam_set, .....)`   
     The inputs 'v_set' and 'lam_set' are sets of candidate values of 'v' and 'lambda' respectively: 'v_set=[0.0001, 0.001, 0.01, 0.1, 1.]' and 'lam_set=[0.008, 0.04, 0.2, 1., 5]')  
     * **Function for plotting the cumulative regret of each algorithm for each combination of hyperparameters**  
     `show_tuning_results(MODEL,...)` 
     * **Function for selecting the best combination of hyperparameters for each algorithm**  
     `return_best_v_and_lambda_pair_real(...)`  
     * **Function for running each algorithm multiple times with the best set of hyperparameters**  
     `run_all_algo_with_best_v_lam_real(...)`   
     * **Function for plotting the median and quantiles of the cumulative regret of each algorithm**  
     `show_and_save_plot(...)`  
     

* `Fig4_main_lastfm.ipynb`  
This file runs the main experiment using the functions and classes defined in `REAL_functions.ipynb` and the data preprocessed by `lastfm-preproc.ipynb`. 


### References

* https://github.com/yang0110/GraphUCB-and-GraphUCB-Local-Algorithms
