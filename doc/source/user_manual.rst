.. _user_manual:


***********
User Manuel
***********


Installation
************

::

    pip install ncbi-genome-download

Alternatively, clone the GitHub repository, then run (in a python virtual environment)::

    pip install .

If this fails on older versions of Python, try updating your pip tool first:::

    pip install --upgrade pip

and then rerun the ncbi-genome-download install.

`ncbi-genome-download` is only developed and tested on `Python` releases still under active support by the Python project.
At the moment, this means versions `2.7`, `3.3`, `3.4`, `3.5` and `3.6`.
Specifically, no attempt at testing under `Python` versions older than `2.7` or `3.3` is being made.

If your system is stuck on an older version of `Python`, consider using a tool like `Homebrew` or
`Linuxbrew` to obtain a more up-to-date version.


Usage
*****

To download all bacterial RefSeq genomes in GenBank format from NCBI, run the following: ::

    ncbi-genome-download bacteria

If you're on a reasonably fast connection, you might want to try running multiple downloads in parallel: ::

    ncbi-genome-download bacteria --parallel 4

To download all fungal GenBank genomes from NCBI in GenBank format, run: ::

    ncbi-genome-download --section genbank fungi

To download all viral RefSeq genomes in FASTA format, run: ::

    ncbi-genome-download --format fasta viral

To download only completed bacterial RefSeq genomes in GenBank format, run: ::

    ncbi-genome-download --assembly-level complete bacteria

To download bacterial RefSeq genomes of the genus Streptomyces, run: ::

    ncbi-genome-download --genus Streptomyces bacteria

.. note::
    This is a simple string match on the organism name provided by NCBI only.

You can also use this with a slight trick to download genomes of a certain species as well: ::

    ncbi-genome-download --genus "Streptomyces coelicolor" bacteria

.. warning::
    The quotes are important. Again, this is a simple string match on the organism name provided by the NCBI.

To download bacterial RefSeq genomes based on their NCBI species taxonomy ID, run: ::

    ncbi-genome-download --species-taxid 562 bacteria

.. note::
    The above command will download all RefSeq genomes belonging to Escherichia coli.

To download a specific bacterial RefSeq genomes based on its NCBI taxonomy ID, run: ::

    ncbi-genome-download --taxid 511145 bacteria

.. note::
    The above command will download the RefSeq genome belonging to Escherichia coli str. K-12 substr. MG1655.

It is possible to also create a human-readable directory structure in parallel to mirroring the layout used by NCBI::

    ncbi-genome-download --human-readable bacteria

This will use links to point to the appropriate files in the NCBI directory structure,
so it saves file space. Note that links are not supported on some Windows file systems and some older versions of Windows.

To get an overview of all options, run: ::

    ncbi-genome-download --help

License
*******

All code is available under the `Apache License version 2`, see the `LICENSE` file for details.