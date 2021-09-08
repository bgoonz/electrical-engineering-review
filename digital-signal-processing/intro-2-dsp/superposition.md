# Superposition

### Superposition: the Foundation of DSP

When we are dealing with linear systems, the only way signals can be combined is by scaling \(multiplication of the signals by constants\) followed by addition. For instance, a signal cannot be multiplied by another signal. Figure 5-10 shows an example: three signals: x0\[n\], x1\[n\], and x2\[n\] are added to form a fourth signal, x\[n\]. This process of combining signals through scaling and addition is called synthesis.

Decomposition is the inverse operation of synthesis, where a single signal is broken into two or more additive components. This is more involved than synthesis, because there are infinite possible decompositions for any given signal. For example, the numbers 15 and 25 can only be synthesized \(added\) into the number 40. In comparison, the number 40 can be decomposed into: 1 + 39 or 2 + 38 or -30.5 + 60 + 10.5, etc.

Now we come to the heart of DSP: superposition, the overall strategy for understanding how signals and systems can be analyzed. Consider an input

![](http://www.dspguide.com/graphics/F_5_11.gif)

![](http://www.dspguide.com/graphics/F_5_10.gif)

signal, called x\[n\], passing through a linear system, resulting in an output signal, y\[n\]. As illustrated in Fig. 5-11, the input signal can be decomposed into a group of simpler signals: x0\[n\], x1\[n\], x2\[n\], etc. We will call these the input signal components. Next, each input signal component is individually passed through the system, resulting in a set of output signal components: y0\[n\], y1\[n\], y2\[n\], etc. These output signal components are then synthesized into the output signal, y\[n\].

Here is the important part: the output signal obtained by this method is identical to the one produced by directly passing the input signal through the system. This is a very powerful idea. Instead of trying to understanding how complicated signals are changed by a system, all we need to know is how simple signals are modified. In the jargon of signal processing, the input and output signals are viewed as a superposition \(sum\) of simpler waveforms. This is the basis of nearly all signal processing techniques.

As a simple example of how superposition is used, multiply the number 2041 by the number 4, in your head. How did you do it? You might have imagined 2041 match sticks floating in your mind, quadrupled the mental image, and started counting. Much more likely, you used superposition to simplify the problem. The number 2041 can be decomposed into: 2000 + 40 + 1. Each of these components can be multiplied by 4 and then synthesized to find the final answer, i.e., 8000 + 160 + 4 = 8164.



## Common Decompositions

Keep in mind that the goal of this method is to replace a complicated problem with several easy ones. If the decomposition doesn't simplify the situation in some way, then nothing has been gained. There are two main ways to decompose signals in signal processing: impulse decomposition and Fourier decomposition. There are described in detail in the next several chapters. In addition, several minor decompositions are occasionally used. Here are brief descriptions of the two major decompositions, along with three minor ones.

Impulse Decomposition  
As shown in Fig. 5-12, impulse decomposition breaks an N samples signal into N component signals, each containing N samples. Each of the component signals contains one point from the original signal, with the remainder of the values being zero. A single nonzero point in a string of zeros is called an impulse. Impulse decomposition is important because it allows signals to be examined one sample at a time. Similarly, systems are characterized by how they respond to impulses. By knowing how a system responds to an impulse, the system's output can be calculated for any given input. This approach is called convolution, and is the topic of the next two chapters.

Step Decomposition  
Step decomposition, shown in Fig. 5-13, also breaks an N sample signal into N component signals, each composed of N samples. Each component signal is a step, that is, the first samples have a value of zero, while the last samples are some constant value. Consider the decomposition of an N point signal, x\[n\], into the components: x0\[n\], x1\[n\], x2\[n\], …, xN-1\[n\]. The kth component signal, xk\[n\], is composed of zeros for points 0 through k - 1, while the remaining points have a value of: x\[k\] - x\[k-1\]. For example, the 5th component signal, x5\[n\], is composed of zeros for points 0 through 4, while the remaining samples have a value of: x\[5\] - x\[4\] \(the difference between

![](http://www.dspguide.com/graphics/F_5_12.gif)

sample 4 and 5 of the original signal\). As a special case, x0\[n\] has all of its samples equal to x\[0\]. Just as impulse decomposition looks at signals one point at a time, step decomposition characterizes signals by the difference between adjacent samples. Likewise, systems are characterized by how they respond to a change in the input signal.

Even/Odd Decomposition  
The even/odd decomposition, shown in Fig. 5-14, breaks a signal into two component signals, one having even symmetry and the other having odd symmetry. An N point signal is said to have even symmetry if it is a mirror image around point N/2. That is, sample x\[N/2 + 1\] must equal x\[N/2 - 1\], sample x\[N/2 + 2\] must equal x\[N/2 - 2\], etc. Similarly, odd symmetry occurs when the matching points have equal magnitudes but are opposite in sign, such as: x\[N/2 + 1\] = -x\[N/2 - 1\], x\[N/2 + 2\] = -x\[N/2 - 2\], etc. These definitions assume that the signal is composed of an even number of samples, and that the indexes run from 0 to N-1. The decomposition is calculated form the relations:![](http://www.dspguide.com/graphics/E_5_1.gif)

This may seem a strange definition of left-right symmetry, since N/2 - ½ \(between two samples\) is the exact center of the signal, not N/2. Likewise, this off-center symmetry means that sample zero needs special handling. What's this all about?

This decomposition is part of an important concept in DSP called circular symmetry. It is based on viewing the end of the signal as connected to the beginning of the signal. Just as point x\[4\] is next to point x\[5\], point x\[N-1\] is next to point x\[0\]. Picture a snake biting its own tail. When even and odd signals are viewed in this circular manner, there are actually two lines of symmetry, one at point x\[N/2\] and another at point x\[0\]. For example, in an even signal, this symmetry around x\[0\] means that point x\[1\] equals point x\[N-1\], point x\[2\] equals point x\[N-2\], etc. In an odd signal, point 0 and point N/2 always have a value of zero. In an even signal, point 0 and point N/2 are equal to the corresponding points in the original signal.

What is the motivation for viewing the last sample in a signal as being next to the first sample? There is nothing in conventional data acquisition to support this circular notion. In fact, the first and last samples generally have less in common than any other two points in the sequence. It's common sense! The missing piece to this puzzle is a DSP technique called Fourier analysis. The mathematics of Fourier analysis inherently views the signal as being circular, although it usually has no physical meaning in terms of where the data came from. We will look at this in more detail in Chapter 10. For now, the important thing to understand is that Eq. 5-1 provides a valid decomposition, simply because the even and odd parts can be added together to reconstruct the original signal.

![](http://www.dspguide.com/graphics/F_5_14.gif)

Interlaced Decomposition  
As shown in Fig. 5-15, the interlaced decomposition breaks the signal into two component signals, the even sample signal and the odd sample signal \(not to be confused with even and odd symmetry signals\). To find the even sample signal, start with the original signal and set all of the odd numbered samples to zero. To find the odd sample signal, start with the original signal and set all of the even numbered samples to zero. It's that simple.

At first glance, this decomposition might seem trivial and uninteresting. This is ironic, because the interlaced decomposition is the basis for an extremely important algorithm in DSP, the Fast Fourier Transform \(FFT\). The procedure for calculating the Fourier decomposition has been know for several hundred years. Unfortunately, it is frustratingly slow, often requiring minutes or hours to execute on present day computers. The FFT is a family of algorithms developed in the 1960s to reduce this computation time. The strategy is an exquisite example of DSP: reduce the signal to elementary components by repeated use of the interlace transform; calculate the Fourier decomposition of the individual components; synthesized the results into the final answer. The results are dramatic; it is common for the speed to be improved by a factor of hundreds or thousands.

Fourier Decomposition  
Fourier decomposition is very mathematical and not at all obvious. Figure 5-16 shows an example of the technique. Any N point signal can be decomposed into N+2 signals, half of them sine waves and half of them cosine waves. The lowest frequency cosine wave \(called xC0\[n\] in this illustration\), makes zero complete cycles over the N samples, i.e., it is a DC signal. The next cosine components: xC1\[n\], xC2\[n\], and xC3\[n\], make 1, 2, and 3 complete cycles over the N samples, respectively. This pattern holds for the remainder of the cosine waves, as well as for the sine wave components. Since the frequency of each component is fixed, the only thing that changes for different signals being decomposed is the amplitude of each of the sine and cosine waves.

Fourier decomposition is important for three reasons. First, a wide variety of signals are inherently created from superimposed sinusoids. Audio signals are a good example of this. Fourier decomposition provides a direct analysis of the information contained in these types of signals. Second, linear systems respond to sinusoids in a unique way: a sinusoidal input always results in a sinusoidal output. In this approach, systems are characterized by how they change the amplitude and phase of sinusoids passing through them. Since an input signal can be decomposed into sinusoids, knowing how a system will react to sinusoids allows the output of the system to be found. Third, the Fourier decomposition is the basis for a broad and powerful area of mathematics called Fourier analysis, and the even more advanced Laplace and z-transforms. Most cutting-edge DSP algorithms are based on some aspect of these techniques.

Why is it even possible to decompose an arbitrary signal into sine and cosine waves? How are the amplitudes of these sinusoids determined for a particular signal? What kinds of systems can be designed with this technique? These are the questions to be answered in later chapters. The details of the Fourier decomposition are too involved to be presented in this brief overview. For now, the important idea to understand is that when all of the component sinusoids are added together, the original signal is exactly reconstructed. Much more on this in Chapter 8.

