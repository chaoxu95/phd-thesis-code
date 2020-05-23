##############################################################################
#       Author: Chao XU
#       Date: 2019-07-07
#       Affiliation: Peking University, TU Dresden
#       Function: Translate the eligibility criterion into formal query
##############################################################################

The list of program files：
------------------------------------------------------------------------------------
1. preparation.py: preprocessing of input eligibility criterion
2. criteria2label.py: get the semantic representation of eligibility criterion
3. labeled2formal.py: get the formal expressions from semantic representation
4. intermediate.py: For the medical concepts, generate the formal expressions.
5. load_file.py: load the parameter file to program
6. similarity_word2vec.py: similarity computing
7. stanford_nlp.py: get the parse tree of sentence
8. baseline.py: batch process the eligibility criteria and get the formal queries.
------------------------------------------------------------------------------------

The list of parameter files: in the param directory
------------------------------------------------------------------------------------
1. age_pattern: regular expressions used to recognize age expressions
2. time_pattern: regular expressions used to recognize temporal expressions
3. concept_scope: restrict the scope of concepts that need to be recognized
4. filter_keywords: Being used to filter out the useless eligibility criteria
5. mapping_output: the output of metamap tagger
6. criterions.xml: The input file including eligibility criterion
------------------------------------------------------------------------------------

The list of output files: in the output directory
------------------------------------------------------------------------------------
1. formal_text: : output the criteria, semantic representation, and final formal query.
2. log.txt: output more detailed information including age expressions, time expressions,
metamap tagger output, refined matamap tagger output, and semantic representation
3. formal_queries.xml: the final output of our program.
------------------------------------------------------------------------------------

The list of paper data files: the input and output files of the test in our paper
------------------------------------------------------------------------------------
1. input files: criterions.xml
2. output files: mapping_output, formal.txt, log.txt, formal_queries.xml
------------------------------------------------------------------------------------

The configuration of web service:
************************************************************************************
1. metamap tagger service：get the output of metamap tagger
2. superclasses service: get all superclasses of concept
3. synset service: get synset of concept
************************************************************************************


Follow the following instructions to run the program:
************************************************************************************
1. Download Stanford Core NLP and put it in some directory. Go to stanford_nlp.py, change ini_path = "/stanford/jars" to your own path.
2. Start Stanford NLP service
3. Download Pretrained word2vec, and go to baseline.py and change "model = KeyedVectors.load_word2vec_format('/word2vec/wiki.en.vec')" to your own path.
4. In criteria2label.py, go to get_all_superclasses and get_synset_of_concept functions and change the url address to your own.
5. In preparation.py, go to get_mapping_from_criterion function and change the url address to your own.
6. Run the preparation.py to get the metampa tagger output, and the metamap tagger output will be written in param/mapping_output
7. Run the baseline.py to get the formal queries.
************************************************************************************

Tips:
The running of baseline.py is independent of preparation.py, the main function of preparation.py is to get the output of metamap tagger.
The output of metamap tagger has been written in file /param/metamap tagger, so you could run the program without installing Metamap tagger service.
But the synset service and superclass service are necessary.
Before run it, please keep the file "mapping_out" in the param directory.
