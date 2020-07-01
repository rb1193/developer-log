# Algorithm Analysis

## Power Laws

Most algorithm's (except logarithmic) running times can be computed as follows: `T(N) = a * N ^ b`

`b` can be obtained by calculating the increase in `T(N)` for large valuse of `N`.

e.g. for the table below, we can see that the value of b is 3:

| N    | T(seconds) | ratio | lg(ratio) |
| ---  | ---        | ---   | ---       |
| 1000 | 0.1        |       |           |
| 2000 | 0.8        | 7.7   | 2.9       |
| 4000 | 6.4        | 8     | 3         |
| 8000 | 51.2       | 8     | 3         |

So we can calculate the constant `a` from that.

## Algorithm Classification Notation

There are four main classifications of algorithm running time:

- Tilde - approx running time
- Big Theta - optimal running time (often unknown for hard problems)
- Big O - worst case running time
- Big Omega - best case running time

e.g. binary search has a best case of Omega(1), but a worst and optimal case of log(N).
