This repository contains datasets and scripts to reproduce results from "Improving representation learning of genomic sequence motifs in convolutional netowrks with exponential activations" by Peter K. Koo and Matthew Ploenzke.


#### Dependencies
* Python 3
* Dependencies: Tensorflow r1.15 and r2.0 (tested), matplotlib, numpy, scipy, sklearn, shap, logomaker, pandas, h5py
* meme suite (5.1.0) to run Tomtom  (Note: Parsing issues may occur if a different version of meme is used)


# Overview of main code

There are 6 main tasks and code is labeled accordingly. The description of each script is given below.

### Task 1 -- Classifying TF binding from synthetic data
* task1_step1_train_models.py
* task1_step2_tomtom.sh
* task1_step3_filter_match.py
* task1_step4_plot_filter_match.ipynb
* task1_step5_plot_filters_with_hits.ipynb
* task1_step6_plot_1stlayer_activation_comparison.ipynb
* task1_step7_PWM_scan_comparison.ipynb
* task1_step8_log_activation_train.py
* task1_step9_log_activation_tomtom.sh
* task1_step10_log_activation_filter_match.py
* task1_step11_log_activation_plot_filter_match.ipynb

### Task 2 -- Classifying TF binding from in vivo data
* task2_step1_train_models.py
* task2_step2_tomtom.sh
* task2_step3_filter_match.py
* task2_step4_plot_filter_match.ipynb
* task2_step5_plot_filters_with_hits.ipynb

### Task 3 -- Classifying cis-regulatory codes from synthetic data
* task3_step1_train_model.py
* task3_step2_attribution_scores.py
* task3_step3_plot_attr_score_comparison.ipynb
* task3_step4_plot_attr_logo_comparison.ipynb
* task3_step5_log_activation_train_model.py
* task3_step6_log_activation_attribution_scores.py
* task3_step7_log_activation_plot_attr_score_comparison.ipynb

### Task 4 -- Classifying chromatin accessibility for DNase-seq data from the Basset dataset
* task4_step1_train_model.py
* task4_step2_tomtom.sh
* task4_step3_plot_attr_score_comparison.ipynb

### Task 5 -- Classifying TF binding for ZBED2 ChIP-seq data  
* task5_step1_train_model.py
* task5_step2_plot_attr_score_comparison.ipynb


### Task 6 -- Classifying TF binding for IRF1 ChIP-seq data 
* task6_step1_train_model.py
* task6_step2_plot_attr_score_comparison.ipynb


### Other
* helper.py
	* functions that are useful to run analysis
* plot_activation_functions.ipynb
* tfomics
	* additional useful functions for NN models and interpretability
* model_zoo
	* CNN models used in this study
* generate_data
	* Notebooks used to generate data for Task 1, Task2, and Task3


# Control Experiments

### Check stability of training/validation metrics throughout training
* visualize_training_history.ipynb
* gradient_analysis_step1_train.py
* gradient_analysis_step2_visualize.ipynb

### Check robustness to different initialization strategies
* initialization_step1_train.py
* initialization_step2_tomtom.sh
* initialization_step3_filter_match.py
* initialization_step4_visualize_filter_match.ipynb

### Check robustness to Normal intialization with varying std. dev.
* initialization_sweep_step1_train.py
* initialization_sweep_step2_tomtom.sh
* initialization_sweep_step3_filter_match.py
* initialization_sweep_step4_visualize_filter_match.ipynb

### Check robustness to varying scaling factor in exponential activations
* exp_scale_sweep_step2_tomtom.py
* exp_scale_sweep_step3_filter_match.py
* exp_scale_sweep_step4_visualize.ipynb

### Check robustness of threshold used to visualize filter representations
* threshold_sweep_step1_test.py
* threshold_sweep_step2_tomtom.sh
* threshold_sweep_step3_filter_match.py
* threshold_sweep_step4_visualize_filter_match.ipynb


### Check robustness to number of background sequences for attribution methods
* background_analysis_step1_sweep.py
* background_analysis_step2_plot_sweep.ipynb


# Figures
The figures from the paper are generated by the corresponding notebooks.

### Main Figures
- Fig. 1a: code/plot_activations.ipynb
- Fig. 1b: code/task1_step4_plot_filters_with_hits.ipynb
- Fig. 1c: code/task1_step5_plot_filter_match.ipynb
- Fig. 1d: code/task2_step4_plot_filter_match.ipynb
- Fig. 2a-c: code/task3_step4_plot_attr_score_comparisons.ipynb
- Fig. 2d: code/task3_step5_plot_attr_logo_comparisons.ipynb
- Fig. 3a: code/task4_step3_plot_attr_score_comparison.ipynb
- Fig. 3b: code/task5_step2_plot_attr_score_comparison.ipynb
- Fig. 3c: code/task6_step2_plot_attr_score_comparison.ipynb

### Extended Data Figures
- Extended Data Fig. 1a,b: code/task1_step5_plot_filter_match.ipynb
- Extended Data Fig. 1c,d: code/task1_step7_PWM_scan_comparison.ipynb
- Extended Data Fig. 1e: code/task1_step11_log_activation_plot_filter_match.ipynb
- Extended Data Fig. 2a,b: code/task3_step4_plot_attr_score_comparisons.ipynb 
- Extended Data Fig. 2c,d: code/task3_step5_plot_attr_logo_comparisons.ipynb

### Supplemental Figures
- Supp Fig. 1: code/task1_step4_plot_filters_with_hits.ipynb
- Supp Fig. 2: code/task1_step4_plot_filters_with_hits.ipynb
- Supp Fig. 3: code/controls/visualize_training_history.ipynb
- Supp Fig. 4: code/controls/gradient_analysis_step2_visualize.ipynb
- Supp Fig. 5a: code/controls/initialization_step4_visualize_filter_match.ipynb
- Supp Fig. 5b: code/controls/initialization_sweep_step4_visualize_filter_match.ipynb
- Supp Fig. 6: code/task2_step5_plot_filters_with_hits.ipynb
- Supp Fig. 7: code/plot_activations.ipynb
- Supp Fig. 8: code/task2_step4_plot_filter_match.ipynb
- Supp Fig. 9: code/controls/exp_scale_sweep_step4_visualize.ipynb
- Supp Fig. 10: code/task1_step6_plot_1stlayer_activation_comparison.ipynb
- Supp Fig. 11a: code/task3_step4_plot_attr_score_comparisons.ipynb
- Supp Fig. 11b: code/task3_step7_log_activation_plot_attr_score_comparison.ipynb
- Supp Fig. 12: code/task4_step3_plot_attr_score_comparison.ipynb
- Supp Fig. 13: code/task5_step2_plot_attr_score_comparison.ipynb
- Supp Fig. 14: code/task6_step2_plot_attr_score_comparison.ipynb
- Supp Fig. 15: code/controls/threshold_sweep_step4_visualize_filter_match.ipynb
- Supp Fig. 16: code/controls/background_analysis_step2_plot_num_background_sweep.ipynb




