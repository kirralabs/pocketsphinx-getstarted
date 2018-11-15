# pocketsphinx-getstarted
1. Get started to train new model with small data

1. This repository only contain small data to train new model. However you needs more data to perform well

# Init
I assume you have done the initial installation
1. pocketsphinx
1. sphinxtrain
1. sphinxbase

# How to run 
1. clone this repo:
```commandline
cd <your-path>
git clone https://github.com/kirralabs/pocketsphinx-getstarted.git other
```

example: (on Linux)
```commandline
cd /home/kirra/sphinx
git clone https://github.com/kirralabs/pocketsphinx-getstarted.git other
```

2. setting etc/sphinx_train.cfg
```commandline
# These are filled in at configuration time
$CFG_DB_NAME = "other";
# Experiment name, will be used to name model files and log files
$CFG_EXPTNAME = "$CFG_DB_NAME";

# Directory containing SphinxTrain binaries
$CFG_BASE_DIR = "<your-path>/other";

```

example: (on Linux)
```commandline
# These are filled in at configuration time
$CFG_DB_NAME = "other";
# Experiment name, will be used to name model files and log files
$CFG_EXPTNAME = "$CFG_DB_NAME";

# Directory containing SphinxTrain binaries
$CFG_BASE_DIR = "/home/kirra/sphinx/other";

```

3. go to root folder
```commandline
cd /home/kirra/sphinx/other
```

4. train model (on Linux)
```commandline
sphinxtrain run
```


# Change config from default (sphinx_train.cfg)
1. number of senons (optional)
```commandline
# Number of tied states (senones) to create in decision-tree clustering
$CFG_N_TIED_STATES = 8;
```

2. model to use
```commandline
# Models to use.
# $DEC_CFG_MODEL_NAME = "$CFG_EXPTNAME.cd_${CFG_DIRLABEL}_${CFG_N_TIED_STATES}";
$DEC_CFG_MODEL_NAME = "$CFG_EXPTNAME.ci_cont";
```

# Testing model
1. go to your root folder
```commandline
cd /home/kirra/sphinx/other
```

2. run testing
```commandline
sphinxtrain -s decode run
```

output:
```coSphinxtrain path: /usr/local/lib/sphinxtrain
Sphinxtrain binaries path: /usr/local/libexec/sphinxtrain
MODULE: DECODE Decoding using models previously trained
        Decoding 4 segments starting at 0 (part 1 of 1) 
        0% 
        Aligning results to find error rate
        SENTENCE ERROR: 0.0% (0/4)   WORD ERROR RATE: 0.0% (0/16)mmandline

```

# Transcript wav with new model 
1. run command
```commandline
pocketsphinx_continuous -hmm model_parameters/other.ci_cont/ -lm etc/other.lm.bin -dict etc/other.dic -infile wav/one.wav
```

output:
```commandline
INFO: pocketsphinx.c(152): Parsed model-specific feature parameters from model_parameters/other.ci_cont//feat.params
Current configuration:
[NAME]			[DEFLT]		[VALUE]
-agc			none		none
-agcthresh		2.0		2.000000e+00
-allphone				
-allphone_ci		yes		yes
-alpha			0.97		9.700000e-01
-ascale			20.0		2.000000e+01
-aw			1		1
-backtrace		no		no
-beam			1e-48		1.000000e-48
-bestpath		yes		yes
-bestpathlw		9.5		9.500000e+00
-ceplen			13		13
-cmn			live		batch
-cmninit		40,3,-1		40,3,-1
-compallsen		no		no
-dict					etc/other.dic
-dictcase		no		no
-dither			no		no
-doublebw		no		no
-ds			1		1
-fdict					
-feat			1s_c_d_dd	1s_c_d_dd
-featparams				
-fillprob		1e-8		1.000000e-08
-frate			100		100
-fsg					
-fsgusealtpron		yes		yes
-fsgusefiller		yes		yes
-fwdflat		yes		yes
-fwdflatbeam		1e-64		1.000000e-64
-fwdflatefwid		4		4
-fwdflatlw		8.5		8.500000e+00
-fwdflatsfwin		25		25
-fwdflatwbeam		7e-29		7.000000e-29
-fwdtree		yes		yes
-hmm					model_parameters/other.ci_cont/
-input_endian		little		little
-jsgf					
-keyphrase				
-kws					
-kws_delay		10		10
-kws_plp		1e-1		1.000000e-01
-kws_threshold		1e-30		1.000000e-30
-latsize		5000		5000
-lda					
-ldadim			0		0
-lifter			0		22
-lm					etc/other.lm.bin
-lmctl					
-lmname					
-logbase		1.0001		1.000100e+00
-logfn					
-logspec		no		no
-lowerf			133.33334	1.300000e+02
-lpbeam			1e-40		1.000000e-40
-lponlybeam		7e-29		7.000000e-29
-lw			6.5		6.500000e+00
-maxhmmpf		30000		30000
-maxwpf			-1		-1
-mdef					
-mean					
-mfclogdir				
-min_endfr		0		0
-mixw					
-mixwfloor		0.0000001	1.000000e-07
-mllr					
-mmap			yes		yes
-ncep			13		13
-nfft			512		512
-nfilt			40		25
-nwpen			1.0		1.000000e+00
-pbeam			1e-48		1.000000e-48
-pip			1.0		1.000000e+00
-pl_beam		1e-10		1.000000e-10
-pl_pbeam		1e-10		1.000000e-10
-pl_pip			1.0		1.000000e+00
-pl_weight		3.0		3.000000e+00
-pl_window		5		5
-rawlogdir				
-remove_dc		no		no
-remove_noise		yes		yes
-remove_silence		yes		yes
-round_filters		yes		yes
-samprate		16000		1.600000e+04
-seed			-1		-1
-sendump				
-senlogdir				
-senmgau				
-silprob		0.005		5.000000e-03
-smoothspec		no		no
-svspec					
-tmat					
-tmatfloor		0.0001		1.000000e-04
-topn			4		4
-topn_beam		0		0
-toprule				
-transform		legacy		dct
-unit_area		yes		yes
-upperf			6855.4976	6.800000e+03
-uw			1.0		1.000000e+00
-vad_postspeech		50		50
-vad_prespeech		20		20
-vad_startspeech	10		10
-vad_threshold		3.0		3.000000e+00
-var					
-varfloor		0.0001		1.000000e-04
-varnorm		no		no
-verbose		no		no
-warp_params				
-warp_type		inverse_linear	inverse_linear
-wbeam			7e-29		7.000000e-29
-wip			0.65		6.500000e-01
-wlen			0.025625	2.562500e-02

INFO: feat.c(715): Initializing feature stream to type: '1s_c_d_dd', ceplen=13, CMN='batch', VARNORM='no', AGC='none'
INFO: mdef.c(518): Reading model definition: model_parameters/other.ci_cont//mdef
INFO: bin_mdef.c(181): Allocating 84 * 8 bytes (0 KiB) for CD tree
INFO: tmat.c(149): Reading HMM transition probability matrices: model_parameters/other.ci_cont//transition_matrices
INFO: acmod.c(113): Attempting to use PTM computation module
INFO: ms_gauden.c(127): Reading mixture gaussian parameter: model_parameters/other.ci_cont//means
INFO: ms_gauden.c(242): 60 codebook, 1 feature, size: 
INFO: ms_gauden.c(244):  1x39
INFO: ms_gauden.c(127): Reading mixture gaussian parameter: model_parameters/other.ci_cont//variances
INFO: ms_gauden.c(242): 60 codebook, 1 feature, size: 
INFO: ms_gauden.c(244):  1x39
INFO: ms_gauden.c(304): 39 variance values floored
INFO: ptm_mgau.c(807): Number of codebooks doesn't match number of ciphones, doesn't look like PTM: 60 != 20
INFO: acmod.c(115): Attempting to use semi-continuous computation module
INFO: ms_gauden.c(127): Reading mixture gaussian parameter: model_parameters/other.ci_cont//means
INFO: ms_gauden.c(242): 60 codebook, 1 feature, size: 
INFO: ms_gauden.c(244):  1x39
INFO: ms_gauden.c(127): Reading mixture gaussian parameter: model_parameters/other.ci_cont//variances
INFO: ms_gauden.c(242): 60 codebook, 1 feature, size: 
INFO: ms_gauden.c(244):  1x39
INFO: ms_gauden.c(304): 39 variance values floored
INFO: acmod.c(117): Falling back to general multi-stream GMM computation
INFO: ms_gauden.c(127): Reading mixture gaussian parameter: model_parameters/other.ci_cont//means
INFO: ms_gauden.c(242): 60 codebook, 1 feature, size: 
INFO: ms_gauden.c(244):  1x39
INFO: ms_gauden.c(127): Reading mixture gaussian parameter: model_parameters/other.ci_cont//variances
INFO: ms_gauden.c(242): 60 codebook, 1 feature, size: 
INFO: ms_gauden.c(244):  1x39
INFO: ms_gauden.c(304): 39 variance values floored
INFO: ms_senone.c(149): Reading senone mixture weights: model_parameters/other.ci_cont//mixture_weights
INFO: ms_senone.c(200): Truncating senone logs3(pdf) values by 10 bits
INFO: ms_senone.c(207): Not transposing mixture weights in memory
INFO: ms_senone.c(268): Read mixture weights for 60 senones: 1 features x 1 codewords
INFO: ms_senone.c(320): Mapping senones to individual codebooks
INFO: ms_mgau.c(144): The value of topn: 4
WARN: "ms_mgau.c", line 148: -topn argument (4) invalid or > #density codewords (1); set to latter
INFO: phone_loop_search.c(114): State beam -225 Phone exit beam -225 Insertion penalty 0
INFO: dict.c(320): Allocating 4106 * 32 bytes (128 KiB) for word entries
INFO: dict.c(333): Reading main dictionary: etc/other.dic
INFO: dict.c(213): Dictionary size 7, allocated 0 KiB for strings, 0 KiB for phones
INFO: dict.c(336): 7 words read
INFO: dict.c(358): Reading filler dictionary: model_parameters/other.ci_cont//noisedict
INFO: dict.c(213): Dictionary size 10, allocated 0 KiB for strings, 0 KiB for phones
INFO: dict.c(361): 3 words read
INFO: dict2pid.c(396): Building PID tables for dictionary
INFO: dict2pid.c(406): Allocating 20^3 * 2 bytes (15 KiB) for word-initial triphones
INFO: dict2pid.c(132): Allocated 9760 bytes (9 KiB) for word-final triphones
INFO: dict2pid.c(196): Allocated 9760 bytes (9 KiB) for single-phone word triphones
INFO: ngram_model_trie.c(354): Trying to read LM in trie binary format
INFO: ngram_search_fwdtree.c(74): Initializing search tree
INFO: ngram_search_fwdtree.c(101): 7 unique initial diphones
INFO: ngram_search_fwdtree.c(186): Creating search channels
INFO: ngram_search_fwdtree.c(323): Max nonroot chan increased to 142
INFO: ngram_search_fwdtree.c(333): Created 7 root, 14 non-root channels, 3 single-phone words
INFO: ngram_search_fwdflat.c(157): fwdflat: min_ef_width = 4, max_sf_win = 25
INFO: continuous.c(307): pocketsphinx_continuous COMPILED ON: Dec 13 2017, AT: 14:49:57

INFO: cmn_live.c(120): Update from < 40.00  3.00 -1.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00 >
INFO: cmn_live.c(138): Update to   < 66.04 -3.88  8.58  3.03 -8.41  1.44  3.32  0.09  1.85 -3.52  8.11 -3.18 -1.55 >
INFO: ngram_search_fwdtree.c(1550):      330 words recognized (1/fr)
INFO: ngram_search_fwdtree.c(1552):     3261 senones evaluated (9/fr)
INFO: ngram_search_fwdtree.c(1556):     1136 channels searched (3/fr), 400 1st, 410 last
INFO: ngram_search_fwdtree.c(1559):      410 words for which last channels evaluated (1/fr)
INFO: ngram_search_fwdtree.c(1561):       24 candidate words for entering last phone (0/fr)
INFO: ngram_search_fwdtree.c(1564): fwdtree 0.01 CPU 0.002 xRT
INFO: ngram_search_fwdtree.c(1567): fwdtree 0.01 wall 0.002 xRT
INFO: ngram_search_fwdflat.c(302): Utterance vocabulary contains 4 words
INFO: ngram_search_fwdflat.c(948):      329 words recognized (1/fr)
INFO: ngram_search_fwdflat.c(950):     2406 senones evaluated (7/fr)
INFO: ngram_search_fwdflat.c(952):     1229 channels searched (3/fr)
INFO: ngram_search_fwdflat.c(954):     1001 words searched (2/fr)
INFO: ngram_search_fwdflat.c(957):      136 word transitions (0/fr)
INFO: ngram_search_fwdflat.c(960): fwdflat 0.00 CPU 0.000 xRT
INFO: ngram_search_fwdflat.c(963): fwdflat 0.00 wall 0.000 xRT
INFO: ngram_search.c(1250): lattice start node <s>.0 end node </s>.346
INFO: ngram_search.c(1276): Eliminated 0 nodes before end node
INFO: ngram_search.c(1381): Lattice has 24 nodes, 16 links
INFO: ps_lattice.c(1374): Bestpath score: -12109
INFO: ps_lattice.c(1378): Normalizer P(O) = alpha(</s>:346:352) = -637945
INFO: ps_lattice.c(1435): Joint P(O,S) = -640502 P(S|O) = -2557
INFO: ngram_search.c(872): bestpath 0.00 CPU 0.000 xRT
INFO: ngram_search.c(875): bestpath 0.00 wall 0.000 xRT
sentences on
INFO: cmn_live.c(120): Update from < 66.04 -3.88  8.58  3.03 -8.41  1.44  3.32  0.09  1.85 -3.52  8.11 -3.18 -1.55 >
INFO: cmn_live.c(138): Update to   < 66.04 -3.88  8.58  3.03 -8.41  1.44  3.32  0.09  1.85 -3.52  8.11 -3.18 -1.55 >
INFO: ngram_search_fwdflat.c(302): Utterance vocabulary contains 0 words
INFO: ngram_search_fwdtree.c(429): TOTAL fwdtree 0.01 CPU 0.002 xRT
INFO: ngram_search_fwdtree.c(432): TOTAL fwdtree 0.01 wall 0.002 xRT
INFO: ngram_search_fwdflat.c(176): TOTAL fwdflat 0.00 CPU 0.000 xRT
INFO: ngram_search_fwdflat.c(179): TOTAL fwdflat 0.00 wall 0.000 xRT
INFO: ngram_search.c(303): TOTAL bestpath 0.00 CPU 0.000 xRT
INFO: ngram_search.c(306): TOTAL bestpath 0.00 wall 0.000 xRT
```

2. the result is:
```commandline
sentences on
```

this model still not accurate, you need put more data to get high accuracy

# Models
You can use the pretain model that i have trained in "sample-output-trainnewmodel.zip".