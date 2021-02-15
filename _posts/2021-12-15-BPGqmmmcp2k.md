---
title: 'Best Practice Guide for Biomolecular QM/MM simulations with CP2K'
date: 2021-12-15
permalink: /posts/2021/12/BPGqmmmcp2k/
tags:
  - qmmm
  - CP2K
  - BPG
---

As part of my work in the BioExcel-2 project at the EPCC, I co-wrote a best practice guide on how to perform QM/MM simulations of biomolecules using CP2K. We provided an overview of the main steps in setting up and running a QM/MM simulation in CP2K. We cover steps starting from preparing your system to running a production QM/MM run. This BPG is designed to be read from the point of view of beginner users. 

A Best Practice Guide for Biomolecular QM/MM simulations with CP2K for beginners
----------

Here is the link: 
[Best Practice Guide for Biomolecular QM/MM simulations with CP2K](https://docs.bioexcel.eu/qmmm_bpg/en/main/)

**Authors:** [Dr Holly Judge](https://www.epcc.ed.ac.uk/about/staff/holly-judge), **Dr Salome Llabres** and [Dr Arno Proeme](https://www.epcc.ed.ac.uk/about/staff/dr-arno-proeme)


A set of tools to set up simulations in QM/MM using CP2K
----------

Also, I developed a set of python3 tools to deal with the set up of CP2K simulations. 

Here you have the link to the [Bioexcel repository](https://github.com/bioexcel/CP2K_qmmm_input_preparation_scripts)

This repository contains the following scripts:

**cp2krestart2gromacs.py**

This script converts CP2K restart file to GROMACS files. It needs parmed. 

```bash
$ python3 cp2krestart2gromacs.py -h 

Usage: cp2krestart2gromacs [options] infile outfile

Converts CP2K restart file to GROMACS format (including velocities).

positional arguments:
  infile          CP2K restart file
  outfile         basename for gromacs files

optional arguments:
  -h, --help  show this help message and exit
  -v          show program's version number and exit
```

**cp2kinput2ndxformat.py**

This script collects atom indexes outlined in the QM region and link atoms of a CP2K input file and writes a GROMACS NDX file for each QM region and for Link atoms.

```bash
$ python3 cp2kinput2ndxformat.py -h 

Usage: cp2kinput2ndxformat.py [options] cp2kinputfile

writes a &QM_KIND section of CP2K given a PDB file

positional arguments:
  inp         The CP2K input file to process

optional arguments:
  -h, --help  show this help message and exit
  -v          show program's version number and exit
```

**get_qm_kind.py**

This script reads a PDB containing the QM region and writes the atom indexes in the CP2K input format.

```bash
$ python3 get_qm_kind.py -h 

Usage: get_qm_kind.py [options] pdbfile

writes a &QM_KIND section of CP2K given a PDB file

positional arguments:
  pdb         The pdb to process

optional arguments:
  -h, --help  show this help message and exit
  -v          show program's version number and exit
```

I hope you find them useful!

