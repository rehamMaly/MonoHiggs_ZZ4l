# MonoHiggs_ZZ4l package for 2017 data

cmsrel CMSSW_9_4_9_cand2
cd CMSSW_9_4_9_cand2/src
cmsenv

//For electron Identification 

 git cms-merge-topic guitargeek:ElectronID_MVA2017_V2_HZZ_940pre3
 git clone -b ElectronID_MVA2017_V2 https://github.com/guitargeek/RecoEgamma-ElectronIdentification RecoEgamma/ElectronIdentification/data/
 rm -rf RecoEgamma/ElectronIdentification/data
git clone -b ElectronID_MVA2017_V2 https://github.com/guitargeek/RecoEgamma-ElectronIdentification RecoEgamma/ElectronIdentification/data/

//For electron energy scale and smear 

git cms-merge-topic cms-egamma:EgammaPostRecoTools_940

//Extra step for 
less RecoEgamma/EgammaTools/python/EgammaPostRecoTools.py 
remove   'RecoEgamma.ElectronIdentification.Identification.cutBasedElectronID_Fall17_94X_V2_cff' 
from 
_fall17V2EleIDModules = [
    'RecoEgamma.ElectronIdentification.Identification.cutBasedElectronID_Fall17_94X_V2_cff',
    'RecoEgamma.ElectronIdentification.Identification.mvaElectronID_Fall17_noIso_V2_cff',
    'RecoEgamma.ElectronIdentification.Identification.mvaElectronID_Fall17_iso_V2_cff'
    ]
    
// For ZZ matrix 

git clone https://github.com/cms-analysis/HiggsAnalysis-ZZMatrixElement.git ZZMatrixElement
cd ZZMatrixElement
git checkout -b from-v216 v2.1.6
. setup.sh -j 12

// For Muon PT correction This is not used in 2017 but we keep if we need later 
git clone -o Analysis https://github.com/bachtis/analysis.git -b KaMuCa_V4 KaMuCa

// For muon Rochester correction 
download  
https://twiki.cern.ch/twiki/pub/CMS/RochcorMuon/roccor.Run2.v2.tgz

// For HiggsAnalysis 


scramv1 b -j 8 


