# snakemake-parallel-test

This repo contains a **non-working** example of an attempt to parallelize parts
of a SnakeMake [pipeline](workflow/Snakefile). The intention is the following:

1. a rule `first_rule` with one input and one output
2. a rule `second_rule` that takes the output from `first_rule` as input and, in turn,
   produces a directory full of files as output
3. a rule `third_rule` in which the files in the output of 2. are processed, one at a 
   time, by a script that is run in parallel as many times as specified by the `-j 4`
   parameter. That script produces one output for its input.
4. a rule `fourth_rule` that continues with the output from 3, and which also invokes 
   a script that takes one input and produces one output, again in parallel
5. a rule `final_rule` that is invoked after rule 4. that takes the directory as input
   and that aggregates all outputs in that directory in a single operation, i.e. not
   parallel.
