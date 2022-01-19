## dl_ids_survey

### Description

This is the code provided by the author of the paper entitled Deep learning Methods in Network intrusion Detection: 
A Survey and an Objective Comparison. The details of the paper are as follows.
```
@article{GAMAGE2020102767,
    title = {Deep learning methods in network intrusion detection: A survey and an objective comparison},
    journal = {Journal of Network and Computer Applications},
    volume = {169},
    pages = {102767},
    year = {2020},
    issn = {1084-8045},
    doi = {https://doi.org/10.1016/j.jnca.2020.102767},
    url = {https://www.sciencedirect.com/science/article/pii/S1084804520302411},
    author = {Sunanda Gamage and Jagath Samarabandu},
    keywords = {Network intrusion detection, Deep learning, Deep neural networks, Survey},
}
```

### Preparation
The environment I tested is shown below. If you download the module is too slow, 
you can add a parameter at the back of the pip `-i https://pypi.tuna.tsinghua.edu.cn/simple`
```
python==3.6
tensorflow==1.12.0
Keras==2.2.4
scikit-learn>=0.20.3
scipy>=1.2.1
matplotlib>=3.0.2
pandas>=0.24.2
h5py==2.9.0
tables==3.7.0
openpyxl==2.6.2
```

The location of each dataset is shown below. You can download it yourself by opening the link.
```
KDD99：http://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html
NSL-KDD：https://www.unb.ca/cic/datasets/nsl.html
CIC-IDS2017：https://www.unb.ca/cic/datasets/ids-2017.html
CIC-IDS2018：https://www.unb.ca/cic/datasets/ids-2018.html
```

Note that the first three dataset are easy to download, but the fourth one requires amazon's tools to be installed
and then downloads using the following commands (mentioned on the website).

```
# the files need to use in this project
aws s3 ls --no-sign-request "s3://cse-cic-ids2018" --recursive --human-readable --summarize
2018-10-12 00:02:25    0 Bytes Processed Traffic Data for ML Algorithms/
2018-10-12 00:02:49  336.0 MiB Processed Traffic Data for ML Algorithms/Friday-02-03-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:03:10  318.3 MiB Processed Traffic Data for ML Algorithms/Friday-16-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:03:33  365.1 MiB Processed Traffic Data for ML Algorithms/Friday-23-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:03:59    3.8 GiB Processed Traffic Data for ML Algorithms/Thuesday-20-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:08:38  102.8 MiB Processed Traffic Data for ML Algorithms/Thursday-01-03-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:08:48  358.5 MiB Processed Traffic Data for ML Algorithms/Thursday-15-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:09:20  364.9 MiB Processed Traffic Data for ML Algorithms/Thursday-22-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:09:44  341.6 MiB Processed Traffic Data for ML Algorithms/Wednesday-14-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:10:12  313.7 MiB Processed Traffic Data for ML Algorithms/Wednesday-21-02-2018_TrafficForML_CICFlowMeter.csv
2018-10-12 00:10:33  199.6 MiB Processed Traffic Data for ML Algorithms/Wednesday-28-02-2018_TrafficForML_CICFlowMeter.csv

# download .csv mentioned above
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Friday-02-03-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Friday-16-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Friday-23-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Thuesday-20-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Thursday-01-03-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Thursday-15-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Thursday-22-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Wednesday-14-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Wednesday-21-02-2018_TrafficForML_CICFlowMeter.csv" .
aws s3 cp --no-sign-request "s3://cse-cic-ids2018/Processed Traffic Data for ML Algorithms/Wednesday-28-02-2018_TrafficForML_CICFlowMeter.csv" .
```

When you download all the dataset, you need to put the dataset on the same level with this project.
The file structure is showed below.
```
.
|--Datasets
    |--KDD99: This dicectory stores the data files of the KDD99 dataset.
    |--NSL_KDD: This dicectory stores the data files of the NSL-KDD dataset.
    |--
    |--
|--dl_ids_survey
|--...(others)
```

### Run the code

The file structure of the project is explained below.
```
dl_ids_survey
|--experiment_specs
    |--additional_exps
    |--selected_model_tests: Model stability test
    |--tuning_exps: The influence of hype parameter changes on indicators
|--models: definitions of the models
    |--__init__.py: 
    |--ae.py
    |--ae_ann.py
    |--ann.py: feed-forward neural network
    |--dbn.py
    |--lstm.py
    |--rf.py
|--.gitignore
|--keras_callbacks.py
|--prepare_data.py: preprocess the dataset
|--README.md
|--run_experiments.py: actually perform various experiments
|--utility.py: some common functions
```

The preprocessed code can be run directly, but the input and output file
paths need to be configured. Running the `run_experiments.py`, you need to add extra 
parameter which is a .csv file mentioned in the experiments_specs directory.
(e.g. `python run_experiments.py experiment_specs/additional_exps/ann_data_efficiency.csv`)

To make it easy to copy and paste, I take a note about the path, and the work
it did below.

```
# Testing two ANN models(Shallow/Deep) in four data sets 
experiment_specs/tuning_exps/ann_experiments.csv

# 
experiment_specs/selected_model_tests/selected_ae_ann.csv

# 
experiment_specs/selected_model_tests/selected_lstm.csv
```





