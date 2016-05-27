# Variable names

If you get so far as looking at the datasets using ROOT, here are the definitions of the variables.

|branchname                 | type   | description |
|-|-|-|
|runNumber                  | int    | run identifier |
|eventNumber                | int    | event identifier |
|channelNumber              | int    | channel identifier |
|mcWeight                   | float  | weight of a simulated event |
|pvxp\_n                    | int    | number of primary vertices |
|vxp\_z                     | float  | z-position of the primary vertex |
|trigE                      | bool   | boolean whether a standard trigger has fired in the egamma stream |
|trigM                      | bool   | boolean whether a standard trigger has fired in the muon stream |
|passGRL                    | bool   | signifies whether event passes the Good Run List may be put in isGoodEvent |
|hasGoodVertex              | bool   | signifies whether the event has at least one good vertex where Ntracks > 4 |
|lep\_n                     | int    | number of preselected leptons |
|lep\_truthMatched          | vector<.bool>  | boolean indicating whether the lepton is matched to a simulated lepton |
|lep\_trigMatched           | vector<.bool>  | boolean signifying whether the lepton is the one triggering the event |
|lep\_pt                    | vector<.float>  | transverse momentum of the lepton |
|lep\_eta                   | vector<.float>  | pseudorapidity of the lepton |
|lep\_phi                   | vector<.float>  | azimuthal angle of the lepton |
|lep\_E                     | vector<.float>  | energy of the lepton |
|lep\_z0                    | vector<.float>  | z-coordinate of the track associated to the lepton wrt. the primary vertex |
|lep\_charge                | vector<.float>  | charge of the lepton |
|lep\_flag                  | vector<.int>    | bitmask implementing object cuts of the top group |
|lep\_type                  | vector<.int>    | number signifying the lepton type (e, mu, tau) of the lepton |
|lep\_ptcone30              | vector<.float>  | ptcone30 isolation for the lepton |
|lep\_etcone20              | vector<.float>  | etcone20 isolation for the lepton |
|lep\_trackd0pvunbiased     | vector<.float>  | d0 of the track associated to the lepton at the point of closest approach (p.o.a.) |
|lep\_tracksigd0pvunbiased  | vector<.float>  | d0 signifcance of the track associated to the lepton at the p.o.a. |
|met\_et                    | float  | Transverse energy of the missing momentum vector |
|met\_phi                   | float  | Azimuthal angle of the missing momentum vector |
|jet\_n                     | int    | number of selected jets |
|jet\_pt                    | vector<.float>  | transverse momentum of the jet |
|jet\_eta                   | vector<.float>  | pseudorapidity of the jet |
|jet\_phi                   | vector<.float>  | azimuthal angle of the jet |
|jet\_E                     | vector<.float>  | energy of the jet |
|jet\_m                     | vector<.float>  | invariant mass of the jet |
|jet\_jvf                   | vector<.float>  | jet vertex fraction of the jet |
|jet\_flag                  | vector<.int>    | bitmask implementing object cuts of the top group |
|jet\_trueflav              | vector<.int>    | flavor of the simulated jet |
|jet\_truthMatched          | vector<.int>    | information whether the jet matches a simulated jet|
|jet\_SV0                   | vector<.float>  | Weight from algorithm that reconstructs Secondary Vertices associated with a jet |
|jet\_MV1                   | vector<.float>  | Weight from algorithm based on Multi-Variate technique |
|scaleFactor\_BTAG          | float              | scalefactor for btagging |
|scaleFactor\_ELE           | float              | scalefactor for electron efficiency |
|scaleFactor\_JVFSF         | float              | scalefactor for jet vertex fraction |
|scaleFactor\_MUON          | float              | scalefactor for muon efficiency |
|scaleFactor\_PILEUP        | float              | scalefactor for pileup reweighting |
|scaleFactor\_TRIGGER       | float              | scalefactor for trigger |
|scaleFactor\_ZVERTEX       | float              | scalefactor for z-vertex reweighting |