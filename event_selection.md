# Event selection

The events in the ntuple are selected from all events where:

* A single electron or muon trigger has fired;
* The primary vertex has at least 5 tracks;
* There is at least one good lepton with pT > 25 GeV;
* The event passes the Good Run List;
* A veto exists on events containing bad jets.

In all of these analyses a standard selection on physics objects is applied:

**table here**

## W Analysis

This analysis implements the criteria for single W boson events with the W boson decaying to leptons. 

The standard object selection criteria are applied.  In addition, the analysis specific event selection criteria are:

* Exactly one good lepton with pT > 25 GeV; 
* Missing ET > 30 GeV;
* Reconstructed mass W > 30 GeV.


## Z Analysis

This is a Z boson analysis where the Z boson decays into a lepton pair. 

The analysis specific event selection criteria are:

* Exactly two good leptons with pT > 25 GeV; 
* Leptons have opposite charge;
* Leptons have same flavour; 
* |mass lepton pair - mass Z | < 20 GeV.


## Top pair Analysis
This analysis focuses on top pair selection in the semileptonic channel.

Top pair analysis is interesting since it is a good test of the Standard Model (SM).
It is important for discrimination between different data simulation generators,  QCD models and parton distribution functions.
In addition, top pair production is an important background in various Higgs boson analyses as well as beyond the SM searches,
and it is therefore crucial to understand this process in detail. 


The analysis specific event selection criteria are:

* Exactly one good lepton with pT > 25 GeV; 
* At least four good jets;
* At least two b-tagged jets (MV1@70%);
* Missing ET > 30 GeV;
* Reconstructed mass W > 30 GeV.

## WZ Analysis

This analysis looks for both a W boson candidate and Z boson candidate.
It is a relatively clean signature due to 3 leptons in the final state.  It is interesting for physics since it is a probe for triple gauge couplings.

The analysis specific event selection criteria are:

* Exactly three good leptons with pT > 25 GeV;
* WZ candidate is chosen by finding the Z boson candidate closest to the nominal Z mass;
* |mass lepton pair -  mass Z | < 10 GeV;
* Reconstructed mass W > 30 GeV.
* 
## ZZ Analysis

This analysis looks for two Z boson candidates where both Z bosons decay to leptons.  

The analysis specific event selection criteria are:

* Exactly four good lepton with pT > 10 GeV;
* Two Z candidates built from leptons pairs of same flavour and opposite charge minimizing the total deviation of both candidates from the Z boson mass;
* |mass Z candidate 1 - mass Z| + |mass Z candidate 2 - mass Z| < 20 GeV.

## HWW Analysis

This analysis implements the criteria for zero jet bin of single W boson events with the W boson decaying to leptons.

This analysis searches for the standard model Higgs boson produced via the vector-boson fusion mechanism. 
The main background is top pair production in association with one or more jets. 

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
* Missing ET > 20 GeV; T
* pT lepton pair > 30 GeV;
* Angular separation between lepton pair and Missing ET > pi/2; ?
* Reconstructed mass W > 30 GeV;
* Mass lepton pair < 55 GeV;
* Angular separation between leading lepton and trailing lepton < 1.8.  ?

## Z' Analysis

The analysis specific event selection criteria are:

* Exactly one good lepton with pT > 25 GeV;
* At least four good jets;
* At least one b-tagged jet (MV1@70%); 
* Missing ET > 30 GeV;
* Mass W + Missing ET > 60 GeV.