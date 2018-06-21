## Digital Waveguides Review

Digital waveguides are a class of algorithms that model how acoustic waves travel through a medium. They thus belong to the more simple proponents of physical modeling algorithms. 

In general, they are implemented using two opposing delay lines, to indicate how waves are reflected at boundaries and travel back and forth through the medium, an excitation signal bringing energy into the system, a pickup withdrawing energy, and a lowpass filter representing friction loss at the boundaries.

The simplest case of string modeling is called the Karplus-Strong algorithm, and consists only of a tuneable, feedbacked delay line with a damping filter. 

## Spicing up

Although for this very simple process the output is astoundingly good, such systems often sound sterile and too polished, because they lack the nonlinearities introduced by material imperfections in the real world.

It is those imperfections, however, that provide realism and present a valuable opportunity for sound design at the same time. We will look at a way to model a string termination as an imperfect spring.

So, at the string boundary, after the delay line, we add a nonlinear allpass filter, that is, an allpass filter with modulatable coefficients. We start out by implementing a simple first order allpass filter as shown in this block diagram. ![](http://peabody.sapp.org/class/st1/lab/prog6/Allpass1-flowgraph.gif)
([http://peabody.sapp.org/class/st1/lab/prog6/](http://peabody.sapp.org/class/st1/lab/prog6/))

We implement the modulation by specifying one coefficient first, and a sample and hold logic to multiply that coefficient. While this provides a glimpse of what we are able to do here, it is a more physically correct modeling we're after here, that is, a string terminated by a nonlinear spring, which can be modelled by two separate springs with different stiffness coefficients.

Thus, we add a second coefficient to our allpass and use both in an alternating manner, based on the zero crossings of the input. In other words, whenever a zero crossing occurs, we switch the coefficient from one to the other. Since nonlinearities can introduce instability into a system, we minimize the probability of them occurring by modulating when the least amount of energy is in the system.

And here the fun part begins: Try experimenting with different combinations of excitation signals and modulators - but don't be surprised when the system grows unstable at some point, it has happened to me quite a few times ;)

For a scientific deduction of the algorithm, see [https://quod.lib.umich.edu/cgi/p/pod/dod-idx/traveling-wave-implementation-of-a-lossless-mode-coupling.pdf?c=icmc;idno=bbp2372.1994.106;format=pdf](https://quod.lib.umich.edu/cgi/p/pod/dod-idx/traveling-wave-implementation-of-a-lossless-mode-coupling.pdf?c=icmc;idno=bbp2372.1994.106;format=pdf)


