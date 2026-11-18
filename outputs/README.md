# outputs/: what each file is

Every file here is written by `01_Data_Preprocessing.ipynb` (step 2–3 files) or `02_Model_Training.ipynb` (everything else). Each figure (`.png`) has a `.csv` with the numbers behind it (the step 6 calibration figure uses `step6_calibration_bins_validation.csv`).

"Test" files come from the single test evaluation, or from its saved predictions with no refitting. "Validation" files never use test rows.

## Main report items
| File | Report item |
|---|---|
| `table1_test_metrics_M0_M2.csv` | **Table 1** (and appendix Table A3). Recall, precision and F1 at 0.15 and 0.50, plus ROC-AUC; M0–M2, both model types, test |
| `table2_test_metrics_M2_vs_M3_module.csv` | **Table 2** (and appendix Table A6). The same for M2-module vs M3 (SDOH-module test respondents) |
| `fig_main1_confusion_matrices_logistic_test.png` | **Figure 1.** Confusion matrices, M0–M2 logistic regression, cutoff 0.15, test |
| `fig_main2_subgroup_recall_precision_M2_logistic_test.png` | **Figure 2.** Subgroup recall and precision, M2 logistic regression, 0.15, test |
| `fig_main3_confusion_M2_vs_M3_logistic_015_test.png` | **Figure 3.** Confusion matrices, M2-module vs M3 logistic regression, 0.15, test |

## Appendix items
| File | What it shows |
|---|---|
| `step10_threshold_table_M2_logistic_test.csv` | **Table A4.** M2 logistic regression at cutoffs 0.10, 0.15, 0.20, 0.30, 0.50 (test; saved predictions). The look is recorded in `step10_threshold_table_record.csv` |
| `step7b_test_by_group_cutoff015.csv` | **Table A5.** Subgroup prevalence, recall, precision and false-positive rate at 0.15 (rows for M2 logistic regression) |
| `fig_appx_subgroup_recall_precision_M2_logistic_test_both_cutoffs.png` | **Figure A1.** Figure 2 at both cutoffs |
| `fig_appx_subgroup_recall_precision_M2_logistic_vs_forest_015_test.png` | **Figure A2.** M2 logistic regression and random forest by subgroup, cutoff 0.15 |
| `step8_test_proposal_rule_check.csv` | Subgroup check for Table A6 (the proposal's "does SDOH help" rule) |

## Records behind numbers in the text
| File | What it is |
|---|---|
| `step2_rebuild_counts.csv` | Row counts after cleaning, checked against the expected values |
| `step3_split_sizes.csv` | Train / validation / test sizes and diabetes rates |
| `step3_leakage_checks_1_2.csv`, `step3_leakage_checks_3_6.csv`, `step3_leakage_check4_medians_means.csv`, `step3_leakage_check5_shuffles.csv`, `step7_leakage_recheck_3_6.csv` | The six leakage checks (all passed), and their rerun before the test evaluation |
| `step3_all_rows_feature_stats.csv` | Missingness and summaries per feature |
| `step7_test_results.csv`, `step7b_test_results_cutoff015.csv`, `step7b_test_results_050_vs_015.csv` | Test metrics, M0–M2, at 0.50 and 0.15 |
| `step7_test_by_group.csv`, `step8_test_by_group_*.csv` | Full subgroup tables at 0.50, and for the SDOH comparison |
| `step8_test_results_module.csv`, `step8_test_M3_minus_M2_overall.csv` | SDOH comparison on test |
| `step7_test_evaluation_record.csv`, `step7b_cutoff015_record.csv`, `step8_test_evaluation_record.csv` | Timestamps of the official test evaluations |
| `step5_chosen_settings_final.csv`, `step8_chosen_settings_module_final.csv` | Final tuned settings |

## Validation and tuning files
Not reported as results; kept for traceability.
- Validation: `step6_validation_results_final_settings.csv`, `step6_calibration_*` and `fig_step6_calibration_validation.png` (the calibration check), `step8_validation_results_module*.csv`, `step8_calibration_bins_validation_module.csv`
- Tuning: `step5_tuning_cv_results.csv`, `step5b_tuning_extension_M2_rf.csv`, `step5_chosen_settings.csv`, `step8_tuning_cv_results_module.csv`, `step8b_tuning_extension_module_rf.csv`, `step8_chosen_settings_module.csv`

## Other views of the same results
Same models and test predictions, drawn differently; not used in the report.
| File | What it shows |
|---|---|
| `fig_step7_confusion_matrices_test.png`, `fig_step7b_confusion_matrices_test_cutoff015.png` | Confusion matrices for all M0–M2 models at 0.50 and at 0.15 |
| `fig_step7_subgroup_recall_fpr_test.png`, `fig_step7b_subgroup_recall_fpr_test_cutoff015.png` | Subgroup recall and false-positive rate, M2 models, at 0.50 and at 0.15 |
| `fig_step8_confusion_matrices_M2_vs_M3_test.png` | M2-module vs M3, both model types, both cutoffs (8 panels) |

`outputs/scores/` (predicted scores cache) is not in the repository; notebook 02 rebuilds it.
