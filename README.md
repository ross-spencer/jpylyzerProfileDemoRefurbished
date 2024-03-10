# Schematron Demo: check if a JP2 file matches a technical profile

Johan's [original demo][original-1] refactored so it sits all in one place for
the user. Demo should work on all OSes based on the instructions below.

[original-1]: https://github.com/bitsgalore/jpylyzerProfileDemo

## About

Simple (demo shows use of [Jpylyzer][1] output and [Schematron][3] to check if
a JP2's properties match a user-defined profile.

## Contents

1. *balloon.jp2*, *balloon_eciRGB.jp2* - test images.
1. *balloon_jpylyzer.xml*, *balloon_eciRGB_jpylyzer.xml* - jpylyzer analysis of
the test images.
1. *demoAccessLossy.sch* - schematron file that represents a technical profile.
1. *probaton.jar* - 2014 implementation of schematron from probatron.org via
[archive.org][archive-1].

[archive-1]: https://web.archive.org/web/20131231062123/https://www.probatron.org/probatron4j.html

## How to use the demo

All of the components required to run this demo are found in this repository
so that the outcome of the demo can be observed without further configuration.

There are two demo images and assessments, and so the basic operation looks
as follows:

```sh
java -jar probatron.jar -r1 <jpylyzer_report_name> <schematron_schema>
```

This instructs java to run the probatron.jar executable with a jpylyzer report
with a given name and a schematon rules file (schema).

The flag `-r1` outputs verbose SVRL (schematron validation report language)
which is important for this information to remain usable over a longer period
of time as it describes when a rule has fired regardless of its result (success
or failure) as well as reporting when a rule has failed.

### balloon.jp2

```sh
java -jar probatron.jar -r1 balloon_jpylyzer.xml demoAccessLossy.sch
```

### balloon_eciRGB.jp2

```sh
java -jar probatron.jar -r1 balloon_eciRGB_jpylyzer.xml demoAccessLossy.sch > assessment.xml
```

## Image attribution

![http://commons.wikimedia.org/wiki/File:1783_balloonj.jpg](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/1783_balloonj.jpg/752px-1783_balloonj.jpg)

> 1786 description of the historic Montgolfier Brothers' 1783 balloon flight.
Illustration with engineering proportions and description.

Public Domain.

<!-- references -->

[1]: https://jpylyzer.openpreservation.org/
[3]: http://en.wikipedia.org/wiki/Schematron
