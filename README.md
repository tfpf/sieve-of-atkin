* A. O. L. Atkin and D. J. Bernstein, "Prime Sieves Using Binary Quadratic Forms", in Mathematics of Computation,
  vol. 73, no. 246, pp. 1023–1030.
* D. J. Bernstein, [primegen 0.97](http://cr.yp.to/primegen.html).

# Sieve of Atkin

A fast prime generator. I have implemented the technique described by Atkin and Bernstein (as opposed to brute-forcing
quadratic congruences). While Bernstein has already provided an optimised implementation, I found the code very hard to
understand, and it does not store the list of primes, so I decided to write it myself.

Also included here is a wheel-factorised sieve of Eratosthenes implementation which proceeds mostly along the same
lines as the sieve of Atkin.

[![style](https://github.com/tfpf/sieve-of-atkin/actions/workflows/style.yml/badge.svg)](https://github.com/tfpf/sieve-of-atkin/actions/workflows/style.yml)
[![tests](https://github.com/tfpf/sieve-of-atkin/actions/workflows/tests.yml/badge.svg)](https://github.com/tfpf/sieve-of-atkin/actions/workflows/tests.yml)

## Implementation Notes

Both sieves start generating primes from 7 onwards. The first three primes (i.e. 2, 3 and 5) must be handled
separately.

## Performance

The sieve of Atkin is faster than the sieve of Eratosthenes. Tabulated below are the times taken (to two significant
figures) to construct the sieves up to _n_ on my machine. Note that the time taken to iterate over the primes (after
constructing the sieves) will, in theory, be identical for a given _n_ because the two sieves store the list of primes
in the same manner.

|_n_|Eratosthenes|Atkin|
|-:|-:|-:|
|2<sup>16</sup>|0 ms|0 ms|
|2<sup>17</sup>|0 ms|0 ms|
|2<sup>18</sup>|1 ms|0 ms|
|2<sup>19</sup>|2 ms|0 ms|
|2<sup>20</sup>|4 ms|0 ms|
|2<sup>21</sup>|7 ms|1 ms|
|2<sup>22</sup>|16 ms|3 ms|
|2<sup>23</sup>|32 ms|6 ms|
|2<sup>24</sup>|69 ms|11 ms|
|2<sup>25</sup>|140 ms|25 ms|
|2<sup>26</sup>|300 ms|50 ms|
|2<sup>27</sup>|680 ms|210 ms|
|2<sup>28</sup>|1800 ms|560 ms|
|2<sup>29</sup>|3900 ms|1400 ms|
|2<sup>30</sup>|8700 ms|3000 ms|

## Related

I rewrote this sieve of Atkin implementation in Rust to augment
[my Project Euler solutions](https://github.com/tfpf/project-euler) library.
