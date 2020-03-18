
*Note: this file is an early design document, but might be updated as the version goes up.*

# Beam splitter #

This article is primarily for reference, since we don't plan to make
beam splitters separate entities in the simulator.

## Photon Number States ##

When you see  $$|0\rangle$$, $$|1\rangle$$, $$|2\rangle$$, etc. in a
paper on quantum optics, be aware that it likely represents a photon
number state, also called Fock state, I believe.  The 0, 1, 2
represents the number of photons in a particular place and time
(called a _spatial mode_).

For photon number (or spatial mode) qubits, photon statistics at beam
splitters are complicated.

See:

1. Weihs and Zeilinger lecture notes from Caltech QIP course
1. Sec. 6.2 & 6.3 of Gerry & Knight
1. Campos et al., PRA 40(3), 1371, 1989, esp. Eqs. 24, 42-48

## Polarization States ##

When you see $$|H\rangle$$ and $$|V\rangle$$ states, they refer to the
polarization of a photon.  It's important to realize, though, that
they represent the polarization of photon in a particular place and at
a fixed time.  Weihs and Zeilinger refer to it as spin representing an
_additional_ degree of freedom, and are very explicit about writing
out the behavior of the BS in four bases: H and V at each of the two
input ports.  This allows the unitary to be written properly, with the
after state being a four-basis representation at the two output ports.

Based on Eqs. 1.21 & 1.21 of W&Z, in the basis

$$\left(\begin{matrix}
a_H \\ b_H \\ a_V \\ b_V
\end{matrix}\right)$$

the unitary is

$$\left(\begin{matrix}
t_H & ir_H & 0 & 0 \\
ir_H & t_H & 0 & 0 \\
0 & 0 & t_V & ir_V \\
0 & 0 & ir_V & t_V
\end{matrix}\right)$$

where $$t$$ is the transmission amplitude and $$r$$ is the reflection
amplitude.

n.b.: I'm not positive that the sign of the terms is actually right;
there should be a relative phase shift of $$\pi$$ for one term, or
$$\pm\pi/2$$ for both.  Is that what this actually does?  Satoh and I
think that this produces $$\pi/2$$ difference in the states.  We don't
quite understand yet.  (Wikipedia says that even for the quantum
mechanical one, the phase difference between reflected and transmitted
beams should be $$\pi$$.)

## Reconciling with Classical Beam Splitters and Interferometry ##

It's worth investing some words in this topic of the phase shift (and
perhaps amplitude) and how we represent that mathematically.

Gerry & Knight answers some questions about what happens to the phase
of a state at a beam splitter; it's dependent on the dielectric
constant.  According to Wikipedia, for a classical beam splitter, it
depends on whether you are going from high index of refraction to low
index of refraction, or vice versa; see
[[https://en.wikipedia.org/wiki/Beam_splitter#Phase_shift]].