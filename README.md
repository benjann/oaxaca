# oaxaca
Stata module to compute the Blinder-Oaxaca decomposition

To install `oaxaca` from the SSC Archive, type

    . ssc install oaxaca, replace

To install `oaxaca` from GitHub, type

    . net install oaxaca, replace from(https://raw.githubusercontent.com/benjann/oaxaca/main/)

---

Main changes:

    24apr2023 (version 4.1.1)
    - various improvements of how the estimation sample and associated information
      is handled
      o if option -svy- is applied, information such as e(N_pop), e(N_psu), etc. is
        now also returned and displayed if -suest- or -nose- is specified;
        observations with zero weights are now consistently counted
        in e(N), e(N_1) and e(N_2); number of groups in by() is checked after
        restricting the sample by subopop(), if specified
      o if selection models are applied, the full estimation sample including
        observations from the first stage is now available to the pooled model
        and is retuned in e(sample); e(N), e(N_1) and e(N_2) refer to full sample
        sizes; selected sample sizes are returned in e(N_1_selected) and
        e(N_2_selected) (and reported in display)
      o in case of fweights, e(N), e(N_1) and e(N_2) are now report sum of weights
      o consistency check applied by normalize() no longer fails if there are
        missing values on some X (which can happen if there are observations with
        a weight of zero)
    - improved computational efficiency of change introduced in version 4.1.0
    - a legend documenting the definitions of the decomposition terms is now
      displayed in the table header; type -nodefinitions- to suppress
    - options -noheader- and -notable- are now supported
    - if -eform- is specified, renaming of _cons for display is now only applied 
      in Stata 11 or earlier
    - e(cmdline) is now returned
    - e(k_eq) and e(k_eform) are now returned
    - in Stata 11 or newer, standard display option such as -coeflegend- or
      -cformat()- are now supported
    - svy option now supports all vcetypes
    - now always using own display routine, i.e., also in case of vce(bootstrap), 
      vce(jackknife), or svy with vcetype other than linearized

    18apr2023 (version 4.1.0)
    - further improved identification of estimation sample in case of -svy-; a
      consistent set of observations is now used across models even if there are
      missings; point estimates are not affected by the change but SEs may be
      slightly different from previous version if some of the variables contain
      missings

    18apr2023 (version 4.0.9)
    - total number of obervations reported by oaxaca when applied with option -svy-
      did not exclude observations with missing values on the analyzed variables; these
      observations were also not excluded from e(sample); this is fixed

    28feb2023 (version 4.0.8)
    - released on github
    - fixed display of header in Stata 17
