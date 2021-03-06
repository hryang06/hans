# BERTs of a feather
This folder contains data accompanying the paper [BERTs of a feather do not generalize together: Large variability in generalization across models with similar test set performance](https://www.aclweb.org/anthology/2020.blackboxnlp-1.21.pdf), in which we analyzed how 100 instances of BERT fine-tuned on MNLI varied in their performance on the MNLI development set and on the HANS evaluation set.

## Accuracies by model

The files ``berts_of_a_feather_accuracies_by_run.xlsx`` and ``berts_of_a_feather_accuracies_by_run.csv`` give the performance of each of our 100 instances of BERT on each category of example they were evaluated on. (The two files give the same data, just in different file types).

## Model predictions

The file ``all_hans_predictions.txt`` gives each model's prediction for each example in the HANS evaluation set. Each line in this file corresponds to one example in the HANS evaluation set; specifically, it corresponds to the HANS example with the example number that is the line number in ``all_hans_predictions.txt`` minus 1. For instance, line 398 in ``all_hans_predictions.txt`` corresponds to the HANS example with the ID ``ex397``, i.e. the example woth premise _The lawyer helped the artist ._ and hypothesis  _The artist helped the lawyer ._.

The file ``all_mnli_development_set_predictions.txt`` gives each model's prediction for each example in the MNLI development set. Each line in this file corresponds to one example in the MNLI development set; specifically, it corresponds to the MNLI development set example with the example number that is the line number in ``all_mnli_development_set_predictions.txt`` minus 1. For instance, line 398 in ``all_mnli_development_set_predictions.txt`` corresponds to the HANS example with the ID ``397``, i.e. the example woth premise _The percent of total cost for each function included in the model and cost elasticity (with respect to volume) are shown in Table 1._ and hypothesis _Table 1 also shows a picture diagram for each function._

In both of these files, each line lists the predictions made by each of our 100 instances of BERT (in order) for the relevant example in HANS or the MNLI development set.

## Number of correct response

The file ``mnli_development_set_number_of_correct_response.txt`` shows, for each example in the MNLI development set, the number of BERT instances (out of 100) that got that example right. This file includes the premises and hypotheses from the MNLI dataset introduced in the paper [A Broad-Coverage Challenge Corpus for Sentence Understanding through Inference](https://www.aclweb.org/anthology/N18-1101/) by Adina Williams, Nikita Nangia, and Samuel Bowman; please see that paper for license details for the MNLI dataset.

## Model weights

The weights for our 100 fine-tuned instances of BERT will be released on Zenodo soon. Warning: Each of these zip files takes up about 1.1 GB of memory.


## Replicating

This section is under construction; it will be finalized once the model weights are done being uploaded to Zenodo.


```
git clone https://github.com/google-research/bert.git ## Clone BERT
cd bert/
git checkout 88a817c # Probably not necessary...but ensures you are using the same version of the BERT git that we are
create a file named download_glue_data.py and copy this script into it: https://gist.github.com/W4ngatang/60c2bdb54d156a41194446737ce03e2e
python download_glue_data.py --data_dir glue_data --tasks MNLI # make sure using Python 3
cd glue_data
mkdir HANS
cd HANS
copy test_matched.tsv from this git repo into the folder HEUR
Download one of the BERT zip files from the Zenodo repository (e.g., bert_0.zip) and move it into the directory bert
unzip bert_0.zip # creates a folder called bert_0_weights
```
 
## Citing

If you use code or data from this folder, please cite our [paper](https://www.aclweb.org/anthology/2020.blackboxnlp-1.21) (BibTex can be found [here](https://www.aclweb.org/anthology/2020.blackboxnlp-1.21.bib)).



