1. create repo using template. note, the .test data will not be cloned.
2. get test data(reads and refs) separately from submodule: https://github.com/snakemake-workflows/ngs-test-data.git
3. create a new file in envs folder, envionment.yaml, for install conda virtual env. Include required softwares like
snakemake, samtools, picard tools, pandas softwares, in order to run snakemake and create index and dict for reference.
- samtools faidx genome.chr21.fa
- bwa index genome.chr21.fa
- java -jar picard.jar CreateSequenceDictionary REFERENCE=genome.chr21.fa OUTPUT=rgenome.chr21.dict
4.run :
snakemake --dag | dot -Tpdf > dag.pdf
snakemake --use-conda --cores 4 ; snakemake --report report.html

possible error if not enough memory:
`OpenJDK 64-Bit Server VM warning: INFO: os::commit_memory(0x0000000729200000, 844103680, 0) failed; error='Not enough space`
