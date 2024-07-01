NOTE: This is not the current code being used for this project--this is the code that resulted after my and my interns' work on the project over summer 2022 and summer 2023. I then moved on to another project and this project was picked up by a different student. For the most up-to-date version of the code, please contact Raja GuhaThakurta at raja@ucolick.org. 

This contains the code written and debugged with the help of two groups of UCSC SIP interns over summer 2022 and summer 2023, as well as all relevant files that  the code references. This was a collaborative effort and would have been impossible without the help of my SIP interns: Ishaan Agrawal, Riya Shah, Jessamine Qu (for summer 2022) and Theodore Cohen, Samik Garg, Andrew Liu (for summer 2023), my advisor Raja GuhaThakurta, and my summer 2022 co-mentor Kyle Nguyen. 

The goal of the code in the "Trial_19.ipnb" file is to generate a series of mock light curves from quasar data (CFHTLS) to understand the amount of quasar contamination in our identified RR Lyrae (NGVS) by testing how often the RR Lyrae identification algorithm mistakes these mock light curves for RR Lyrae. These mock light curves are generated by selecting the closest time match between the RR Lyrae times and the interpolated quasar times in each epoch (to mimic the cadence of the NGVS survey used to observe the identified RR Lyrae), pulling the corresponding quasar magnitudes, and adding in noise--essentially creating what NGVS would have seen if it had observed that quasar. The code iterates through a series of quasars and RR Lyrae, and shifts the RR Lyrae in time to capture all possible variations over the full quasar observing run, producing an output of ~10,000 mock light curves. See the comments in the code for more detail.

The .csv and .zip files contained in this project are all necesary for the code to run. For a summary, see below:
1. "TargetData.csv": A .csv file containing the RR Lyrae data from the NGVS dataset, to be iterated through and referenced when creating the mock light curves. The file is structured with 10 columns: the RR Lyrae's NGVS catalog ID, the band (ugiz) of the corresponding datapoint, the date and time the datapoint was taken, the exposure length, the frame, the image index, the zeropoint, the magnitude of the datapoint, the systematic error of the datapoint, and the time, using MJD, of the datapoint.
2. "Quasars.csv": A .csv file containing the names and locations (D1-4) of the most recognizable quasars in the CFHTLS dataset, to be iterated through when creating the mock light curves. These quasars were chosen by visual vetting by myself and the 2022 SIP interns. 
3. "u_err.csv": A .csv file containing the error in the u band (ultraviolet) for the quasar data; this is interpolated to add noise to the generated mock light curves. The file is structured with two coloumns: the magnitude and the corresponding error. 
4. "g_err.csv": A .csv file containing the error in the g band (visible) for the quasar data; this is interpolated to add noise to the generated mock light curves. The file is structured as in "u_err.csv".
5. "i_err.csv": A .csv file containing the error in the i band (near infrared) for the quasar data; this is interpolated to add noise to the generated mock light curves. The file is structured as in "u_err.csv".
6. "z_err.csv": A .csv file containing the error in the z band (near infrared) for the quasar data; this is interpolated to add noise to the generated mock light curves. The file is structured as in "u_err.csv".
7. "D1.zip": A .zip file containing a folder of all the quasar datasets in the D1 (Deep field 1 at ~ 02hr/-04deg in RA/DEC) region, in .csv format. Each file is named with the quasar's CFHTLS ID, and is structured with 4 columns: the time using MJD, the magnitude, the error, and the filter (ugriz) of the datapoint. The first row is irrelevant, and therefore skipped in the code. These were iterated through to generate the mock light curves. 
8. "D2.zip": A .zip file containing a folder of all the quasar datasets in the D2 (Deep field 2 at ~ 10hr/+02deg in RA/DEC) region, in the same format as "D1.zip".
9. "D3.zip": A .zip file containing a folder of all the quasar datasets in the D3 (Deep field 3 at ~ 14hr/+52deg in RA/DEC) region, in the same format as "D1.zip".
10. "D4.zip": A .zip file containing a folder of all the quasar datasets in the D4 (Deep field 4 at ~ 22hr/-17deg in RA/DEC) region, in the same format as "D1.zip".

In addition to these files, the output files of the code will be written to folders labeled "dee1", "dee2", "dee3", "dee4", so if you want to run the code, please make sure that these files have been created in the same location as the code.
