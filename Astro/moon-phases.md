# Algorithm to calculate the phase of the Moon
* Moon age: Number between 0 and 30=0 (recall that a lunation is 29.52 days); meaning:
 
| Moon Phase        | Day Numb. (rounded) | Day Numb. |
| :---              |     ---:            |      ---: |
| New Moon          | 0                   | 0         |
| First Quarter Moon| 7                   | 7.38      |
| Full Moon         | 15                  | 14.76     |
| Last Quarter Moon | 22                  | 22.14     |
| New Moon          | 30                  | 29.52     |

* Calculate the moon age from a date YYYY-MM-DD
* Algorithm (simplified version of an algorithm by John Conway)
  1. Year YY
    * This algorithm is valid for years 2000 to 2018 (from 2000-01-01 to 2018-12-31)
      * If outside those years, add or subtract repeatedly 19 years till the year is in the range  2000 to 2018 (this uses the Metonic Cycle of 19 years)
    * Take the last two places of the year and add 2 (you can think of this as adding the 4 digits such that the last two are considered together)
    * Multiply by 11
    * Subtract repeatedly 30 till the number is between 0 and 29
  2. Month MM
    * Add the number of the month (a number between 1 and 12; if the month is January or February; add additionally +1)
  3. Day DD
    * Add the number of the day
  4. Result
    * Subtract repeatedly 30 till the number is between 0 and 29
    * The result is the moon age (with a maximum error of +/- 2 days)

* Examples
  1. 2000-01-06
    * (2+00)*11=22
    * 22+1+1=24
    * 24+6=30
    * Moon Day=0 (New Moon)
  2. 2022-09-10
    * 2022-19=2003
    * (2+3)*11=55
    * 55-30=25
    * 25+9=34
    * 34-30=4
    * 4+10=14
    * Moon Day=14 (~Full Moon)  
