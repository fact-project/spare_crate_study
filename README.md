# spare_crate_study

repo where I wanna keep track of my study of the performance of the FACT spare crate in Zurich.
The PC connected to the hardware is `fact03`, where you can login with the old fact default password.

The test data, I take will be in `/loc_data/raw/yyyy/mm/dd` and I'll try to keep track of the runs, I took here.
I might delete runs, which turn out to be useless, the disk is not endless.

------

2017.11.03 

No FPAs connected.
internat trigger setting: 20 [unit?]

FAD labels:
0. 06-24001-e1-0043
1. 06-24001-e1-0068
2. 06-24001-e1-0063
3. 06-24001-e1-0035
4. 06-24001-e1-0008
5. 06-24001-e1-0048
6. 06-24001-e1-0026
7. 06-24001-e1-0028
8. 06-24001-e1-0014
9. 06-24001-e1-0015

cold-ish:

20171103_001: drs pedestal, 1000 events, 10 boards
20171103_002: drs gain, 1000 events, 10 boards
20171103_003: drs pedestal, 1000 events, 10 boards

warm-ish:

20171103_004: drs pedestal, 1000 events, 10 boards
20171103_005: drs gain, 1000 events, 10 boards
20171103_006: drs pedestal, 1000 events, 10 boards

there is some chaos with the runs. this is the "dim" script I used to take the runs:
```
.w 1000
FAD_CONTROL/START_DRS_CALIBRATION
.w 500

FAD_CONTROL/CONFIGURE 0 1000 drs-pedestal
.w 2000
FAD_CONTROL/RESET_CONFIGURE
.w 500
FAD_CONTROL/ENABLE_CONTINOUS_TRIGGER yes
.w 55000


FAD_CONTROL/CONFIGURE 0 1000 drs-gain
.w 2000
FAD_CONTROL/RESET_CONFIGURE
.w 500
FAD_CONTROL/ENABLE_CONTINOUS_TRIGGER yes
.w 55000


FAD_CONTROL/CONFIGURE 0 1000 drs-pedestal
.w 2000
FAD_CONTROL/RESET_CONFIGURE
.w 500
FAD_CONTROL/ENABLE_CONTINOUS_TRIGGER yes
.w 55000

FAD_CONTROL/CONFIGURE 0 1000 drs-pedestal
.w 2000
FAD_CONTROL/RESET_CONFIGURE
.w 500
FAD_CONTROL/ENABLE_CONTINOUS_TRIGGER yes
.w 55000


FAD_CONTROL/SET_FILE_FORMAT 6
.>CALIBRATION DONE
```

There are now runs 1...7 so 7 runs not 6. I think in one of the runs the connection broke down. So its better to use the run headers ti
to find out what the DAC settings and roi settings were. Clear is only: it was no FPA attached and the internal trigger was used.


-----


20171106

Take 3 runs drs calib as usual.

Then 10 runs with dac values from 0 .. 50000 in steps of 5000




