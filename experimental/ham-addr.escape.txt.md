
## 5. Escaping *(OPTIONAL)* ##

***NOTE:*** *This section is a work-in-progress, and may be subject
to changes and adjustments which are incompatible with what is
described below*

This specification also defines an optional escaping mechanism for
compactly encoding special characters and indicator suffixes.

If a particular encoder or decoder supports escaping, the the escape
character may be used with one of the following values in order to
compactly encode the associated string:

 *  Characters
     *  ESC + `/` : `:` (Colon)
     *  ESC + `-` : `_` (Underscore)
     *  ESC + `D` : `.` (Dot)
     *  ESC + `V` : `|` (Pipe)
 *  Indicator Suffix
     *  ESC + `R` : Repeater Indicator, rendered as `/RPTR` or `/RPTR-`
     *  ESC + `P` : Portable Indicator, rendered as `/PORT` or `/PORT-`
     *  ESC + `M` : Mobile Indicator, rendered as `/MOBI` or `/MOBI-`
     *  ESC + `S` : Maritime Mobile Indicator, rendered as `/MARI` or
        `/MARI-`
     *  ESC + `A` : Aeronautical Mobile Indicator, `/AIRM` or `/AIRM-`
	 *  ESC + `C` : Contest Indicator, rendered as `/CTST` or `/CTST-`

All other escape pairings are currently undefined and should be
considered *reserved* for future use. If a decoder encounters an
unsupported escape code pair, it should render it literally as `^x`,
with `x` being the character value after the escape code.

Note that the above indicator suffix escape codes unambiguously refer
to the indicated description. In other words, `N6DRC^M` unambigously
means that N6DRC is operating from an automobile, without any
confusion as to if the address referrs to a Californian operating
under a reciprocal licence in England. (See FCC rule 97.119(c))

If there are additional characters present after an escape code pair
representing an indicator suffix, a dash (`-`) will be inserted
immediately after the rendered suffix.

The escape values for the Indicator Suffix patterns were specifically
chosen to make the unescaped versions of the callsigns humanly
readable.
