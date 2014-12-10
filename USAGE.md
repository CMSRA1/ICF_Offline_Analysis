# check out the offline analysis code (used for making tables, closure tests, rootfiles etc)

git clone https://github.com/CMSRA1/ICF_Offline_Analysis

# make a directory for your rootfiles

mkdir rootfiles

# make directories in here to contain your rootfiles, e.g. rootfiles/AlphaT0p53_noSITV_01Dec_v0

# cd into RA1_Offline_Analysis

cd RA1_Offline_Analysis

# edit the run_details.py file to include your new directory. This requires a new entry in the dict

out_dict["AlphaT0p53_noSITV_01Dec_v0"] = {

    "path_name": "rootfiles/rootfiles/AlphaT0p53_noSITV_01Dec_v0",
    
    # All Runs
    "had_lumi": 18.493,
    "mu_lumi": 19.131,
    "ph_lumi": 19.12,

    # taken from parked final (change if necessary)
    "wj_corr": 0.93,
    "dy_corr": 0.94,
    "tt_corr": 1.18,

    }

# use these values. they represent the luminosities of each data sample and the HT sideband corrections
# set the variable "selector" (at the top of the file) to be the key of your new dictionary entry

# now try running to make some tables

./Prediction_RA1.py -u 2

# this produce vanilla (not formula method) tables for the le3j category
2 - le3j
3- ge4j
all - ge2j

-u - vanilla tables
-n - formula tables
-c closure tests (additional arguement is 'jetcat')
-r - rootfiles for input to stats code
-m - sideband normalisation

# different variables can be changed in Prediction_RA1.py, such as the alphaT slice, the HT bins, whether to 
# apply the sideband corrections etc. etc.
