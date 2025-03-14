# CMS Phase-2 Muon HLT

## Running L3 Muon reco (OI + IO) in CMSSW_14_0_9

### Setup
```shell
cmsrel CMSSW_14_0_9
cd CMSSW_14_0_9/src
cmsenv

git cms-init
git cms-addpkg RecoMuon/TrackerSeedGenerator
git cms-addpkg HLTrigger/HLTfilters
git cms-addpkg HLTrigger/Configuration/

git clone https://github.com/aman0404/CMSPhase2MuonHLT.git HLTrigger/PhaseII/python/Muon

cp -r HLTrigger/PhaseII/python/Muon/Analyzers HLTrigger/
cp -r HLTrigger/PhaseII/python/Muon/TSG/* RecoMuon/TrackerSeedGenerator/plugins/

scram b -j 10
```

### Configs
Located under `HLTrigger/PhaseII/python/Muon/example_cfgs/`. 

The configs contain full Phase2 HLT setup, but you can choose
whether to create OI seeds from L2 muons or L1TkMuons (skip L2).

VectorHits are enabled for both tracking and seeding in setups with suffix `_VectorHits`.

```shell
# Configs
HLT_Phase2_OIFromL2.py
HLT_Phase2_OIFromL2_VectorHits.py
HLT_Phase2_OIFromL1TkMu.py
HLT_Phase2_OIFromL1TkMu_VectorHits.py
```


