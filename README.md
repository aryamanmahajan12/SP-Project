# Signal Processing - Project

# The problem statement consisted of three components:

- Echo creation for a given audio file,
- Removal of echo from a given audio file, 
- Identification and classification of the noises present in each audio file.


## For the first section: 
The solution was implemented using two different methods. Solution consisted of applying convolution of the given audio with itself, which produced both uniform and non-uniform delays with the echo.


## For the second section: 
We use LMS adaptive filtering which iteratively adjusts the filter coefficients by minimizing the difference between the output of the filter and the desired, echo-free audio sample.


## For the third section: 
We had 4 sample audio files which each contained the same background music, superimposed with a different noise. We extract the template noises from these sample files, and then cross correlate the input audio file with these noise templates. The noise template with which the highest correlation is obtained is essentially the kind of noise present in the input audio file.


The method for generating the template noises, which worked with the highest accuracy and lowest error rate is the method discussed below for generating template noises: 

- We obtain 4C2 = 6 combinations of the 4 input files. We know that the background music behind all the noise samples is the same. Also, the length of all 4 files is also known to be the same. Assuming the nature 
  of noise is purely additive in all the 4 given music samples, the subtraction of the data points of two of these 4 files cancels the music content and leaves behind only the noise content. Hence, we finally 
  generate 6 ‘only noise’ samples. Now, we obtain correlation of the input file with all 6 samples. We store the peak values of each correlation vector in an array. The three highest values in the vector have a 
  certain noise component in common, which is thus concluded as the kind of noise present in the input file.
