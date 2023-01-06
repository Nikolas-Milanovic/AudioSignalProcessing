# The Problem

Audio signals can contain sounds from many sources. For example a microphone next to a railway can pick up a bird chirping and also a train whistle. But what if we wanted to seperate/filter these sounds bites from eachother, how could this possibly be done?

# AudioSignalProcessing

This Python program will take a specified inputed audio file containing a bird chirping and a train whistle. The audio file can be visualized by the time-domain plot below (signal array y and sampling rate Fs on the x-axis). It would be rather difficult to separate the bird chirps from the train whistlle directly from this mixed single, as they heavily overlap in time.

 <img width="426" alt="image" src="https://user-images.githubusercontent.com/59632554/211058513-bfd0e38f-2579-4e4e-8715-f1739532b7f3.png">

# Implementaion: 

This is rather pretty simple:
1) Obtain the Discrete Fourier Tranform of the audio (i.e. DFT(audio data))
2) Since the input data is real (i.e. does not include imaginary numbers) we can exploit that fact that the FFT will have (conjugate) symmetry, as seen below:

![image](https://user-images.githubusercontent.com/59632554/211059611-330a0262-c921-4d3a-8592-4e5dca574481.png)

3) Now with some trial and error we can isolate the Frequencies that correspond to the respective train whistle and bird chirping 
4) And in doing so, we compute the Inverse Fast Fourier Tranform to get the resulting filtered sound bites

# Results


The figure shows the DFT Frequencies that comprise of the Train Whistle.

![image](https://user-images.githubusercontent.com/59632554/211060029-13e7edd3-3017-4539-bef8-bb62b891246e.png)

The figure shows the DFT Frequencies that comprise of the Bird Chirping.

![image](https://user-images.githubusercontent.com/59632554/211060051-4da151da-e891-4600-930d-6eb0d5f0e8fa.png)

We can then perform an Inverse Discrete Fourier Tranform (IDFT) on these two data sets to get the respective sound bites for the train whistle and bird chirping.
