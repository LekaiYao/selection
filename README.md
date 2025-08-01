```
1.How to create analysis.C and analysis.h by MakeClass():
  root -l /PATH/to/RootFiles/xxx.root   #root -l /lstore/cms/henrique/Bmeson/MC_DATA/MC_ppRef_Bmeson/Bu_phat5_Bfinder.root
    [0].ls
    [1]Bfinder->cd()
    [2]ntKp->MakeClass("analysis")
Then analysis.C and analysis.h are created automatically. You can change the name in MakeClass("name") and it would produce name.C and name.h

2.Make specific changes to analysis.C:
(1)define the variables for output
  line37:  Float_t B_mass;
  line108: tree->Branch("B_mass", &B_mass, "B_mass/F");
  line216: B_mass = Bmass[i_B];
(2)set selection cuts 
  From line190 to line 213

3.How to run analysis.C:
  root -l analysis.C
    root> analysis t
    root> t.Loop()

4.How to add more cut on a TTree without changes on its structure:
  modify the input file and "Apply B_mass window cut" part in new_select.C, then
  root -l new_select.C
  (This code could also delete the nan/inf events.)



The codes here:
  To run selection codes for data,
  root -l ana.C
    root> ana t
    root> t.Loop()

  To run selection codes for MC,
  root -l analysis.C
    root> analysis t
    root> t.Loop()
```
