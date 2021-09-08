# Why Do We Need Filters?



#### Why Do We Need Filters?

Filters are used in a wide variety of applications. Most of the time, the final goal of using a filter is to achieve a kind of frequency selectivity on the spectrum of the input signal.

As an example, suppose that a 50-Hz noise falls on top of the signal produced by a sensor. The noise component may be strong enough to limit the measurement precision. The output of the sensor is usually converted to a digital signal by an ADC to be processed by a DSP or a microcontroller. Therefore, we can use a digital filter after the ADC to eliminate the noise component. In this particular example, a notch filter centered at 50 Hz can be utilized to suppress the noise.

At this point, it is worth reviewing the frequency response of a practical filter. Figure \(1\) shows an example of a practical lowpass filter. In this example, frequency components in the passband, from DC to ωpωp, will pass through the filter almost with no attenuation. The components in the stopband, above ωsωs, will experience significant attenuation. Note that the frequency response of a practical filter cannot be absolutely flat in the passband or in the stopband. As shown in Figure \(1\), some ripples will be unavoidable and the transition band, ωp&lt;ω&lt;ωsωp&lt;ω&lt;ωs , cannot be infinitely sharp in practice.

![](https://www.allaboutcircuits.com/uploads/articles/Fig1_1.jpg)​

**Figure \(1\) Frequency response of a practical lowpass filter. Image courtesy of the University of Michigan \(PDF\).**

#### General Considerations

Digital filter design involves four steps:

1\) **Determining specifications**

First, we need to determine what specifications are required. This step completely depends on the application. In the example of 50-Hz noise on the output of the sensor, we need to know how strong the noise component is relative to the desired signal and how much we need to suppress the noise. This information is necessary to find the filter with minimum order for this application.

2\) **Finding a transfer function**

With design specifications known, we need to find a transfer function which will provide the required filtering. The rational transfer function of a digital filter is as in Equation \(1\).

H\(z\)=∑M−1k=0bkz−k∑N−1k=0akz−kH\(z\)=∑k=0M−1bkz−k∑k=0N−1akz−k

**Equation \(1\)**

This step calculates the coefficients, akak and bkbk, in Equation \(1\).

3\) **Choosing a realization structure**

Now that H\(z\)H\(z\) is known, we should choose the realization structure. In other words, there are many systems which can give the obtained transfer function and we must choose the appropriate one. For example, any of the direct form I, II, cascade, parallel, transposed, or lattice forms can be used to realize a particular transfer function. The main difference between the aforementioned realization structures is their sensitivity to using a finite length of bits. Note that in the final digital system, we will use a finite length of bits to represent a signal or a filter coefficient. Some realizations, such as direct forms, are very sensitive to quantization of the coefficients. However, cascade and parallel structures show smaller sensitivity and are preferred.

4\) **Implementing the filter**

After deciding on what realization structure to use, we should implement the filter. You have a couple of options for this step: a software implementation \(such as a MATLAB or C code\) or a hardware implementation \(such as a DSP, a microcontroller, or an ASIC\).

This article focuses on the second step in designing an FIR filter.

#### FIR Filters

An FIR filter is a special case of Equation \(1\), where a0=1a0=1 and ak=0ak=0 for k=1,...,N−1k=1,...,N−1, hence we obtain:

H\(z\)=M−1∑k=0bkz−kH\(z\)=∑k=0M−1bkz−k

**Equation \(2\)**

The direct form realization of Equation \(2\) for M=3 is shown in Figure \(2\). As shown in this figure, a digital filter can be implemented using only three elements: 

1. Addition
2. Multiplication by a constant \(necessary for the implementation of the coefficients\)
3. Delay blocks

![](https://www.allaboutcircuits.com/uploads/articles/Fig2_1.jpg)

**Figure \(2\) Direct form of an FIR filter of order 2**

There are three coefficients and two delay cells in Figure \(2\). Note that this filter is of order 2, the number of delay cells, not 3, the number of coefficients.

An FIR filter has two important advantages over an IIR design:

Firstly, as shown in Figure \(2\), there is no feedback loop in the structure of an FIR filter. Due to not having a feedback loop, an FIR filter is inherently stable. Meanwhile, for an IIR filter, we need to check the stability.

Secondly, an FIR filter can provide a linear-phase response. As a matter of fact, a linear-phase response is the main advantage of an FIR filter over an IIR design—otherwise, for the same filtering specifications, an IIR filter will lead to a lower order.

In order to have a linear-phase FIR filter, we must provide symmetry in the time domain, i.e. b\[n\]=±b\[M−1−n\]b\[n\]=±b\[M−1−n\]. In the example shown in Figure \(2\), assume that b0=b2b0=b2, hence Equation \(2\) gives

H\(z\)=b0+b1e−jω+b0e−j2ω=e−jω\(b1+2b0cos\(ω\)\)H\(z\)=b0+b1e−jω+b0e−j2ω=e−jω\(b1+2b0cos⁡\(ω\)\)

**Equation \(3\)**

Since bkbk is real, phase of H\(z\)H\(z\) will be

∡H\(z\)={−ωpb1+2b0cos\(ω\)&gt;0−ωp+πb1+2b0cos\(ω\)&lt;0∡H\(z\)={−ωpb1+2b0cos\(ω\)&gt;0−ωp+πb1+2b0cos\(ω\)&lt;0

**Equation \(4\)**

Therefore, the phase response will be linear. Although this example shows a linear-phase response in the case of a three-tap filter, it can be shown that for an arbitrary value of MM, time-domain symmetry leads to a linear-phase response. This is an important property which helps us to examine the linear-phase response of an FIR filter just by considering the values of bkbk without any calculation.

The reader may wonder why a linear-phase frequency response is important. To gain insight, consider the continuous-time case. Assume that the frequency response of a system is

H\(s\)=αe−jβωH\(s\)=αe−jβω

**Equation \(5\)**

where αα and ββ are real constants. The phase response of this system is linear, i.e. ∡H\(s\)=−βω∡H\(s\)=−βω.

If we apply x\(t\)=Acos\(ω1t\)x\(t\)=Acos\(ω1t\) to this system, the output will be y\(t\)=αAcos\(ω1t−βω1\)=αx\(t−β\)y\(t\)=αAcos\(ω1t−βω1\)=αx\(t−β\). Therefore, the linear-phase response corresponds to a constant delay. A system with a nonlinear-phase response will distort the input, even if \|H\(s\)\|\|H\(s\)\| is constant. In such a system, different frequency components of the input will experience different time delays as they pass through the system. For a digital system with a phase response of ∡H\(z\)=−kω∡H\(z\)=−kω where kk is an integer, we can also prove that the linear phase is equal to a constant delay.

#### Introduction to FIR Filter Design by Windowing

We will explain the window method by using an example. Suppose that we want to design a lowpass filter with a cutoff frequency of ωcωc, i.e. the desired frequency response will be:

Hd\(ω\)={1\|ω\|&lt;ωc0elseHd\(ω\)={1\|ω\|&lt;ωc0else

**Equation \(6\)**

To find the equivalent time-domain representation, we calculate the inverse discrete-time Fourier transform:

hd\[n\]=12π∫+π−πHd\(ω\)ejωndωhd\[n\]=12π∫−π+πHd\(ω\)ejωndω

**Equation \(7\)**

Substituting Equation \(6\) into Equation \(7\), we obtain:

hd\[n\]=12π∫+ωc−ωcejωndω=sin\(nωc\)nπhd\[n\]=12π∫−ωc+ωcejωndω=sin⁡\(nωc\)nπ

**Equation \(8\)**

Equation \(8\) for ωc=π4ωc=π4 is shown in Figure \(3\):

![](https://www.allaboutcircuits.com/uploads/articles/Fig3.jpg)

**Figure \(3\) Impulse response of an ideal lowpass filter with ωc=π4ωc=π4**

Figure \(3\) shows that hd\[n\]hd\[n\] needs an infinite number of input samples to perform filtering and that the system is not a causal system.

The obvious solution will be to truncate the impulse response and use, for example, only 21 samples of the input and assume other coefficients to be zero. Intuition suggests that, as the number of samples increases, the truncated impulse response will be closer to the ideal impulse response in Figure \(3\) and therefore the frequency response of the achieved filter will be closer to Equation \(6\).

On the other hand, as we increase the number of samples, more hardware will be required. If we choose to use only 21 taps of the ideal response, there will be three options which are shown in Figures \(4\) to \(6\).

The first option is shown in Figure \(4\). This impulse response corresponds to a non-causal system and cannot be used. 

![](https://www.allaboutcircuits.com/uploads/articles/Arar_windowing_fig4_.jpg)

**Figure \(4\) Truncated impulse response: linear-phase, but non-causal**

The next option is shown in Figure \(5\) which, despite being causal, does not have a linear-phase response \(the most important property of an FIR system\).

![](https://www.allaboutcircuits.com/uploads/articles/Fig5.jpg)

**Figure \(5\) Truncated impulse response: causal, but nonlinear-phase**

The last option is shown in Figure \(6\). This system is both causal and linear phase. The only drawback to this system is its delay which is M−12M−12 samples. In other words, in response to an impulse at n=0n=0, the system will not react until almost n=M−12n=M−12. This delay may cause problems in some applications.

![](https://www.allaboutcircuits.com/uploads/articles/Fig6.jpg)

**Figure \(6\) Truncated impulse response: causal and linear phase**

Truncation of the impulse response is equivalent to multiplying hd\[n\]hd\[n\] \(or its shifted version\) by a rectangular window, w\[n\]w\[n\] which is equal to one for n=0,...,M−1n=0,...,M−1 and zero otherwise. Therefore, considering the applied shift, we obtain the impulse response of the designed filter:

h\[n\]=hd\[n−M−12\]w\[n\]h\[n\]=hd\[n−M−12\]w\[n\]

**Equation \(9\)**

Clearly the spectrum of the rectangular window will cause the filter response to deviate from the ideal response in Equation \(6\). Figure \(7\) compares the response of the designed filter with that of the ideal one.

This figure shows that, unlike the ideal filter, the designed filter has a smoother transition from the passband to the stopband. Moreover, there are some ripples in both the passband and stopband of H\(ω\)H\(ω\) . How can we make the transition band sharper? How can we make the ripples smaller? What other options are there to be used instead of a rectangular window?

![](https://www.allaboutcircuits.com/uploads/articles/Fig7.jpg)

**Figure \(7\) Frequency response of the filter designed by a rectangular window**

#### Summary

* To design a digital filter, we need to find the coefficients, akak and bkbk, in Equation \(1\).
* An FIR filter is a special case of Equation \(1\), where a0=1a0=1 and ak=0ak=0 for k=1,...,N−1k=1,...,N−1.
* Stability and linear-phase response are the two most important advantages of an FIR filter over an IIR filter.
* A linear-phase frequency response corresponds to a constant delay.
* Truncation of the impulse response is equivalent to multiplying hd\[n\]hd\[n\] by a rectangular window, w\[n\]w\[n\], which is equal to one for n=0,...,M−1n=0,...,M−1 and zero otherwise.
* A wider transition band and ripples in the passband and stopband are the most important differences between the ideal filters and those designed by window method.



This article will review some basic structures to implement Finite Impulse Response \(FIR\) filters.

When designing a filter, we start from a set of specifications which are generally determined by a particular application. For example, we may need to suppress the 50-Hz noise which appears at the output of a sensor and makes our measurements inaccurate. Based on the frequency and strength of the noise component, we can determine the filter specifications such as the passband and stopband edge, the transition bandwidth, the ultimate out-of-band rejection, etc. Now, we can find the system function, H\(z\)H\(z\), which satisfies these requirements.

For a FIR design, we have a couple of options such as [the windowing method](https://www.allaboutcircuits.com/technical-articles/finite-impulse-response-filter-design-by-windowing-part-i-concepts-and-rect/), the frequency sampling method, and more. Then, we need to choose [a realization structure](http://www.ee.ic.ac.uk/hp/staff/dmb/courses/DSPDF/01000_Structures.pdf) for the obtained system function. In other words, there are several structures which exhibit the same system function H\(z\)H\(z\). One consideration for choosing the appropriate structure is the sensitivity to coefficient quantization. Since a digital filter uses a finite number of bits to represent signals and coefficients, we need structures which can somehow retain the target filter specifications even after quantizing the coefficients. In addition, sometimes we observe that a particular structure can dramatically reduce the computational complexity of the system.

#### The Direct-Form Structure

The direct-form structure is directly obtained from the difference equation. Assume that the difference equation of the FIR filter is given by

y\(n\)=M−1∑k=0bkx\(n−k\)y\(n\)=∑k=0M−1bkx\(n−k\)

**Equation 1**

Based on the above equation, we need the current input sample and M−1M−1 previous samples of the input to produce an output point. For M=5M=5, we can simply obtain the following diagram from Equation 1.

![](https://www.allaboutcircuits.com/uploads/articles/Fig19282017.png)

**Figure 1. Direct-form structure for a fourth-order FIR filter.**

Using the direct-form realization of Figure 1, we need MM multipliers for an \(M−1\)\(M−1\)th-order FIR filter. However, usually, we can almost halve the number of multipliers. This can be achieved by noting that we are mainly interested in linear-phase FIR filters. In fact, the main advantage of a FIR filter over an infinite impulse response \(IIR\) design is its linear-phase response, otherwise, for a given set of specifications, an IIR design can offer a filter of lower order and reduce the computational complexity. On the other hand, for a linear-phase FIR filter, we observe the following [symmetry in the coefficients](https://www.allaboutcircuits.com/technical-articles/finite-impulse-response-filter-design-by-windowing-part-i-concepts-and-rect/) of the difference equation

bk=±bM−1−kbk=±bM−1−k

For M=5M=5, Equation 1 gives

y\(n\)=b0x\(n\)+b1x\(n−1\)+b2x\(n−2\)+b3x\(n−3\)+b4x\(n−4\)y\(n\)=b0x\(n\)+b1x\(n−1\)+b2x\(n−2\)+b3x\(n−3\)+b4x\(n−4\)

Assuming bk=bM−1−kbk=bM−1−k, we obtain

y\(n\)=b0\(x\(n\)+x\(n−4\)\)+b1\(x\(n−1\)+x\(n−3\)\)+b2x\(n−2\)y\(n\)=b0\(x\(n\)+x\(n−4\)\)+b1\(x\(n−1\)+x\(n−3\)\)+b2x\(n−2\)

The structure obtained from the above equation is shown in Figure 2. While Figure 1 requires five multipliers, employing the symmetry of a linear-phase FIR filter, we can implement the filter using only three multipliers. This example shows that for an odd MM, the symmetry property reduces the number of multipliers of an \(M−1\)\(M−1\)th-order FIR filter from MM to M+12M+12. For a brief discussion about the importance of linear-phase response see [this article](https://www.allaboutcircuits.com/technical-articles/finite-impulse-response-filter-design-by-windowing-part-i-concepts-and-rect/).

![](https://www.allaboutcircuits.com/uploads/articles/Fig29282017.png)

**Figure 2. The symmetry of a linear-phase FIR filter can be used to reduce the number of multipliers.**

#### The Cascade-Form Structure

While the direct form is derived from the difference equation, the cascade structure is obtained from the system function H\(z\)H\(z\). The idea is to decompose the target system function into a cascade of second-order FIR systems. In other words, we need to find second-order systems which satisfy

H\(z\)=M−1∑k=0bkz−k=P∏k=1\(b0k+b1kz−1+b2kz−2\)H\(z\)=∑k=0M−1bkz−k=∏k=1P\(b0k+b1kz−1+b2kz−2\)

**Equation 2**

where PP is the integer part of M2M2. For example, M=5M=5, H\(z\)H\(z\) will be a polynomial of degree four which can be decomposed into two second-order sections. Each of these second-order filters can be realized using a direct form structure. It is desirable to set a pair of complex-conjugate roots for each of the second-order sections so that the coefficients become real. The reader may wonder why we need to rewrite a given H\(z\)H\(z\) in terms of second-order sections. In a future article, we will see that the main advantage of the cascade structure is its smaller sensitivity to the coefficient quantization.

To clarify converting a system function into the cascade form, let’s review an example.

#### Example 1

Assume that we need to implement the nine-tap FIR filter given by the following table using a cascade structure.

![](https://www.allaboutcircuits.com/uploads/articles/Table1.png)

The system function of this filter is

H\(z\)=−0.0977+0.1497z−2+0.2813z−3+0.3333z−4+0.2813z−5+0.1497z−6−0.0977z−8H\(z\)=−0.0977+0.1497z−2+0.2813z−3+0.3333z−4+0.2813z−5+0.1497z−6−0.0977z−8

It can be shown that

H\(z\)=GH1\(z\)H2\(z\)H3\(z\)H4\(z\)H\(z\)=GH1\(z\)H2\(z\)H3\(z\)H4\(z\)

where

G=−0.0977G=−0.0977

H1\(z\)=\(1−2.5321z−1+z−2\)H1\(z\)=\(1−2.5321z−1+z−2\)

H2\(z\)=\(1−0.3474z−1+z−2\)H2\(z\)=\(1−0.3474z−1+z−2\)

H3\(z\)=\(1+1.8794z−1+z−2\)H3\(z\)=\(1+1.8794z−1+z−2\)

H4\(z\)=\(1+z−1+z−2\)H4\(z\)=\(1+z−1+z−2\)

Hence, we obtain the structure shown in Figure 3.

![](https://www.allaboutcircuits.com/uploads/articles/Fig3m9282017.png)

**Figure 3. The cascade structure for the system function of Example 1.**

Each of these second-order systems can be realized using the direct-form structure. For example, the realization of H1\(z\)H1\(z\) is shown in Figure 4.

![](https://www.allaboutcircuits.com/uploads/articles/Fig4m9282017.png)

**Figure 4. The direct form realization of H1\(z\)H1\(z\).**

You can verify that H1\(z\)H1\(z\) pairs two real zeros of H\(z\)H\(z\), i.e. z1=2.0425z1=2.0425 and z2=0.4896z2=0.4896; however, the other three second-order sections \(sos\) incorporate the complex-conjugate roots of H\(z\)H\(z\). For example, the roots of H2\(z\)H2\(z\) are z3=0.1737+0.9848jz3=0.1737+0.9848j and z4=0.1737−0.9848jz4=0.1737−0.9848j.

Since finding the cascade form of a practical FIR filter involves tedious mathematics, we can use the MATLAB function _tf2sos_, which stands for transfer function to second-order section, to obtain the cascade form of a given transfer function. In fact, the cascade form of H\(z\)H\(z\) in the above example was found using the _tf2sos_ function with the following lines of code:

_N=\[-0.0977 0 0.1497 0.2813 0.3333 0.2813 0.1497 0 -0.0977\]; % This line defines the numerator of H\(z\)_

_D=1; % This defines the denominator of H\(z\)_

_\[sos, G\]=tf2sos\(N, D\) % converts the transfer function defined by Nand Dinto a cascade of second-order sections_

The result will be:

sos=

![](https://www.allaboutcircuits.com/uploads/articles/Table2.png)

and G=−0.0977G=−0.0977.

Each row of sos above gives the transfer function of one of the second-order sections. The first three numbers of each row represent the numerator of the corresponding second-order section and the second three numbers give its denominator. For example, the first row of sos gives the second-order section H1\(z\)H1\(z\) of Example 1 and so on. The _tf2sos_ command also gives a gain factor, GG, which can be included in the cascade-form structure as shown in Figure 3.

#### Example 2

Assume that we need to implement the ten-tap FIR filter given by the following table using a cascade structure.

![](https://www.allaboutcircuits.com/uploads/articles/Table3.png)

Similar to the previous example, we have:

_N=\[-0.0024 0.0073 0.0606 0.1691 0.2654 0.2654 0.1691 0.0606 0.0073 -0.0024\];  
D=1;  
\[sos, G\]=tf2sos\(N, D\)_

The result will be:

sos =

![](https://www.allaboutcircuits.com/uploads/articles/Table4.png)

and G=−0.0024G=−0.0024.

Hence, the target system function can be rewritten in terms of second-order sections as

H\(z\)=GH1\(z\)H2\(z\)H3\(z\)H4\(z\)H5\(z\)H\(z\)=GH1\(z\)H2\(z\)H3\(z\)H4\(z\)H5\(z\)

where

G=−0.0024G=−0.0024

H1\(z\)=1−7.7465z−1H1\(z\)=1−7.7465z−1

H2\(z\)=1+0.8709z−1−0.1291z−2H2\(z\)=1+0.8709z−1−0.1291z−2

H3\(z\)=1+1.7922z−1+1.6972z−2H3\(z\)=1+1.7922z−1+1.6972z−2

H4\(z\)=1+0.9858z−1+z−2H4\(z\)=1+0.9858z−1+z−2

H5\(z\)=1+1.0560z−1+0.5892z−2H5\(z\)=1+1.0560z−1+0.5892z−2

In this example, the system function polynomial is of degree nine and, hence, the filter has nine zeros. As a result, we observe that H1\(z\)H1\(z\) incorporates only one zero, i.e. the coefficient b2kb2k in Equation 2 is zero for this second-order section.

We can realize the second-order sections of this example using a direct form structure and obtain the cascade structure of the filter; however, there is another alternative which allows us to reduce the computational complexity. To find this computationally efficient structure, remember that, as illustrated by Figure 1 and 2 above, a linear-phase FIR filter can be realized with a smaller number of multipliers. On the other hand, notice that while the target system function is a linear phase, only H4\(z\)H4\(z\) is a linear-phase FIR structure \(because of the coefficient symmetry\).

So, the question remains: can we group the zeros of a given linear-phase FIR system function in a way that the obtained decomposition incorporates linear-phase structures? For a linear-phase FIR filter, the symmetry in the bkbk coefficients leads to asymmetry in the zeros of the transfer function. In particular, if z1z1 and z∗1z1∗ are the zeros of the transfer function, then 1z11z1 and 1z∗11z1∗ are also a pair of its zeros.We can use this property to group the zeros in a way that the system function is decomposed into linear-phase elements. Let’s use the MATLAB command _roots_, to find the zeros of the system function:

_N=\[-0.0024 0.0073 0.0606 0.1691 0.2654 0.2654 0.1691 0.0606 0.0073 -0.0024\];_

_roots\(N\)_

Hence, we obtain:

z1=−1.0000z1=−1.0000

z2=7.7465z2=7.7465, z3=0.1291z3=0.1291

z4=−0.4929+0.8701jz4=−0.4929+0.8701j, z5=−0.4929−0.8701jz5=−0.4929−0.8701j

z6=−0.5280+0.5571jz6=−0.5280+0.5571j, z7=−0.5280−0.5571jz7=−0.5280−0.5571j

z8=−0.8961+0.9456jz8=−0.8961+0.9456j, z9=−0.8961−0.9456jz9=−0.8961−0.9456j

The reader can verify that z2=1z3z2=1z3, z4=1z∗5z4=1z5∗, z6=1z∗8z6=1z8∗ and z7=1z∗9z7=1z9∗. Then, we can pair z2z2 and z3z3 to obtain the following linear-phase second-order section

HLP1\(z\)=\(1−0.1291z−1\)\(1−7.7465z−1\)=\(1−7.8756z−1+z−2\)HLP1\(z\)=\(1−0.1291z−1\)\(1−7.7465z−1\)=\(1−7.8756z−1+z−2\)

Pairing z4z4 and z5z5 gives:

HLP2\(z\)=\(1−\(−0.4929+0.8701j\)z−1\)\(1−\(−0.4929−0.8701j\)z−1\)=\(1+0.9858z−1+z−2\)HLP2\(z\)=\(1−\(−0.4929+0.8701j\)z−1\)\(1−\(−0.4929−0.8701j\)z−1\)=\(1+0.9858z−1+z−2\)

Grouping z6z6, z7z7, z8z8, and z9z9 together, we obtain:

HLP3\(z\)=1+2.8482z−1+4.1790z−2+2.8482z−3+z−4HLP3\(z\)=1+2.8482z−1+4.1790z−2+2.8482z−3+z−4

To incorporate the zero z1z1, we need to include a first-order section, i.e. HLP4\(z\)=1+z−1HLP4\(z\)=1+z−1. A cascade of these linear-phase elements will give the original system function:

H\(z\)=GHLP1\(z\)HLP2\(z\)HLP3\(z\)HLP4\(z\)H\(z\)=GHLP1\(z\)HLP2\(z\)HLP3\(z\)HLP4\(z\)

where G=−0.0024G=−0.0024 as before.

In general, the zeros of a linear-phase FIR filter can be of four different arrangements as illustrated in Figure 5. These arrangements include: 1- a pair of complex-conjugate zeros which are not on the unit circle along with their reciprocals, e.g. z1z1, z∗1z1∗, 1z11z1, and 1z∗11z1∗ in the figure, 2- a pair of complex-conjugate zeros on the unit circle such as z3z3 and z∗3z3∗ in the figure, 3- a real zero which is not on the unit circle along with its reciprocal such as z2z2 and 1z21z2, and finally, 4- a real zero on the unit circle like z4z4 in Figure 5. The system function of the above example had zeros of all these four groups.

![](https://www.allaboutcircuits.com/uploads/articles/Fig5m9282017.png)

**Figure 5. The symmetry of zeros for a linear-phase FIR filter. Image courtesy of Discrete-Time Signal Processing.**

Factoring the system function of Example 2 into linear-phase elements, we need a total of five multipliers. The following table shows the number of multipliers for each section.

![](https://www.allaboutcircuits.com/uploads/articles/Table5.png)

However, the first realization requires nine multipliers as listed below:

![](https://www.allaboutcircuits.com/uploads/articles/Table6.png)

In summary, we can use the _tf2sos_ command to rewrite the system function of a FIR filter as the product of second-order sections; however, these second-order sections are not necessarily linear-phase. To have a cascade of linear-phase elements, we need to group the zeros of the transfer function appropriately. Using a cascade of linear-phase sections, we can reduce the number of multiplications. Note that, in this case, some of the sections might be of order four as HLP3\(z\)HLP3\(z\) in the above example.

#### Summary

* There are several structures to realize a given system function H\(z\)H\(z\). One consideration choosing the appropriate structure is the sensitivity to coefficient quantization. In addition, sometimes we observe that a particular structure can dramatically reduce the computational complexity of the system.
* The symmetry property of a linear-phase FIR filter can be used to reduce the number of the required multiplications.
* The main advantage of the cascade structure is its smaller sensitivity to the coefficient quantization.
* We can use the _tf2sos_ command to rewrite the system function of a FIR filter as the product of second-order sections; however, these second-order sections are not necessarily linear-phase. To have a cascade of linear-phase elements, we need to group the zeros of the transfer function appropriately.

