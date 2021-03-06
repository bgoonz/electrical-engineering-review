# Intro 2 DSP

{% file src="../../.gitbook/assets/dsp\_book\_dspguide.zip" %}

{% file src="../../.gitbook/assets/andreas-intoniou-digital-signal-processing.9780071454247.31527.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch1.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch2.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch3.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch4 \(1\).pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch5.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch6 \(1\).pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch7.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch8.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch9.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch10.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch11.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch12.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch13.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch14.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch15.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch16.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch17.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch18.pdf" %}

{% file src="../../.gitbook/assets/dsp\_book\_ch19.pdf" %}

























































































### Table of contents

* * [1: The Breadth and Depth of DSP](http://www.dspguide.com/ch1.htm)
  * [2: Statistics, Probability and Noise](http://www.dspguide.com/ch2.htm)
  * [3: ADC and DAC](http://www.dspguide.com/ch3.htm)
    * [Quantization](http://www.dspguide.com/ch3/1.htm)
    * [The Sampling Theorem](http://www.dspguide.com/ch3/2.htm)
    * [Digital-to-Analog Conversion](http://www.dspguide.com/ch3/3.htm)
    * [Analog Filters for Data Conversion](http://www.dspguide.com/ch3/4.htm)
    * [Selecting The Antialias Filter](http://www.dspguide.com/ch3/5.htm)
    * [Multirate Data Conversion](http://www.dspguide.com/ch3/6.htm)
    * [Single Bit Data Conversion](http://www.dspguide.com/ch3/7.htm)
  * [4: DSP Software](http://www.dspguide.com/ch4.htm)
  * [5: Linear Systems](http://www.dspguide.com/ch5.htm)
  * [6: Convolution](http://www.dspguide.com/ch6.htm)
  * [7: Properties of Convolution](http://www.dspguide.com/ch7.htm)
  * [8: The Discrete Fourier Transform](http://www.dspguide.com/ch8.htm)
  * [9: Applications of the DFT](http://www.dspguide.com/ch9.htm)
  * [10: Fourier Transform Properties](http://www.dspguide.com/ch10.htm)
  * [11: Fourier Transform Pairs](http://www.dspguide.com/ch11.htm)
  * [12: The Fast Fourier Transform](http://www.dspguide.com/ch12.htm)
  * [13: Continuous Signal Processing](http://www.dspguide.com/ch13.htm)
  * [14: Introduction to Digital Filters](http://www.dspguide.com/ch14.htm)
  * [15: Moving Average Filters](http://www.dspguide.com/ch15.htm)
  * [16: Windowed-Sinc Filters](http://www.dspguide.com/ch16.htm)
  * [17: Custom Filters](http://www.dspguide.com/ch17.htm)
  * [18: FFT Convolution](http://www.dspguide.com/ch18.htm)
  * [19: Recursive Filters](http://www.dspguide.com/ch19.htm)
  * [20: Chebyshev Filters](http://www.dspguide.com/ch20.htm)
  * [21: Filter Comparison](http://www.dspguide.com/ch21.htm)
  * [22: Audio Processing](http://www.dspguide.com/ch22.htm)
  * [23: Image Formation & Display](http://www.dspguide.com/ch23.htm)
  * [24: Linear Image Processing](http://www.dspguide.com/ch24.htm)
  * [25: Special Imaging Techniques](http://www.dspguide.com/ch25.htm)
  * [26: Neural Networks \(and more!\)](http://www.dspguide.com/ch26.htm)
  * [27: Data Compression](http://www.dspguide.com/ch27.htm)
  * [28: Digital Signal Processors](http://www.dspguide.com/ch28.htm)
  * [29: Getting Started with DSPs](http://www.dspguide.com/ch29.htm)
  * [30: Complex Numbers](http://www.dspguide.com/ch30.htm)
  * [31: The Complex Fourier Transform](http://www.dspguide.com/ch31.htm)
  * [32: The Laplace Transform](http://www.dspguide.com/ch32.htm)
  * [33: The z-Transform](http://www.dspguide.com/ch33.htm)
  * [34: Explaining Benford's Law](http://www.dspguide.com/ch34.htm)

**Signal and Graph Terminology**

A signal is a description of how one parameter depends on another parameter. For example, the most common type of signal in analog electronics is a voltage that varies with time. Since both parameters can assume a continuous range of values, we will call this a continuous signal. In comparison, passing this signal through an analog-to-digital converter forces each of the two parameters to be quantized. For instance, imagine the conversion being done with 12 bits at a sampling rate of one kilohertz. The voltage is curtailed to 4096 possible binary levels, and the time is only defined at one millisecond increments. Signals formed from parameters that are quantized in this manner are said to be discrete signals or digitized signals. For the most part, continuous signals exist in nature, while discrete signals exist inside computers \(although you can find exceptions to both cases\). It is also possible to have signals where one parameter is continuous and the other is discrete. Since these mixed signals are quite uncommon, they do not have special names given to them, and the nature of the two parameters must be explicitly stated.

Figure 2-1 shows two discrete signals, such as might be acquired with a digital data acquisition system. The vertical axis may represent voltage, light intensity, sound pressure, or an infinite number of other parameters. Since we don't know what it represents in this particular case, we will give it the generic label: amplitude. This parameter is also called several other names: the y-axis, the dependent variable, the range, and the ordinate.

The horizontal axis represents the other parameter of the signal, going by such names as: the x-axis, the independent variable, the domain, and the abscissa. Time is the most common parameter to appear on the horizontal axis of acquired signals; however, other parameters are used in specific applications. For example, a geophysicist might acquire measurements of rock density at equally spaced distances along the surface of the earth. To keep things general, we will simply label the horizontal axis: sample number. If this were a continuous signal, another label would have to be used, such as: time, distance, x, etc.

The two parameters that form a signal are generally not interchangeable. The parameter on the y-axis \(the dependent variable\) is said to be a function of the parameter on the x-axis \(the independent variable\). In other words, the independent variable describes how or when each sample is taken, while the dependent variable is the actual measurement. Given a specific value on the x-axis, we can always find the corresponding value on the y-axis, but usually not the other way around.

Pay particular attention to the word: domain, a very widely used term in DSP. For instance, a signal that uses time as the independent variable \(i.e., the parameter on the horizontal axis\), is said to be in the time domain. Another common signal in DSP uses frequency as the independent variable, resulting in the term, frequency domain. Likewise, signals that use distance as the independent parameter are said to be in the spatial domain \(distance is a measure of space\). The type of parameter on the horizontal axis is the domain of the signal; it's that simple. What if the x-axis is labeled with something very generic, such as sample number? Authors commonly refer to these signals as being in the time domain. This is because sampling at equal intervals of time is the most common way of obtaining signals, and they don't have anything more specific to call it.

Although the signals in Fig. 2-1 are discrete, they are displayed in this figure as continuous lines. This is because there are too many samples to be distinguishable if they were displayed as individual markers. In graphs that portray shorter signals, say less than 100 samples, the individual markers are usually shown. Continuous lines may or may not be drawn to connect the markers, depending on how the author wants you to view the data. For instance, a continuous line could imply what is happening between samples, or simply be an aid to help the reader's eye follow a trend in noisy data. The point is, examine the labeling of the horizontal axis to find if you are working with a discrete or continuous signal. Don't rely on an illustrator's ability to draw dots.

The variable, N, is widely used in DSP to represent the total number of samples in a signal. For example, N = 512 for the signals in Fig. 2-1. To

![](http://www.dspguide.com/graphics/F_2_1.gif)

keep the data organized, each sample is assigned a sample number or index. These are the numbers that appear along the horizontal axis. Two notations for assigning sample numbers are commonly used. In the first notation, the sample indexes run from 1 to N \(e.g., 1 to 512\). In the second notation, the sample indexes run from 0 to N\`-\`1 \(e.g., 0 to 511\). Mathematicians often use the first method \(1 to N\), while those in DSP commonly uses the second \(0 to N\`-\`1\). In this book, we will use the second notation. Don't dismiss this as a trivial problem. It will confuse you sometime during your career. Look out for it!



Mean and Standard Deviation

The mean, indicated by ?? \(a lower case Greek mu\), is the statistician's jargon for the average value of a signal. It is found just as you would expect: add all of the samples together, and divide by N. It looks like this in mathematical form:

![](http://www.dspguide.com/graphics/E_2_1.gif)

In words, sum the values in the signal, xi, by letting the index, i, run from 0 to N-1. Then finish the calculation by dividing the sum by N. This is identical to the equation: ?? =\(x0 + x1 + x2 + ... + xN-1\)/N. If you are not already familiar with ?? \(upper case Greek sigma\) being used to indicate summation, study these equations carefully, and compare them with the computer program in Table 2-1. Summations of this type are abundant in DSP, and you need to understand this notation fully. In electronics, the mean is commonly called the DC \(direct current\) value. Likewise, AC \(alternating current\) refers to how the signal fluctuates around the mean value. If the signal is a simple repetitive waveform, such as a sine or square wave, its excursions can be described by its peak-to-peak amplitude. Unfortunately, most acquired signals do not show a well defined peak-to-peak value, but have a random nature, such as the signals in Fig. 2-1. A more generalized method must be used in these cases, called the standard deviation, denoted by ?? \(a lower case Greek sigma\).

As a starting point, the expression,\|xi-??\|, describes how far the ith sample deviates \(differs\) from the mean. The average deviation of a signal is found by summing the deviations of all the individual samples, and then dividing by the number of samples, N. Notice that we take the absolute value of each deviation before the summation; otherwise the positive and negative terms would average to zero. The average deviation provides a single number representing the typical distance that the samples are from the mean. While convenient and straightforward, the average deviation is almost never used in statistics. This is because it doesn't fit well with the physics of how signals operate. In most cases, the important parameter is not the deviation from the mean, but the power represented by the deviation from the mean. For example, when random noise signals combine in an electronic circuit, the resultant noise is equal to the combined power of the individual signals, not their combined amplitude.

The standard deviation is similar to the average deviation, except the averaging is done with power instead of amplitude. This is achieved by squaring each of the deviations before taking the average \(remember, power ??? voltage2\). To finish, the square root is taken to compensate for the initial squaring. In equation form, the standard deviation is calculated:

![](http://www.dspguide.com/graphics/E_2_2.gif)

In the alternative notation: sigma = sqrt\(\(x0 -??\)2 + \(x1 -??\)2 + ... + \(xN-1 -??\)2 / \(N-1\)\). Notice that the average is carried out by dividing by N - 1 instead of N. This is a subtle feature of the equation that will be discussed in the next section. The term, ??2, occurs frequently in statistics and is given the name variance. The standard deviation is a measure of how far the signal fluctuates from the mean. The variance represents the power of this fluctuation. Another term you should become familiar with is the rms \(root-mean-square\) value, frequently used in electronics. By definition, the standard deviation only measures the AC portion of a signal, while the rms value measures both the AC and DC components. If a signal has no DC component, its rms value is identical to its standard deviation. Figure 2-2 shows the relationship between the standard deviation and the peak-to-peak value of several common waveforms.

![](http://www.dspguide.com/graphics/F_2_2.gif)

Table 2-1 lists a computer routine for calculating the mean and standard deviation using Eqs. 2-1 and 2-2. The programs in this book are intended to convey algorithms in the most straightforward way; all other factors are treated as secondary. Good programming techniques are disregarded if it makes the program logic more clear. For instance: a simplified version of BASIC is used, line numbers are included, the only control structure allowed is the FOR-NEXT loop, there are no I/O statements, etc. Think of these programs as an alternative way of understanding the equations used

![](http://www.dspguide.com/graphics/T_2_1.gif)

in DSP. If you can't grasp one, maybe the other will help. In BASIC, the % character at the end of a variable name indicates it is an integer. All other variables are floating point. Chapter 4 discusses these variable types in detail.

This method of calculating the mean and standard deviation is adequate for many applications; however, it has two limitations. First, if the mean is much larger than the standard deviation, Eq. 2-2 involves subtracting two numbers that are very close in value. This can result in excessive round-off error in the calculations, a topic discussed in more detail in Chapter 4. Second, it is often desirable to recalculate the mean and standard deviation as new samples are acquired and added to the signal. We will call this type of calculation: running statistics. While the method of Eqs. 2-1 and 2-2 can be used for running statistics, it requires that all of the samples be involved in each new calculation. This is a very inefficient use of computational power and memory.

A solution to these problems can be found by manipulating Eqs. 2-1 and 2-2 to provide another equation for calculating the standard deviation:

![](http://www.dspguide.com/graphics/E_2_3.gif)

While moving through the signal, a running tally is kept of three parameters: \(1\) the number of samples already processed, \(2\) the sum of these samples, and \(3\) the sum of the squares of the samples \(that is, square the value of each sample and add the result to the accumulated value\). After any number of samples have been processed, the mean and standard deviation can be efficiently calculated using only the current value of the three parameters. Table 2-2 shows a program that reports the mean and standard deviation in this manner as each new sample is taken into account. This is the method used in hand calculators to find the statistics of a sequence of numbers. Every time you enter a number and press the ?? \(summation\) key, the three parameters are updated. The mean and standard deviation can then be found whenever desired, without having to recalculate the entire sequence.

![](http://www.dspguide.com/graphics/T_2_2.gif)

Before ending this discussion on the mean and standard deviation, two other terms need to be mentioned. In some situations, the mean describes what is being measured, while the standard deviation represents noise and other interference. In these cases, the standard deviation is not important in itself, but only in comparison to the mean. This gives rise to the term: signal-to-noise ratio \(SNR\), which is equal to the mean divided by the standard deviation. Another term is also used, the coefficient of variation \(CV\). This is defined as the standard deviation divided by the mean, multiplied by 100 percent. For example, a signal \(or other group of measure values\) with a CV of 2%, has an SNR of 50. Better data means a higher value for the SNR and a lower value for the CV.



### Signal vs. Underlying Process

Statistics is the science of interpreting numerical data, such as acquired signals. In comparison, probability is used in DSP to understand the processes that generate signals. Although they are closely related, the distinction between the acquired signal and the underlying process is key to many DSP techniques.

For example, imagine creating a 1000 point signal by flipping a coin 1000 times. If the coin flip is heads, the corresponding sample is made a value of one. On tails, the sample is set to zero. The process that created this signal has a mean of exactly 0.5, determined by the relative probability of each possible outcome: 50% heads, 50% tails. However, it is unlikely that the actual 1000 point signal will have a mean of exactly 0.5. Random chance will make the number of ones and zeros slightly different each time the signal is generated. The probabilities of the underlying process are constant, but the statistics of the acquired signal change each time the experiment is repeated. This random irregularity found in actual data is called by such names as: statistical variation, statistical fluctuation, and statistical noise.

This presents a bit of a dilemma. When you see the terms: mean and standard deviation, how do you know if the author is referring to the statistics of an actual signal, or the probabilities of the underlying process that created the signal? Unfortunately, the only way you can tell is by the context. This is not so for all terms used in statistics and probability. For example, the histogram and probability mass function \(discussed in the next section\) are matching concepts that are given separate names.

Now, back to Eq. 2-2, calculation of the standard deviation. As previously mentioned, this equation divides by N-1 in calculating the average of the squared deviations, rather than simply by N. To understand why this is so, imagine that you want to find the mean and standard deviation of some process that generates signals. Toward this end, you acquire a signal of N samples from the process, and calculate the mean of the signal via Eq. 2.1. You can then use this as an estimate of the mean of the underlying process; however, you know there will be an error due to statistical noise. In particular, for random signals, the typical error between the mean of the N points, and the mean of the underlying process, is given by:

![](http://www.dspguide.com/graphics/E_2_4.gif)

If N is small, the statistical noise in the calculated mean will be very large. In other words, you do not have access to enough data to properly characterize the process. The larger the value of N, the smaller the expected error will become. A milestone in probability theory, the Strong Law of Large Numbers, guarantees that the error becomes zero as N approaches infinity.

In the next step, we would like to calculate the standard deviation of the acquired signal, and use it as an estimate of the standard deviation of the underlying process. Herein lies the problem. Before you can calculate the standard deviation using Eq. 2-2, you need to already know the mean, ??. However, you don't know the mean of the underlying process, only the mean of the N point signal, which contains an error due to statistical noise. This error tends to reduce the calculated value of the standard deviation. To compensate for this, N is replaced by N-1. If N is large, the difference doesn't matter. If N is small, this replacement provides a more accurate

![](http://www.dspguide.com/graphics/F_2_3.gif)

estimate of the standard deviation of the underlying process. In other words, Eq. 2-2 is an estimate of the standard deviation of the underlying process. If we divided by N in the equation, it would provide the standard deviation of the acquired signal.

As an illustration of these ideas, look at the signals in Fig. 2-3, and ask: are the variations in these signals a result of statistical noise, or is the underlying process changing? It probably isn't hard to convince yourself that these changes are too large for random chance, and must be related to the underlying process. Processes that change their characteristics in this manner are called nonstationary. In comparison, the signals previously presented in Fig. 2-1 were generated from a stationary process, and the variations result completely from statistical noise. Figure 2-3b illustrates a common problem with nonstationary signals: the slowly changing mean interferes with the calculation of the standard deviation. In this example, the standard deviation of the signal, over a short interval, is one. However, the standard deviation of the entire signal is 1.16. This error can be nearly eliminated by breaking the signal into short sections, and calculating the statistics for each section individually. If needed, the standard deviations for each of the sections can be averaged to produce a single value.

