# Take a look at the data

In your terminal window, you are in the main directory ATLAS-DataAndTools.  Here you can see RunScript.py and PlotResults.py


## Run an analysis

Type the following into the command line

    python RunScript.py -a TTbarAnalysis -s "WW,WZ"

This runs the code called 'TTbarAnalysis' with just the WW and WZ data samples.

The analysis should run, telling you about Event Statistics and complete by saying "Job WZ: finished successfully".


![](Output/RunScriptWWWZ.png)


The resulting histograms are put into the results folder.


The RunScript has several options which are displayed by typing

    python RunScript.py --help

The options include:

    -a,            --analysis              overrides the analysis that is stated in the configuration file
    -s,            --samples               comma separated string that contains the keys for a subset of processes to run over
    -p,            --parallel              enables running in parallel (default is single core use)
    -n NWORKERS,   --nWorkers NWORKERS     specifies the number of workers if multi core usage is desired (default is 4)
    -c CONFIGFILE, --configfile CONFIGFILE specifies the config file to be read (default is Configurations/Configuration.py)

## Plot the results

Results for the WW and WZ analyses may now be plotted using the relevant plotting configuration file. 

    python PlotResults.py Configurations/PlotConf_TTbarAnalysis.py

The resulting plots are put into the Output folder.

    ls Output/
    
This will list the pdf files containing your plots.    

To display a plot use evince, for example

    evince Output/lep_pt
    
    
![](Output/lepPT.png)

## The Analyses

The available analyses are:
  * TTbarAnalysis
  * WAnalysis
  * WZAnalysis
  * ZAnalysis
  * ZZAnalysis
  * ZPrimeAnalysis

The files can be found in the Analysis folder

    ls Analysis

If, as we suggested, you are using the small Virtual Machine, you only have 10% of the data.  You do not have access to all the data for all the analyses.  For the moment you can take a look at WW and WZ.  For the other analyses you need to download the rest of the data (which just takes time) and move it into your Input directory.

