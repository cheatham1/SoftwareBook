# Event selection

An important aspect of these samples is that they were prepared specifically for educational purposes. To this end, precision has been traded for simplicity of use. The introduced simplifications are:

* No facilities to estimate systematic uncertainties have been included as these quickly introduce large complexities. 

* The b-tagging scale factor is computed for a specific working point (MV1@70% efficiency). The
user, however, is free to specify the b-tagging weight used for tagging jets allowing for a potential
mismatch of the definition considered in the scale factor calculation and the one being actually applied.


* No QCD simulated samples were prepared as they would have been insufficient in statistics while introducing large set of additional samples. 


* The description of the W boson properties in simulated
W+jets events is not ideal. 
Corrections are only available
for samples produced with the Monte Carlo generator Alpgen
but not for those produced with
Sherpa generator.  However, using
Alpgen would have introduced a prohibitively large number of samples.  Sherpa was therefore used.


* The missing transverse momentum was calculated using the object preselection.
A recalculation of the missing transverse momentum is not implemented into the tools provided
for simplicity reasons. Therefore, changes in the object selection are not reflected in the missing
transverse momentum leading to potential mis-modeling of variables relying on it.

* The simulated data takes into account the pile-up and vertex position profile of the whole 2012
data taking, although the measured data is taken from a small list of runs from period D. This
introduces a certain mismatch regarding the number of vertices and the primary vertex position.




The events in the ntuple are selected from all events where:

* A single electron or muon trigger has fired;
* The primary vertex has at least 5 tracks;
* There is at least one good lepton with pT > 25 GeV;
* The event passes the Good Run List;
* A veto exists on events containing bad jets.

In all of these analyses a standard selection on physics objects is applied:

| electrons and muons            | jets |
| --                             | --   |
|pT > 25 GeV                     |  pt > 25 GeV |  
|Isolation: ptcone30 < 0.15 & etcone20 < 0.15      |  Jet Vertex Fraction cut|


## W Analysis

This analysis searches W bosons decaying to leptons. 

The analysis specific event selection criteria are:

* Exactly one good lepton with pT > 25 GeV; 
* Missing ET > 30 GeV;
* Reconstructed transverse mass W > 30 GeV.


## Z Analysis

This analysis seaches for Z bosons decaying into a lepton pair. 

The analysis specific event selection criteria are:

* Exactly two good leptons with pT > 25 GeV; 
* Leptons have opposite charge;
* Leptons have same flavour; 
* |mass lepton pair - mass Z | < 20 GeV.


## Top pair Analysis

This analysis searches for a top quark and an antitop quark.

The analysis specific event selection criteria are:

* Exactly one good lepton with pT > 25 GeV; 
* At least four good jets;
* At least two b-tagged jets (MV1@70%);
* Missing ET > 30 GeV;
* Reconstructed transverse mass W > 30 GeV.

## WZ Analysis

This analysis looks for both a W boson candidate and Z boson candidate.

It is a relatively clean signature due to 3 leptons in the final state.  It is interesting for physics since it is a probe for triple gauge couplings.

The analysis specific event selection criteria are:

* Exactly three good leptons with pT > 25 GeV;
* WZ candidate is chosen by finding the Z boson candidate closest to the nominal Z mass;
* |mass lepton pair -  mass Z | < 10 GeV;
* Reconstructed transverse mass W > 30 GeV.


## ZZ Analysis

This analysis looks for two Z boson candidates where both Z bosons decay to leptons.  

The analysis specific event selection criteria are:

* Exactly four good lepton with pT > 10 GeV;
* Two Z candidates built from leptons pairs of same flavour and opposite charge minimizing the total deviation of both candidates from the Z boson mass;
* |mass Z candidate 1 - mass Z| + |mass Z candidate 2 - mass Z| < 20 GeV.

## HWW Analysis

This analysis searches for W bosons decaying to leptons, with no jets.

The analysis specific event selection criteria are:

* Exactly two good leptons with pT > 25 GeV;
* Leptons have opposite charge;
* No jets with pT > 25 GeV;
 
If leptons have same flavor:
* mass lepton pair > 12 GeV;
* |mass lepton pair - mass Z| > 15GeV;
* Missing ET > 40 GeV;
 
Else:
* mass dilepton pair > 10 GeV;
* Missing ET > 20 GeV;
* pT lepton pair > 30 GeV;
* Angular separation between lepton pair and Missing ET > pi/2;
* Reconstructed transverse mass W > 30 GeV;
* Mass lepton pair < 55 GeV;
* Angular separation between leptons < 1.8.

## Z' Analysis

This analysis searches for Z' in the semileptonic top pair channel.

The analysis specific event selection criteria are:

* Exactly one good lepton with pT > 25 GeV;
* At least four good jets;
* At least one b-tagged jet (MV1@70%); 
* Missing ET > 30 GeV;
* Reconstructed transverse mass W + Missing ET > 60 GeV.