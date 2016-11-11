# Take a closer look

## Configuration files

Now let's take a closer look at what is going on when you run the analysis.

The Configurations folder contains the configuration files. The Configuration.py file specifies how an analysis should behave. 

The preconfigured analysis is a top pair analysis called TTbarAnalaysis.  This can be changed later if you wish to look at another analysis, or just use the -a option.
The first portion of the configuration file defines the job and looks like this:

Look at the code directly here: [Configuration.py](https://github.com/atlas-outreach-data-tools/atlas-outreach-data-tools-framework/blob/master/Configurations/Configuration.py)

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


## Plotting

Now let's take a closer look at what is going on when you plot the results of your analysis.

    python PlotResults.py Configurations/PlotConf_TTbarAnalysis.py

The plotting configuration file allows you to steer the plotting process. Each analysis has its own plotting configuration file to accommodate changes in background composition or histograms required.

Look at the code directly here: [PlotConf_TTbarAnalysis.py](https://github.com/atlas-outreach-data-tools/atlas-outreach-data-tools-framework/blob/master/Configurations/PlotConf_TTbarAnalysis.py)

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


Each Plot consists of several depictions of paintables. A depiction is a certain standard type of visualising information. Available depictions include simple plots, ratios and agreement plots. A paintable is a histogram or stack with added information such as colours and which processes contribute to said histogram. A simple definition of paintables may look like this:

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

There are currently three types of depictions available: Main, Agreement and Ratio. Main type plots will simply show the paintables in a simple plot fashion. Ratio type plots will show the ratio of the first paintable w.r.t. the second paintable. Agreement type plots are typically used to evaluate the agreement between two paintables (usually the stack of predictions and the data).

The order of the depictions is determined in line 2 of the code example above.


![](Output/lepPT.png)

Here we can see an agreement plot above and ratio plot below for lepton $$p_T$$.