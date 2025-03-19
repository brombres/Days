# Days
Command line utility to compute dates and intervals.

About     | Current Release
----------|-----------------------
Version   | 3.1
Date      | March 19, 2025
Platforms | Windows, macOS, Linux

# Installation

1. Install [morlock](https://morlock.sh).
2. `morlock install brombres/days`

# Usage By Example

    Console> days
    Enter h or ? for help.

    > ?
    Days Calculator

    v3.0 - March 8, 2023 by Brom Bresenham

    USAGE
      days              # Interactive mode
      days <command>    # Runs computation and displays results


    COMMANDS
      <Date>                - Gives days since or until the given date.
      <Date> +/- <Interval> - Reports the computed date.
      <Date> - <Date>       - Gives elapsed number of days between the two dates.
      q                     - Quit

    DATE AND INTERVAL FORMATS
      January 1, 2020
      JAN 1 2020           # Case-insensitive month names
      1 jan 2020
      12.1.2020 / 2020.12.1
      12-1-2020 / 2020-12-1
      12/1/2020 / 2020/12/1
      12.1 / 12-1 / 12/1
      today / tomorrow / yesterday
      1 / 1d / 1 day / 2 days
      1w / 1 week / 2 weeks
      1m / 1 mo / 1 month / 2 months
      1y / 1 year / 2 years

    > today
    2020.05.25 | Monday, May 25, 2020

    > today + 2 weeks
    2020.06.08 | Monday, June 8, 2020

    > Dec 25
    214 days until Friday, December 25, 2020

    > q

    Console> days jan 31
    115 days since Friday, January 31, 2020

    Console> days jan 31 + 1m
    2020.02.29 | Saturday, February 29, 2020

    Console> days dec 31 - jan 1
    365 days

# Development Notes

1. *Days* was developed using the [Froley](https://github.com/brombres/Froley) parser generator.
2. `rogo --create --project=Days` was used to set up the project. The "main file", `Source/Days.rogue`, was then deleted so that Froley would generate a new parser wrapper in its place.
3. The [Days.froley](Source/Days.froley) tokenizer and parser definition file was copied from Froley's "Simple" example and modified.
4. The Froley compile command (to generate Rogue parser classes from `Days.froley`) was added to [Build.rogue](Build.rogue).
5. `rogo froley` generated most of the code in `Source/`.
6. An `evaluate()` method was manually added to the generated Cmd nodes in [CmdEval.rogue](Source/CmdEval.rogue).
7. [DaysValue.rogue](Source/DaysValue.rogue) and [Resolver.rogue](Source/Resolver.rogue) were manually added.
8. [Days.rogue](Source/Days.rogue) was modified to resolve the parsed input and print out appropriate results.

