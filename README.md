# CrosstalkReco
Crosstalk Reconstruction Code

This is the 1.0v of the LAPPD crosstalk reconstruction algorithm for the ANNIE collaboration. As of now, a few things need to be specified and input for this algorithm to work.

Firstly, you'll need an s-parameter file as obtained from the Ansys HFSS simulations in the form of a .sNp file. The S-parameters in these files need to be in the form of alternating sides of the LAPPD, i.e 1_0, 1_1, 2_0, 2_1... where the first digit is the microstrip and the second digit is the side of the LAPPD.

Second, you'll need LAPPD event files. As of now, the algorithm works on the .txt files output by ToolAnalysis- one for each side of the LAPPD. Each event is 30 lines in each file (the script ignores the first line of the files, which is irrelevant here, as well as the first 3 columns of each file as they are irrelevant here as well), but the last 2 correspond to the trigger signal which is ignoreable. So, each event spans 28 lines corresponding to the 28 non-HV strips. 0-28 is one event, 30-58 the next etc.

Lastly, the microstrips on which the signals are incident need to be specified. In typical LAPPD pulses, there is a primarily-excited strip with the highest voltage, as well as the two neighboring strips which experience some charge sharing. So, each time the script is run, it runs over 3 microstrips on which the signal was observed.
