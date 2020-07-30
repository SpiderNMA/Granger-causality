# Granger-causality
..............................................................................................................................Hassan (Finding the counts of regions)
 groupings of brain regions

regions = ["vis ctx", "thal", "hipp", "other ctx", "midbrain", "basal ganglia", "cortical subplate", "other"]
brain_groups = [["VISa", "VISam", "VISl", "VISp", "VISpm", "VISrl"], # visual cortex
                ["CL", "LD", "LGd", "LH", "LP", "MD", "MG", "PO", "POL", "PT", "RT", "SPF", "TH", "VAL", "VPL", "VPM"], # thalamus
                ["CA", "CA1", "CA2", "CA3", "DG", "SUB", "POST"], # hippocampal
                ["ACA", "AUD", "COA", "DP", "ILA", "MOp", "MOs", "OLF", "ORB", "ORBm", "PIR", "PL", "SSp", "SSs", "RSP"," TT"], # non-visual cortex
                ["APN", "IC", "MB", "MRN", "NB", "PAG", "RN", "SCs", "SCm", "SCig", "SCsg", "ZI"], # midbrain
                ["ACB", "CP", "GPe", "LS", "LSc", "LSr", "MS", "OT", "SNr", "SI"], # basal ganglia 
                ["BLA", "BMA", "EP", "EPd", "MEA"] # cortical subplate
                ]
for i in range(38):
  dat = alldat[i]
  Areas, Count = np.unique((dat['brain_area']), return_counts=True)

  nareas = 7 # only the top 7 regions are in this particular mouse
  NN = len(dat['brain_area']) # number of neurons
  barea = nareas * np.ones(NN, ) # last one is "other"
  for j in range(nareas):
   barea[np.isin(dat['brain_area'], brain_groups[j])] = j # assign a number to each region
  
# dict.items(dat['brain_area']))
# print(barea)

# for i in range(3):
#   dat = alldat[i]
  print("session: ", i)
  print("Brain areas : " , Areas)
  print("Occurrence Count : ", Count)
 

  region, Counts = np.unique((barea), return_counts=True)
  print("regions : " , region,)
  print("Occurrence Count : ", Counts)
  print('\n')
.........................................................................................................
