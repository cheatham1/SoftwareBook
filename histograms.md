# Histograms

After running the analysis you will have lots of histograms in your output directory.  Let's take a look.

<img src="./Output/pvxp_n.jpg" width="200" />
<img src="./Output/vxp_z.jpg" width="200" />

Here we can see the number of vertices in this top pair analysis (TTbarAnalysis)  ranges from around 0 to 25.
The data and simulated data have a similar shape.  However there is a slight offset due to ... 

The primary vertex position in the coordinate z (where the z axis follows the beam direction and positive z points towards Geneva) is centered around zero.  This is expected since the origin of the coordinate system is the nominal interaction point.

<img src="./Output/n_jets.jpg" width="200" />
<img src="./Output/jet_eta.jpg" width="200" />
<img src="./Output/jet_pt.jpg" width="200" />


We also see that the number of jets  varies from 4 to 9.  Simulated data shows a similar distribution of numbers of jets.
The jet [pseudorapidity](https://en.wikipedia.org/wiki/Pseudorapidity) distribution is symmetrical, which is expected since the ATLAS detector itself is symmetrical in pseudrapidity.
The jet transverse momentum (pT) distribution has a maximum between 30 and 40 GeV. The simulated data slightly over-estimates the data jet pT distribution.

<img src="./Output/lep_type.jpg" width="200" />
<img src="./Output/lep_n.jpg" width="200" />
<img src="./Output/lep_pt.jpg" width="200" />
<img src="./Output/lep_eta.jpg" width="200" />

Looking at lepton Particle Data Group ([PDG](http://pdg.lbl.gov)) we see peaks at 11 and 13.  These correspond to electrons and muons according to the official [numbering scheme](http://pdg.lbl.gov/2015/reviews/rpp2015-rev-monte-carlo-numbering.pdf).  
This TTbarAnalysis requires 'exactly one good lepton with pT > 25 GeV' (see chapter 'Event Selection').  Indeed this agrees with the distributions seen in Number of Leptons and Lepton Transverse Momentum.
The Lepton Pseudorapidity distribution is symmetrical, with data and simulated data in agreement.

<img src="./Output/etmiss.jpg" width="200" />
<img src="./Output/WtMass.jpg" width="200" />

Missing transverse momentum is defined as the event momentum
imbalance in the plane transverse to the beam axis, where momentum conservation is expected.
Such an imbalance may signal the presence of undetectable particles, such as neutrinos or new
stable, weakly-interacting particles.

The average W mass based on [published results](http://pdg.lbl.gov/2012/listings/rpp2012-list-w-boson.pdf) is 80.385 ± 0.015 GeV
