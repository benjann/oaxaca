# oaxaca
Stata module to compute the Blinder-Oaxaca decomposition

To install `oaxaca` from the SSC Archive, type

    . ssc install oaxaca, replace

To install `oaxaca` from GitHub, type

    . net install oaxaca, replace from(https://raw.githubusercontent.com/benjann/oaxaca/main/)

---

Main changes:

    18apr2023 (version 4.0.9)
    - total number of obervations reported by oaxaca when applied with option -svy-
      did not exclude observations with missing values on the analyzed variables; these
      observations were also not excluded from e(sample); this is fixed

    28feb2023 (version 4.0.8)
    - released on github
    - fixed display of header in Stata 17
