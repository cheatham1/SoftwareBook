# Getting started
## ATLAS open data

The ATLAS collaboration has made some data available to everyone.

You need to download some code to get started. It will enable to take a first look at the newly released ATLAS data.  You can then modify the code and make it you own.

## Setup

/////*
The data and tools **will be** available on the CERN Open Data Portal,
 but **for now** can just access tools here:
 https://gitlab.cern.ch/fthomas/ATLASDatasetTools
 and data here:
 /afs/cern.ch/user/f/fthomas/work/ATLASDataset/PublicationDatasets.zip
*///////

Select the **ATLAS Public Release Spring 2016** at the [CERN Open Data Portal](http://opendata.cern.ch/education/ATLAS).

Download the code.  In the root directory you will see five directories, a README file plus two python scripts.  The python scripts are RunScript.py and PlotResults.py.  The directory names are Analysis, Configurations, Input, Plotting and Output.

Download the data into your Input directory. 

You need to have [ROOT](https://root.cern.ch/downloading-root) installed.  ROOT is a framework for data processing, at the heart of the research on high-energy physics. 

# Taking a look at the data
## Analysis

As a first go, to check whether everything works fine, you can run 

    python RunScript.py -a TTbarAnalysis -s "WW, WZ"

This runs the code using the TTbarAnalysis with just the WW and WZ samples.

The runscript has several options which are displayed by typing

    python RunScript.py --help

The options include:

    -a,            --analysis              overrides the analysis that is stated in the configuration file
    -s,            --samples               comma separated string that contains the keys for a subset of processes to run over
    -p,            --parallel              enables running in parallel (default is single core use)
    -n NWORKERS,   --nWorkers NWORKERS     specifies the number of workers if multi core usage is desired (default is 4)
    -c CONFIGFILE, --configfile CONFIGFILE specifies the config file to be read (default is Configurations/Configuration.py)

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


To run over the full set of available samples using multiple cores. 

    python RunScript.py -a TTbarAnalysis -n 4

Execution times are between 1 to 1.5 hours in single core mode or ~ 15 minutes in multi core mode.

## Plotting

Results for a particular analysis may be plotted using the relevant plotting configuration file. In the TTbarAnalysis case :

    python PlotResults.py Configurations/PlotConf_TTbarAnalysis.py

The resulting histograms will be put into the Output folder.

The plotting configuration file allows you to steer the plotting process. Each analysis has its own plotting configuration file to accommodate changes in background composition or histograms required.

General information for plotting include the Luminosity and InputDirectory located at the top of the file:

      config = {
          "Luminosity"     : 1000,
          "InputDirectory" : "results",
          ...

The names of the histograms to be drawn can be specified like so:

     "Histograms" : {
          "WtMass"          : {},
          "etmiss"          : {rebin : 4, log_y : True},
          "lep_phi"         : {"y_margin" : 0.6},
          ...

Note that it is possible to supply additional information via a dictionary like structure to further detail the per histogram options. Currently available options are:

    rebin    : int   - used to merge X bins into one. Useful in low statistics situations
    log_y    : bool  - if True is set as the bool the main depiction will be drawn in logarithmic scale
    y_margin : float - sets the fraction of whitespace above the largest contribution in the plot. Default value is 0.1.


## Definition of Paintables and Depictions


Each Plot consists of several depictions of paintables. A depiction is a certain standard type of visualising information. Availabe depictions include simple plots, ratios and agreement plots. A paintable is a histogram or stack with added information such as colors and which processes contribute to said histogram. A simple definition of paintables may look like this:

    'Paintables': {
        "Stack": {
            "Order"     : ["Diboson", "DrellYan", "W", "Z", "stop", "ttbar"],
            "Processes" : {                
                "Diboson" : {
                    "Color"         : "#fa7921",
                    "Contributions" : ["WW", "WZ", "ZZ"]},

                "DrellYan": {       
                    "Color"         : "#5bc0eb",
                    "Contributions" : ["DYeeM08to15", "DYeeM15to40", "DYmumuM08to15", "DYmumuM15to40", "DYtautauM08to15", "DYtautauM15to40"]},
                ...
        },

        'Higgs': {
            'Color': '#0000ff', 
            'Contributions': ['ggH125_WW2lep']},

        "data" : {
            "Contributions": ["data_Egamma", "data_Muons"]}

Stack and data are specialised names for paintables. This ensures that only one stack and one data representation are present in the visual results. A stack shows the different processes specified in "order" stacked upon each other to give an idea of the composition of the simulated data. The definitions for these individual processes are defined under "Processes". Each process has a certain colour and a list of contributing parts that comprise it. These contributing parts have to fit the keys used in both the run configuration and the infofile.py.

Data is a specialised paintable which is geared toward the standard representation of data. Since the data does not need to be scaled there is no need to align the used names in contributions with those found in the infofile.py. However, they still have to fit the ones used in the configuration.py.

All otherwise named paintables (like "Higgs" in the example) are considered as "overlays". Overlays are used to show possible signals or to compare shapes between multiple overlays (see for instance in the ZPrimeAnalysis).

The paintables can be used in depictions like so:

    "Depictions": {
        "Order"       : ["Main", "Data/MC", "Z`Ratio"],
        "Definitions" : {
            "Data/MC": {
                "type"       : "Agreement",
                "Paintables" : ["data", "Stack"]},

            "Main": {
                "type"      : "Main",
                "Paintables": ["Stack", "data"]},

            'Z`Ratio': {
                'type'       : 'Ratio',
                'Paintables' : ['ZPrime1000', 'ZPrime500']},
        }

There are currently three types of depictions available: Main, Agreement and Ratio. Main type plots will simply show the paintables in a simple plot fashion. Ratio type plots will show the ratio of the first paintable w.r.t. the second paintable. Agreement type plots are typically used to evaluate the agreement between two paintables (usually the stack of predictions and the data).

The order of the depictions is determined in line 2 of the code example above.

# In Depth Information
## Analysis Code

The analysis code is located in the Analysis folder. It is used to write out histograms for the individual input files which will be used for plotting purposes later.

The basic code implementing the protocol to read the files and how the objects can be read is in Tuplereader.py. Have a look there to see which information is available. The general analysis flow can be found in Job.py whereas the base class for all concrete analyses is located in Analysis.py.

It is recommended to start out by modifying one of the existing analyses, e.g. the ZAnalysis located in ZAnalysis.py. If you want to add an analysis, make sure that the filename is the same as the class name, otherwise the code will not work.

The files associated with the processes are found via python's glob module, enabling the use of unix style wildcards.