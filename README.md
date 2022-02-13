# Strawberry Fields Experiments
In this repository is some work that was done in experimenting with Strawberry Fields
to see its behaviour in particular contexts. 
Hopefully, this can be useful in the future as a starting point for code that already
does something known and potentially useful.

The most useful jupyter notebook here is probably `Homodyne, heterodyne integrity.ipynb`
where I performed heterodyne and homodyne measurements using the built-in classes from
Strawberry Fields as well as heterodyne detection "from scratch" using x- and y- built-in
homodyne measurement classes. These heterodyne and homodyne detection methods were based on
work [done at a hackathon](https://github.com/CDL-Quantum/Hackathon2021/tree/main/The%20Sensors),
from which it seemed that there were certain bugs with the Bosonic backend as well as 
quirks in the behaviour of the built-in heterodyne detection method.

## Results:
Something I found rather shocking was that after initializing a state with some amplitude
$a$, and performing homodyne measurement, the x-value in the case of a phase of 0 was measured to be $2a$. 

The explanation I found for this was as follows:
For amplitude $a$, phase $\phi$, and position and momentum quadratures $x$ and $p$,
$$ae^{i\phi} = \frac{1}{\sqrt{2\hbar}}(x+ip)$$
but **Strawberry Fields defines** $\hbar = 2$. This means that, in the case of $\phi=0$
$$a = \frac{x}{2}$$
which is consistent with observation.

Two bugs were observed from the aforementioned hackathon:
* The bosonic backend had to be run twice each time
* When heterodyne measurement was performed "manually" (by applying a beamsplitter and measuring the resulting states)
the measurements did not agree

I tested for both of these issues and was not able to reproduce them.
Either this issue was some consequence of a mistake in the program written for the hackathon,
or it was a bug in the Strawberry Fields library that was present in the version used for the
hackathon but has been resolved since in the version that I used for this project.
If either of the above issues recurs, my code can be a way to see whether it is
a problem in the library iteslf or the usage thereof.

