# PING docker
This branch of PING is setup to be run using Docker [https://www.docker.com/]

## Docker environment variables
CWD  # Set to local PING directory (default ~/PING)
RAW_FASTQ_DIR  # Set to sequence directory (default ~/PING/test_sequence/)
FASTQ_PATTERN  # use '_KIR_' to find already extracted files, otherwise use 'fastq' or whatever fits your data (default 'fastq')
THREADS  # set the number of threads for PING to use (default 4)
RESULTS_DIR  # Set the master results directory, all pipeline output will be recorded here (default '~/3_test_sequence_results/')
SHORTNAME_DELIM  # Set a delimiter to shorten sequence ID's, ID will be characters before delim, ID's must still be unique (default '_')
MIN_DP  # Set the minimum alignment depth for SNP calling (default 10)
HET_RATIO  # Set the heterozygous determination ratio (default 0.25)
SETUP_READBOOST  # Boolean variable to set whether to process cross-mapped reads during initial genotype determination (default T)
FINAL_READBOOST  # Boolean variable to set whether to process cross-mapped reads during final genotype determinatin (default F)
READBOOST_THRESH  # Integer variable to set the threshold to be used for cross-mapped read processing, higher value = more stringent processing (default 6)
COPY_FULLALIGN  # Boolean variable to set whether the full reference set is used for copy number determination (default T)
ALLELE_FULLALIGN  # Boolean variable to set whether the full reference set is used for intial genotype determination (default F)

## Docker run example using included sequence
In terminal, navigate to PING directory

`docker build --tag ping_docker:1.0 .`
( if permission denied message use `sudo` )

`docker run -e FASTQ_PATTERN='_KIR_' -e COPY_FULLALIGN=F ping_docker:1.0`
( if permission denied message use `sudo` )


Seeing the following message in the copy graphing module is normal:

'A line object has been specified, but lines is not in the mode
Adding lines to the mode...'
