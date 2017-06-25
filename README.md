# eviiom

eviiom, canonically pronounced "ev-ee-ome", constructs a BIOM table of evidence of feature associations from two input BIOM tables. 

To construct the evidence matrix, eviiom evalutes each pair of observations between the two tables (the "left" and "right" tables). If both observations are found to exist in the same sample, evidence for an association is incremented (i.e., positive evidence). If a left observation is found without a right observation, under the constraint that a positive association had been found, evidence for the pair is decremented (i.e., contradictory evidence).

# Installation

A formal `setup.py` is not available yet. To install:

    $ git clone https://github.com/biocore/eviiom.git
    $ cd eviiom
    $ export PYTHONPATH=`pwd`:$PYTHONPATH
    $ python eviiom/drive.py blend --help
    Usage: drive.py blend [OPTIONS]

    Options:
      --left-table PATH       A BIOM table  [required]
      --right-table PATH      A BIOM table  [required]
      --threads INTEGER
      --min-overlap INTEGER   The minimum number of supporting samples overlapping
      --output PATH           [required]
      --left-as-observations  Set the observation IDs in the left table as the
                              observation IDs in the resulting table
      --help                  Show this message and exit.

# Dependencies

eviiom requires `numpy`, `click`, `biom >= 2.1.6` (with `h5py`), and `joblib`. Version requirements noted where known. 

# Use

The samples axis must be in common between both tables in terms of the IDs represented (order does not matter). The two input tables are described as "left" and "right." The values within the "left" table are used to increment and decrement evidence. The observation axis of the output table can be controlled at runtime so it is relative to either the left or the right tables.
