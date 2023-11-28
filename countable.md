# Counting the Continued Fractions

## Brief Introduction
* The intended direction taken here is to provide a quick sanity check (a "peered preview" if you will).<br>
* It is deliberately kept terse, in order to focus on potential problems.<br>
* Explanations and examples need to be improved and expanded upon, feedback for which parts being appreciated.

## Observations Which Summarize How
* Cantor's Diagonal Argument does not factor in the Base of the Real Numbers or the Decimal Points.
* Continued Fractions (with caveats) uniquely map the Real Numbers into a sequence of Integers `> 0`.
* A sequence of Integers `> 0` can be counted into a single Integer `> 0`
* A simplistic example would be counting base 10s into base 11, using the extra digit to represent both the separator, and +1 to the count.

## Prior Proofs Built Off Of
### Continued Fractions Can Count the Real Numbers
In order for there to be a unique mapping, a finite Continued Fraction requires the final Integer to be `> 1`.

* A common syntax Continued Fractions are written in is:<br>
  `a; b, ..., y, z`

Where:<br>
`a;` is an Integer<br>
`b, ..., y,` are each Integers `> 0`<br>
`z` is an Integer `> 1`<br>

### Integer Mappings to an Integer `> 0`
`a;` maps to:<br>
 0 ->   (special case, see "Putting It Together" below)<br>
+1 -`> 1`<br>
-1 -> 2<br>
+2 -> 3<br>
-2 -> 4<br>
+3 -> 5<br>
-3 -> 6<br>
  ...<br>
+n ->  2n -1 => 2n -1<br>
-n -> -2(-n) => 2n<br>

`z` maps to:<br>
2 -`> 1`<br>
3 -> 2<br>
4 -> 3<br>
 ...<br>
n -> n-1<br>

Therefore:<br>
Before: `a;` and `z` were special cases<br>
After:  `a; b, ..., y, z` each map to an Integer `> 0`<br>
Remaing case where `a;` is `0;` handled below.

## Mapping an Integer `> 0` into Base 10
An Integer ``> 0`` can be mapped into Base `> 1` according to the following:<br>
| Integer ``> 0``        | Base 2     | Base 3     | Base 4     | Base 5     |
| ------             | -----      | -----      | -----      | -----      |
| 1                  | 1          | 2          | 3          | 4          |
| 2                  | 10         | 20         | 30         | 40         |
| 3                  | 100        | 21         | 31         | 41         |
| 4                  | 1000       | 200        | 32         | 42         |
| 5                  | 10000      | 201        | 300        | 43         |
| 6                  | 100000     | 210        | 301        | 400        |
| ...                | ...        | ...        | ...        | ...        |

The largest digit in a base is the most significant digit and only occurs once.

## Putting It Together
* Numbers are read from right to left, so that the largest digit counts the top of each Integer.
* They occur in the same order `a; b, ..., y, z` occurs in.
* When `a;` is read, if the most significant digit is the largest digit, then it counts `0; b,` otherwise it counts `a;`

Base 2 currently requires a workaround of subtracting 1 from the final Integer, and may still have issues. The other Bases work correctly, but handle the case where a; is 0; differently then base 2 does, as they have more digits available.

### Incomplete Listing of Example Mappings
| Integers `> 0`     | Base 2 (-1 to) | Base 3     | Base 4     | Base 5     |
| ------           | -----          | -----      | -----      | -----      |
| 1                | 10 -1          | 1          | 1          | 1          |
| 2                | 100 -1         | 10         | 2          | 2          |
| 3                | 1000 -1        | 11         | 10         | 3          |
| 0 1              |  11 -1         |  2         |  3         |  4         |
| 0 2              |  110 -1        |  20        |  30        |  40        |
| 0 1 1            |  111 -1        |  22        |  33        |  44        |
| 0 3 2            |  110010 -1     |  2120      |  3130      |  4140      |
| 1 1              | 101 -1         | 12         | 13         | 14         |
| 1 1 1            | 1011 -1        | 122        | 133        | 144        |
| 2 1 1            | 10011 -1       | 1022       | 233        | 244        |
| 2 1 1 1          | 100111 -1      | 10222      | 2333       | 2444       |
| 1 2 3 4          | 10101001000 -1 | 12021200   | 1303132    | 1404142    |
| 4 3 2 1          | 10000100101 -1 | 10021202   | 1131303    | 10241404   |

Well this can be explained/shown better, the above is able to represent all possible lists of Integers `> 0`.

A more direct way to explain this can be seen by the special case of how Base 3 encodes a Base 2 number:<br>
* The leading 2 can be read as the leading 1 of a Base 2 number, as all Base 2 numbers `> 0` lead with a 1.
* The remaining base 3 numbers that don't lead with a 2, map to the case where `a;` is `> 0`, well the above counts the cases where `a;` is 0.
* Each 2 digit now acts as both the separator digit and the leading 1 of a base 2 number, counting a list of base 2 Integers `> 0`.

### Reverse Mapping Example from Base 3 to List of Base 2's
| Base 3 |  Base 2's       |
| ------ | --------------  |
| 1      |   1             |
| 2      |   0;   1        |
| 10     |  10             |
| 11     |  11             |
| 12     |   1;   1        |
| 20     |   0;  10        |
| 21     |   0;  11        |
| 22     |   0;   1,  1    |
| 100    | 100             |
| 101    | 101             |
| 102    |  10;   1        |
| 110    | 110             |
| 111    | 111             |
| 112    |  11;   1        |
| 120    |   1;  10        |
| 121    |   1;  11        |
| 122    |   1;   1,  1    |
| 200    |   0; 100        |
| 201    |   0; 101        |
| 202    |   0;  10,  1    |
| 210    |   0; 110        |
| 211    |   0; 111        |
| 212    |   0;  11,  1    |
| 220    |   0;   1, 10    |
| 221    |   0;   1, 11    |
| 222    |   0;   1,  1, 1 |
