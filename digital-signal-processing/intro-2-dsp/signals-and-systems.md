# Signals and Systems



A signal is a description of how one parameter varies with another parameter. For instance, voltage changing over time in an electronic circuit, or brightness varying with distance in an image. A system is any process that produces an output signal in response to an input signal. This is illustrated by the block diagram in Fig. 5-1. Continuous systems input and output continuous signals, such as in analog electronics. Discrete systems input and output discrete signals, such as computer programs that manipulate the values stored in arrays.

Several rules are used for naming signals. These aren't always followed in DSP, but they are very common and you should memorize them. The mathematics is difficult enough without a clear notation. First, continuous signals use parentheses, such as: x\(t\) and y\(t\), while discrete signals use brackets, as in: x\[n\] and y\[n\]. Second, signals use lower case letters. Upper case letters are reserved for the frequency domain, discussed in later chapters. Third, the name given to a signal is usually descriptive of the parameters it represents. For example, a voltage depending on time might be called: v\(t\), or a stock market price measured each day could be: p\[d\].

![](http://www.dspguide.com/graphics/F_5_1.gif)

Signals and systems are frequently discussed without knowing the exact parameters being represented. This is the same as using x and y in algebra, without assigning a physical meaning to the variables. This brings in a fourth rule for naming signals. If a more descriptive name is not available, the input signal to a discrete system is usually called: x\[n\], and the output signal: y\[n\]. For continuous systems, the signals: x\(t\) and y\(t\) are used.

There are many reasons for wanting to understand a system. For example, you may want to design a system to remove noise in an electrocardiogram, sharpen an out-of-focus image, or remove echoes in an audio recording. In other cases, the system might have a distortion or interfering effect that you need to characterize or measure. For instance, when you speak into a telephone, you expect the other person to hear something that resembles your voice. Unfortunately, the input signal to a transmission line is seldom identical to the output signal. If you understand how the transmission line \(the system\) is changing the signal, maybe you can compensate for its effect. In still other cases, the system may represent some physical process that you want to study or analyze. Radar and sonar are good examples of this. These methods operate by comparing the transmitted and reflected signals to find the characteristics of a remote object. In terms of system theory, the problem is to find the system that changes the transmitted signal into the received signal.

At first glance, it may seem an overwhelming task to understand all of the possible systems in the world. Fortunately, most useful systems fall into a category called linear systems. This fact is extremely important. Without the linear system concept, we would be forced to examine the individual characteristics of many unrelated systems. With this approach, we can focus on the traits of the linear system category as a whole. Our first task is to identify what properties make a system linear, and how they fit into the everyday notion of electronics, software, and other signal processing systems.



Requirements for Linearity

A system is called linear if it has two mathematical properties: homogeneity \(hōma-gen-ā-ity\) and additivity. If you can show that a system has both properties, then you have proven that the system is linear. Likewise, if you can show that a system doesn't have one or both properties, you have proven that it isn't linear. A third property, shift invariance, is not a strict requirement for linearity, but it is a mandatory property for most DSP techniques. When you see the term linear system used in DSP, you should assume it includes shift invariance unless you have reason to believe otherwise. These three properties form the mathematics of how linear system theory is defined and used. Later in this chapter we will look at more intuitive ways of understanding linearity. For now, let's go through these formal mathematical properties.

As illustrated in Fig. 5-2, homogeneity means that a change in the input signal's amplitude results in a corresponding change in the output signal's amplitude. In mathematical terms, if an input signal of x\[n\] results in an output signal of y\[n\], an input of kx\[n\] results in an output of ky\[n\], for any input signal and constant, k.![](http://www.dspguide.com/graphics/F_5_2.gif)

A simple resistor provides a good example of both homogenous and non-homogeneous systems. If the input to the system is the voltage across the resistor, v\(t\), and the output from the system is the current through the resistor, i\(t\) , the system is homogeneous. Ohm's law guarantees this; if the voltage is increased or decreased, there will be a corresponding increase or decrease in the current. Now, consider another system where the input signal is the voltage across the resistor, v\(t\), but the output signal is the power being dissipated in the resistor, p\(t\). Since power is proportional to the square of the voltage, if the input signal is increased by a factor of two, the output signal is increase by a factor of four. This system is not homogeneous and therefore cannot be linear.

The property of additivity is illustrated in Fig. 5-3. Consider a system where an input of x1\[n\] produces an output of y1\[n\]. Further suppose that a different input, x2\[n\], produces another output, y2\[n\]. The system is said to be additive, if an input of x1\[n\] + x2\[n\] results in an output of y1\[n\] + y2\[n\], for all possible input signals. In words, signals added at the input produce signals that are added at the output.![](http://www.dspguide.com/graphics/F_5_3.gif)

The important point is that added signals pass through the system without interacting. As an example, think about a telephone conversation with your Aunt Edna and Uncle Bernie. Aunt Edna begins a rather lengthy story about how well her radishes are doing this year. In the background, Uncle Bernie is yelling at the dog for having an accident in his favorite chair. The two voice signals are added and electronically transmitted through the telephone network. Since this system is additive, the sound you hear is the sum of the two voices as they would sound if transmitted individually. You hear Edna and Bernie, not the creature, Ednabernie.

A good example of a nonadditive circuit is the mixer stage in a radio transmitter. Two signals are present: an audio signal that contains the voice or music, and a carrier wave that can propagate through space when applied to an antenna. The two signals are added and applied to a nonlinearity, such as a pn junction diode. This results in the signals merging to form a third signal, a modulated radio wave capable of carrying the information over great distances.

As shown in Fig. 5-4, shift invariance means that a shift in the input signal will result in nothing more than an identical shift in the output signal. In more formal terms, if an input signal of x\[n\] results in an output of y\[n\], an input signal of x\[n + s\] results in an output of y\[n + s\], for any input signal and any constant, s. Pay particular notice to how the mathematics of this shift is written, it will be used in upcoming chapters. By adding a constant, s, to the independent variable, n, the waveform can be advanced or retarded in the horizontal direction. For example, when s = 2, the signal is shifted left by two samples; when s = -2, the signal is shifted right by two samples.

![](http://www.dspguide.com/graphics/F_5_4.gif)

Shift invariance is important because it means the characteristics of the system do not change with time \(or whatever the independent variable happens to be\). If a blip in the input causes a blop in the output, you can be assured that another blip will cause an identical blop. Most of the systems you encounter will be shift invariant. This is fortunate, because it is difficult to deal with systems that change their characteristics while in operation. For example, imagine that you have designed a digital filter to compensate for the degrading effects of a telephone transmission line. Your filter makes the voices sound more natural and easier to understand. Much to your surprise, along comes winter and you find the characteristics of the telephone line have changed with temperature. Your compensation filter is now mismatched and doesn't work especially well. This situation may require a more sophisticated algorithm that can adapt to changing conditions.

Why do homogeneity and additivity play a critical role in linearity, while shift invariance is something on the side? This is because linearity is a very broad concept, encompassing much more than just signals and systems. For example, consider a farmer selling oranges for $2 per crate and apples for $5 per crate. If the farmer sells only oranges, he will receive $20 for 10 crates, and $40 for 20 crates, making the exchange homogenous. If he sells 20 crates of oranges and 10 crates of apples, the farmer will receive: . This is the same amount as if the two had been sold individually, making the transaction additive. Being both homogenous and additive, this sale of goods is a linear process. However, since there are no signals involved, this is not a system, and shift invariance has no meaning. Shift invariance can be thought of as an additional aspect of linearity needed when signals and systems are involved.





## Examples of Linear and Nonlinear Systems

Table 5-1 provides examples of common linear and nonlinear systems. As you go through the lists, keep in mind the mathematician's view of linearity \(homogeneity, additivity, and shift invariance\), as well as the informal way most scientists and engineers use \(static linearity and sinusoidal fidelity\).

![](http://www.dspguide.com/graphics/T_5_1.gif)

Special Properties of Linearity

Linearity is commutative, a property involving the combination of two or more systems. Figure 5-10 shows the general idea. Imagine two systems combined in a cascade, that is, the output of one system is the input to the next. If each system is linear, then the overall combination will also be linear. The commutative property states that the order of the systems in the cascade can be rearranged without affecting the characteristics of the overall combination. You probably have used this principle in electronic circuits. For example, imagine a circuit composed of two stages, one for amplification, and one for filtering. Which is best, amplify and then filter, or filter and then amplify? If both stages are linear, the order doesn't make any difference and the overall result is the same. Keep in mind that actual electronics has nonlinear effects that may make the order important, for instance: interference, DC offsets, internal noise, slew rate distortion, etc.

![](http://www.dspguide.com/graphics/F_5_7.gif)

Figure 5-8 shows the next step in linear system theory: multiple inputs and outputs. A system with multiple inputs and/or outputs will be linear if it is composed of linear subsystems and additions of signals. The complexity does not matter, only that nothing nonlinear is allowed inside of the system.

To understand what linearity means for systems with multiple inputs and/or outputs, consider the following thought experiment. Start by placing a signal on one input while the other inputs are held at zero. This will cause the multiple outputs to respond with some pattern of signals. Next, repeat the procedure by placing another signal on a different input. Just as before, keep all of the other inputs at zero. This second input signal will result in another pattern of signals appearing on the multiple outputs. To finish the experiment, place both signals on their respective inputs simultaneously. The signals appearing on the outputs will simply be the superposition \(sum\) of the output signals produced when the input signals were applied separately.

![](http://www.dspguide.com/graphics/F_5_8.gif)

The use of multiplication in linear systems is frequently misunderstood. This is because multiplication can be either linear or nonlinear, depending on what the signal is multiplied by. Figure 5-9 illustrates the two cases. A system that multiplies the input signal by a constant, is linear. This system is an amplifier or an attenuator, depending if the constant is greater or less than one, respectively. In contrast, multiplying a signal by another signal is nonlinear. Imagine a sinusoid multiplied by another sinusoid; the resulting waveform is clearly not sinusoidal.

Another commonly misunderstood situation relates to parasitic signals added in electronics, such as DC offsets and thermal noise. Is the addition of these extraneous signals linear or nonlinear? The answer depends on where the contaminating signals are viewed as originating. If they are viewed as coming from within the system, the process is nonlinear. This is because a sinusoidal input does not produce a pure sinusoidal output. Conversely, the extraneous signal can be viewed as externally entering the system on a separate input of a multiple input system. This makes the process linear, since only a signal addition is required within the system.

![](http://www.dspguide.com/graphics/F_5_9.gif)

