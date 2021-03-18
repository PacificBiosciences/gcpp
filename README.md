<h1 align="center">GCpp</h1>
<p align="center">Generate Highly Accurate Reference Contigs</p>

***

_gcpp_ takes an alignment in the form of a BAM file and polishes the references
with the provided subreads from the alignment. It uses the Arrow algorithm in
multi-molecule consensus setting and can reach up to QV60 at coverage 100. GCpp
is the machine-code successor of the venerable ``GenomicConsensus`` suite which
has reached EOL. Command-line parameters are the same as for
``GenomicConsensus``, with the exception of not supporting ``Quiver``/RSII
anymore.

## Availability
The latest `gcpp` can be installed via the bioconda package `pbgcpp`.

Please refer to our [official pbbioconda page](https://github.com/PacificBiosciences/pbbioconda)
for information on Installation, Support, License, Copyright, and Disclaimer.

## Latest Version
Version **2.0.2**: [Full changelog here](#changelog)

## Execution
**Input**: Aligned subreads in PacBio BAM format (`.bam`).

**Output**: Polished contigs in `.fasta` or `.fastq` format.

## FAQ

### Why am I getting "Missing valid chemistry from input file, is this a proper PBBAM input file?"

You have likely aligned a FASTQ/FASTA file or a BAM file that yielded an
invalid PBBAM file. A PBBAM file is a BAM with additional metadata. You cannot,
in general, align FASTQ files and produce valid PBBAMs. We recommend you align
the `.subreads.bam` or `.subreadset.xml` file using
[pbmm2](https://github.com/PacificBiosciences/pbmm2) which produces valid
PBBAMs.

## Licenses
PacBio® tool _gcpp_, distributed via Bioconda, is licensed under
[BSD-3-Clause-Clear](https://spdx.org/licenses/BSD-3-Clause-Clear.html)

## Changelog

 * 2.0.2:
   * Require FAI index upfront when passing the `-w` argument. This would lead to rare crashes when users did not have FAI files present.
 * 2.0.1:
   * Fixed a buffer overflow in Arrow that could lead to segfaults in rare cases.
 * 2.0.0:
   * SMRT Link v10.0 release candidate
 * 1.0.0:
   * SMRT Link v8.0 release candidate
   * Only perform QV computation when required (`.fasta`-only output will skip QV computation)
   * Allow 0-byte input references
   * Logs limited to at most 1000 lines per contig
   * Improved UX for invalid BAM inputs
   * Do not require PB Index, only BAI
 * 0.0.1
   * Released with SMRT Link v7.0
   * First commercial release

## DISCLAIMER
THIS WEBSITE AND CONTENT AND ALL SITE-RELATED SERVICES, INCLUDING ANY DATA, ARE PROVIDED "AS IS," WITH ALL FAULTS, WITH NO REPRESENTATIONS OR WARRANTIES OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, ANY WARRANTIES OF MERCHANTABILITY, SATISFACTORY QUALITY, NON-INFRINGEMENT OR FITNESS FOR A PARTICULAR PURPOSE. YOU ASSUME TOTAL RESPONSIBILITY AND RISK FOR YOUR USE OF THIS SITE, ALL SITE-RELATED SERVICES, AND ANY THIRD PARTY WEBSITES OR APPLICATIONS. NO ORAL OR WRITTEN INFORMATION OR ADVICE SHALL CREATE A WARRANTY OF ANY KIND. ANY REFERENCES TO SPECIFIC PRODUCTS OR SERVICES ON THE WEBSITES DO NOT CONSTITUTE OR IMPLY A RECOMMENDATION OR ENDORSEMENT BY PACIFIC BIOSCIENCES.
