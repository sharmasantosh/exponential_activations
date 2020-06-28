This repository contains datasets and scripts to reproduce results from "Improving representation learning of genomic sequence motifs in convolutional netowrks with exponential activations" by Peter K. Koo and Matthew Ploenzke.


#### Dependencies
* Python 3
* Dependencies: Tensorflow r1.15 (tested), matplotlib, numpy, scipy, sklearn, shap, logomaker, pandas, h5py
* meme suite (5.1.0) to run Tomtom


## Overview of the code

There are 6 main tasks and code is labeled accordingly. The description of each script is given below.

#### Task 1 -- Classifying TF binding from synthetic data
* task1_train_model.py
	* trains models (CNN-4, CNN-25, and CNN-deep) with various activation functions on the task1 synthetic dataset for 10 different trials 
		* dataset is in /data/syntehtic_dataset.h5
		* to generate again, run code/generate_data/task1_generate_synthetic_dataset.ipynb
	* model parameters saved to results/task1/model_params
	* tests each model on held-out test data 
		* statistics saved to results/task1/task1_classification_performance.tsv 
		* results for each trial saved to results/task1/task1_performance_results.pickle
	* generates a plot of sequence logos for 1st layer filters 
		* plots saved to results/task1/conv_filters
	* generates a meme file for 1st layer filters 
		* files saved to results/task1/conv_filters
* task1_tomtom.sh
	* performs a tomtom motif comparison search of the 1st layer filter representations (meme files) against the JASPAR database (located in /data/JASPAR_CORE_2016_vertebrates.meme)
		* results are stored in a directory in results/task1/conv_filters under: model_activation_trial
* task1_filter_match.py
	* quantifies motif comparison results against the ground truth motifs from the synthetic dataset
		* summary statistics saved to results/task1/task1_filter_results.tsv
		* results for each trial saved to results/task1/task1_filter_results.pickle
* task1_plot_filter_match_synthetic.ipynb
	* Plots comparison classification performance of each model and activation function (results/task1/task1_performance_roc.pdf and results/task1/task1_performance_pr.pdf)
	* Plots comparison of filter match to relevant motifs in the Jaspar database for different activations (results/task1/task1_filter_match.pdf)
	* Plots comparison of filter match to relevant motifs in the Jaspar database for modified activations (results/task1/task1_filter_match_modified_activations.pdf)
	* Plots comparison of filter match to relevant motifs in the Jaspar database for an ablation study of modified activations (results/task1/task1_filter_match_ablation.pdf)
	* Plots comparison of filter match to any motifs in the Jaspar database (results/task1/task1_filter_match_any_JASPAR.pdf)
* task1_Plot_filters_with_hits.ipynb
	* replots 1st layer filters with y-labels given by a tomtom hit to a ground truth motif (results/task1/conv_filters)
* task1_PWM_scan_comparison.ipynb
	* comparison of PWM scans vs CNN with exponential activations (saved to: results/task1/pwm_comparison)
* task1_train_model_log.py
	* trains models with log-based activation functions on the task1 synthetic dataset for 10 different trials 
	* model parameters saved to results/task1/model_params
	* tests each model on held-out test data 
		* statistics saved to results/task1/task1_classification_performance_log.tsv 
		* results for each trial saved to results/task1/task1_performance_results_log.pickle
	* generates a plot of sequence logos for 1st layer filters 
		* plots saved to results/task1/conv_filters
	* generates a meme file for 1st layer filters 
		* files saved to results/task1/conv_filters
* task1_tomtom_log.sh
	* performs a tomtom motif comparison search of the 1st layer filter representations (meme files) against the JASPAR database
		* results are stored in a directory in results/task1/conv_filters under: model_activation_trial
* task1_filter_match_log.py
	* quantifies motif comparison results against the ground truth motifs from the synthetic dataset
		* summary statistics saved to results/task1/task1_filter_results_log.tsv
		* results for each trial saved to results/task1/task1_filter_results_log.pickle
* task1_plot_filter_match_synthetic-log.ipynb
	* 	* Plots comparison of filter match to relevant motifs in the Jaspar database for different activations (results/task1/task1_filter_match_log.pdf)
* task1_plot_synthetic_filters_with_hits_log.ipynb
	* replots 1st layer filters with y-labels given by a tomtom hit to a ground truth motif to results/task1/conv_filters


#### Task 2 -- Classifying TF binding from in vivo data
* task2_train_model.py
	* trains all models (CNN-4, CNN-25, and CNN-deep) with various activation functions for 10 trials on the truncated-DeepSea dataset 
		* dataset is over 100 MBs, so is not included in the repository
		* to generate, run code/generate_data/task2_generate_invivo_dataset.ipynb
	* model parameters saved to results/task2/model_params
	* tests models on held-out test data 
		* statistics saved to results/task2/task2_classification_performance.tsv 
		* results for each trial saved to results/task2/task2_performance_results.pickle
	* generates a plot of sequence logos for 1st layer filters 
		* plots saved to results/task2/conv_filters
	* generates a meme file for 1st layer filters 
		* files saved to results/task2/conv_filters
* task2_tomtom.sh
	* performs a tomtom motif comparison search of the 1st layer filter representations (meme files) against the JASPAR database
		* results are saved to results/task2/conv_filters
* task2_filter_match.py
	* quantifies motif comparison results against the known motifs for TFs in JASPAR database
		* summary statistics saved to results/task2/task2_filter_results.tsv
		* results for each trial saved to results/task2/task2_filter_results.pickle
* task2_plot_filter_match_invivo.ipynb
	* Plots comparison classification performance of each model and activation function (results/task2/task2_performance_roc.pdf and results/task2/task2_performance_pr.pdf)
	* Plot comparison of filter match to relevant motifs in the Jaspar database for different activations (results/task2/task2_filter_match.pdf)
	* Plot comparison of filter match to relevant motifs in the Jaspar database for modified activations (results/task2/task2_filter_match_modified_activations.pdf)
	* Plot comparison of filter match to any motifs in the Jaspar database (results/task2/task2_filter_match_any_JASPAR.pdf)
* task2_plot_invivo_filters_with_hits.ipynb
	* replots 1st layer filters with y-labels given by a tomtom hit to a ground truth motif (results/task2/conv_filters)


#### Task 3 -- Classifying cis-regulatory codes from synthetic data
* task3_train_model.py
	* trains models (CNN-local and CNN-dist) with various activation functions for 10 trials on the synthetic regulatory code dataset 
		* dataset is in /data/synthetic_code_dataset.h5
		* to generate again, run code/generate_data/task3_generate_synthetic_code_dataset.ipynb
	* model parameters saved to results/task3/model_params
	* tests models on held-out test data 
		* statistics saved to results/task3/task3_classification_performance.tsv 
		* results for each trial saved to results/task3/task3_performance_results.pickle
* task3_attribution_scores.py
	* generates attribution maps for saliency maps, mutagenesis, integrated gradients and DeepSHAP for each model and each trial.  Results for each trial are grouped together into a saved file: (results/task3/scores/model_name_activation.pickle)
* task3_plot_attr_score_comparison.ipynb
	* plots a comparison of the attribution scores against ground truth from a sequence model and saves results to (results/task3/): task3_compare_attr_score_activations.pdf, task3_compare_attr_score_modified.pdf, task3_compare_cnn_attr_score_performance.pdf, task3_compare_cnn_attr_score_roc.pdf, task3_compare_cnn_attr_score_pr.pdf, task3_compare_attr_methods_roc.pdf, and task3_compare_attr_methods_pr.pdf
* task3_plot_attr_logo_comparison.ipynb
	* plots a comparison of the attribution maps and saves results to (results/task3/attr_logo_plots)
* task3_train_model_log.py
	* performs experiments with log_relu activations with and without L2-regularization 
	* model parameters saved to results/task3/model_params
* task3_attribution_scores_log.py
	* generates attribution maps for saliency maps for each model in train3_train_model_log.py and saves results to: results/task3/scores/model_name_activation_l2.pickle
* task3_plot_attr_score_comparison_log.ipynb
	* Plots a comparison of interpretability results from task3_attribution_scores_log.py and saves plots to: task3_compare_attr_score_auroc_log.pdf and task3_compare_attr_score_pr_log.pdf
* task3_sweep_num_background.py
	* systematically try different number of reference sequences from 1 to 25 and store in num_background_sweep.pickle
* task3_plot_num_background_sweep.ipynb
	* plot results from task3_sweep_num_background.py


#### Task 4 -- Classifying chromatin accessibility for DNase-seq data from the Basset dataset
* task4_train_model.py
	* trains a Basset model with relu and exponential activations on the full Basset dataset (data/er.h5) <-- Need to download dataset (10GB) via https://github.com/davek44/Basset
	* model parameters saved to results/task4/model_params
	* tests models on held-out test data 
		* statistics saved to results/task4/task4_classification_performance.tsv 
	* generates a plot of sequence logos for 1st layer filters 
		* plots saved in results/task4/conv_filters)
	* generates a .meme file for 1st layer filters 
		* files saved in results/task4/conv_filters)
* task4_tomtom.sh
	* performs a tomtom motif comparison search of the 1st layer filter representations (.meme files) against the JASPAR database
		* results are stored in a directory in results/task4/conv_filters
* task4_plot_attr_score_comparison.ipynb
	* plots a comparison of saliency maps for sequences with Basset model with relu activations and exponential activations (saves to: task4/attr_plots)

#### Task 5 -- Classifying TF binding for ZBED2 ChIP-seq data  
* task5_train_model.py
	* trains a Residualbind model with relu and exponential activations on the ZBED2 ChIP-seq dataset (data/ZBED2_400_h3k27ac.h5)
	* model parameters saved to results/task5/model_params
	* tests models on held-out test data 
		* statistics saved to results/task5/task5_classification_performance.tsv 
* task5_plot_attr_score_comparison.ipynb
	* plots a comparison of saliency maps for sequences with Residualbind with relu activations and exponential activations (saves to: task5/attr_plots)


#### Task 6 -- Classifying TF binding for IRF1 ChIP-seq data 
* task6_train_model.py
	* trains a Residualbind model with relu and exponential activations on the IRF1 ChIP-seq dataset (data/IRF1_400_h3k27ac.h5)
	* model parameters saved to results/task6/model_params
	* tests models on held-out test data 
		* statistics saved to results/task5/task5_classification_performance.tsv 
* task6_plot_attr_score_comparison.ipynb
	* plots a comparison of saliency maps for sequences with Residualbind with relu activations and exponential activations (saves to: task6/attr_plots)


#### Other
* helper.py
	* functions that are useful to run analysis
* tfomics
	* additional useful functions for NN models and interpretability
* model_zoo
	* CNN models used in this study
* generate_data
	* Notebooks used to generate data for Task 1, Task2, and Task3
	


