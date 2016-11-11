# Take a closer look

## Configuration files

Now let's take a closer look at what is going on when you run the analysis.

The Configurations folder contains the configuration files. The Configuration.py file specifies how an analysis should behave. The preconfigured analysis is a top pair analysis called TTbarAnalaysis.  This can be changed later if you wish to look at another analysis, or just use the -a option.
The first portion of the configuration file defines the job and looks like this:

     Job = {
         "Batch"           : True,              (switches progress bar on and off, forced to be off when running in parallel mode)
         "Analysis"        : "TTbarAnalysis",   (names the default analysis to be executed)
         "Fraction"        : 1,                 (determines the fraction of events per file to be analysed)
         "MaxEvents"       : 1234567890,        (determines the maximum number of events per file to be analysed)
         "OutputDirectory" : "results/"         (specifies the directory where the output root files should be saved)
     }

The second portion of the configuration file specifies which processes to include. The locations of the individual files that are to be used for the different processes are set as such:

    Processes = {
        # Diboson processes
        "WW"                    : "Input/MC/mc_105985.WW.root",  (single file)
        ...
        "data_Egamma"           : "Input/Data/DataEgamma*.root", (potentially many files)
    }

Whilst the analysis is running you will see the analysis name (circled in orange below) and the process you are running over (circled in blue below).

![](TTbar.png)

The names chosen for the processes are important as they are the keys used in the infofile.py to determine the necessary scaling factors for correct plotting.


To run over the full set of available data samples (if you have downloaded them) takes between 1 to 1.5 hours in single core mode:

    python RunScript.py -a TTbarAnalysis

Execution times are reduced to ~ 15 minutes in multi core mode:

    python RunScript.py -a TTbarAnalysis -n 4
