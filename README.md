# Bayesian Calculation Program Guide for COMBMORC 2021
## I. Installing the required packages
You can get the R interpreter from here: https://cran.r-project.org/

You also should install the R Studio IDE: https://www.rstudio.com/

Before you can run the software, you must install these packages in R:
*mvtnorm
*shiny
*rgdal
*sp
*raster
*RColorBrewer

Use command
```R 
install.packages("mvtnorm")
```
to install the packages. You may need to download additional libraries to be able to compile some parts of the packages. There is plenty of information on the internet for every kind of operating system.

## II. Running the software:

You will need to open the app.R file:
![image](https://user-images.githubusercontent.com/30175279/139648977-22e938e1-c402-40cc-8265-8310dac1eee3.png)


The app.R file will open in the document viewer of the Rstudio. To run the app you need to press the “Run App” button:
![image](https://user-images.githubusercontent.com/30175279/139648998-0d609365-8347-4145-8803-ba6a0ce32753.png)

A new window should pop up:
![image](https://user-images.githubusercontent.com/30175279/139649032-8c2e454c-a92f-47ca-8245-8ca25c8f6823.png)


This is the main window of the calculation program. You will use the window to upload the files, change the parameters and run the Bayesian calculations. The program is divided in to three separate sections: (i) Data input, (ii) Data generation and (iii) Reconstruction. Each section has representative input tabs on the gray portion of the screen on the left, and output tabs, on the white portion of the screen on the right.

## III. Uploading data
To upload the data, choose the file type you will use, either CSV or NBL. Then, upload files accordingly. After the required files are uploaded, press the big “Process” button to store the data in the memory.
You can use the data selection slider to select the data range, which will be used in Bayesian calculations. The selected range will automatically be used. There are no buttons to confirm the selected range (you can leave the setting and go to different tab).

## IV. Data generation
There is a possibility to generate mobile gamma spectrometry data using the Generate tab:
![image](https://user-images.githubusercontent.com/30175279/139649066-3be78a69-af07-45b1-96be-5c5f2da37c11.png)


you need to input the position of the source, activity, background count rate, starting position of the survey, speed, acquisition time, and number of measurement points. The direction of the virtual detector is along the x axis. Here is a small image representative of the coordinate system used:
![image](https://user-images.githubusercontent.com/30175279/139649079-29a57545-11bf-4043-9b90-9b5f089b6abe.png)


The efficiency of the detector set here is used only for data generation. Also, not that the efficiency is used only to evaluate the count-rate from the source. The background count-rate is given separately. In reality, if the efficiency is increased twice, the background count-rate would also increase twice. To obtain data for the same situation but different efficiency, the background count-rate has to be adjusted manually accordingly.

## V. Bayesian calculations
The reconstruction tab allows to run the Bayesian reconstruction using MCMC algorithm. The settings regarding the in the Reconstruction tab:
![image](https://user-images.githubusercontent.com/30175279/139649095-90995da0-bfd3-4f17-9ade-38349ec8095b.png)


The efficiency value used here will be used in the Bayesian estimation only. Input the efficiency value of your detectors here.
IMPORTANT: BEFORE RUNNING THE RECONSTRUCTION MAKE SURE THAT THE USE DATA RADIO BUTTON IS IN THE CORRECT SETTING.
If it is set to uploaded data, and there is no data uploaded, the program will crash. Likewise for the generated data. Make sure that there is data before running the calculations

You also have the possibility to change the initial value of the MCMC chain. To do that, change the initial parameter radio button to “specified” and change the parameters.

Change the number of MCMC iterations used by altering the value of the appropriate field.

You can change the burnin value yourself. Burnin denotes the number of discarded first samples, which are not representative of the target posterior distribution. After changing the parameter, you need to press the redraw button.

Here are a few posterior distribution plots that you will get after successful run:
![image](https://user-images.githubusercontent.com/30175279/139649127-cfe8de6e-301b-4878-ab5b-31ed7df6ca92.png)
![image](https://user-images.githubusercontent.com/30175279/139649133-4546e56f-2356-4f92-a3fd-7789cca16e31.png)


The graphs are probability distributions. So in the graph on the left (position posterior) the darker the shade of the color, the higher the probability for the source being there. Similarly, for the posterior distribution of source activity, the higher the probability density of a given activity value, the higher the probability that the source is of that activity.

As a checkup, the fit of the data is displayed below the posterior distributions. It displays the projected mean count-rate given the estimated parameters of the source position, activity and background.
![image](https://user-images.githubusercontent.com/30175279/139649146-70d59bad-9860-4089-a451-98eceb364ef0.png)




## VI. After a crash
If for some reason the program crashes, make sure that the R session is ready first, before running the app again.
![image](https://user-images.githubusercontent.com/30175279/139649151-eb8afb0e-0d1a-4d69-9038-dd2fc6e4014f.png)


This image above corresponds to a busy R session, which is not actively listening for new commands, with the red stop sign available on the top-right part of the console window in the R studio screen. It is possible to terminate the R session in case it is stuck for example by pressing the red stop sign. 
Then, when you see the “>” symbol available in the console, the R session is ready and listening for new inputs.
![image](https://user-images.githubusercontent.com/30175279/139649161-b68dc153-85a5-4a99-887a-f224d9b96088.png)

Then, the app can be safely restarted using the “Run App” button.
