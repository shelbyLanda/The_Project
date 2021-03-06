# The_Project
Bio-497 environmental genomics class project: Shelby and Jon

__Quick notes__ I finished the outline. It needs some work though. Some of the structure doesn't work because the data format of a fasta is very different from jplace. I am not sure how to translate from parsing two different strings to parsing a nested dictionary and a string containing way too many strange characters. I think it would be good to sit down infront of a whiteboard and diagram the shit out of it. That and talk to an expert such as a prof or Eric.  I am going to begin work on the coding. O.O watch me run into a brick wall now :P 

### To do list

__Shelby__
* [X] What numbers in the jplace file correspond to fields? tree and placements
* [X] what is named multiplicity? corresponds to the "nm" value in the jplace file
  * If you scroll down to "multiplicity" it talks about what it is. I am finding the documentation about guppy is helpful in general too. http://matsen.github.io/pplacer/generated_rst/guppy.html#id8
* [X] Ask Robin/Ryan about duplicate/overlapping sequences in nm key
  * deduping is for amplicon data. 
* [ ] draw a small tree and make a small jplace file and show how they correspond to eachother.
* [ ] Figure how to tell if placement on the tip vs internal 
* [ ] email Filip about python

__Jon__
* [X] what are the values that corresponde to the reference tree numbers
  *  jplace.fields will tell you what each field is
* [ ] How to find leaves in the tree section of the jplace file
  * Opposing "()" denotes a tree leaf  
* [ ] write class and methods for parsing Newick/jplace tree 
* [X] look for figures to use. figure for jplace file, fat tree with placement labels, example of python code
* [ ] write class and methods for parsing placements 

### Project proposal paper:


- __Introduction__
  - Background: talk metagenomics -> phylogenetic trees -> pipeline -> pplacer and fat trees
  - Questions/state of the field: No easy way to extract data. 
  - Primary goals: Write a script to extract a variety of data from jplace
  - Hypothesis: We will write a fucking mind blowing script null: it won't be fucking mind blowing or....analysis of internal vs leaves will alter tree interpretation.
- __Methods__
  - Data type: jplace file/json
  * Annotation pipeline: phylosift
  * Statistics: summary statistics 
     *We should probably ask what sort of stats we will be doing. She will probably have a better idea that my vaguery  
  * Software packages: phylosift
- __Expected Outcomes__
  * What we expect to find: Fucking awesome script. extrapolate on how abundance data will influence interpretation
  * Mock figures: Psuedo code, concept map, phylogenetic fat tree vs normal tree 
- __References__
  * Ten references: uuhhhh

### Resources

__Online Arhaeoptryx example__ 
http://matsen.fredhutch.org/pplacer/demo/p4z1r36.html

__Papers__
Some papers we could possible reference for our final project presentation/paper? 
http://matsen.fredhutch.org/pplacer/
http://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-11-538

__Python JSON Parsing__
http://docs.python-guide.org/en/latest/scenarios/json/



__Guppy Documentation__
http://matsen.github.io/pplacer/generated_rst/guppy.html#id8
This contains tidbits on guppy. 
* Interestingly, guppy has a command (info) which writes the number of leaves on the tree and how many partial placements are on each leaf. http://matsen.github.io/pplacer/generated_rst/guppy_info.html#guppy-info
* Also, the guppy command for making fat trees counts the number reads mapped to internal edges. If we can look at the code and make sense of it we might be able to convert to python. http://matsen.github.io/pplacer/generated_rst/guppy_fat.html#guppy-fat

__DAP__
Hmmm, maybe we should poke around the DAP to see if any of it could be useful for us? I have access to its github repository. __JE__

__Newick Format__
* At the bottom of the wikipedia page on newick format is a setion on parsing newick formats. Some interesting bits down there. https://en.wikipedia.org/wiki/Newick_format __JE__
* Also, it appears there is a python module for doing things with newick trees. I haven't looked, but I am guessing it might contain hints as to how we could do things to the 'tree' section of the jplace file
https://github.com/glottobank/python-newick and https://pypi.python.org/pypi/newick/0.4.0 __JE__

__Nested Dictionaries and lists__
Correct me if I am wrong. The placement section contains a dictionary of placements. Each placement value contains a list of Sequences IDs and a list of placement information such as Tax ID, confidence, etc. __JE__

__tinyfasta__
https://github.com/tjelvar-olsson/tinyfasta/blob/master/tinyfasta/__init__.py
This is a fasta parsing script written in python 3 which I am attempting to base the jplace parsing script off of. It is broken down in to four sections (main classes): FastaRecordComponent, Sequence, FastaRecord, and FastaParse. Inside each class are subclasses and functions for dealing with the data unique to that section. For example, the first class (FastaRecordComponent) takes a string and checks if it is in the provided data. This is then used in all the other classes. Another example is the Sequence class which looks at the sequence in each fasta record. The FastaRecord class looks at the description part of each fasta reord. I am invisioning a similar format for the jplace script. Each section has a unique class for parsing it. The class will contain short functions, each created for one purpose and then utilized in other parts of the class or script. At least, that is what I think I was seeing in the tinyfasta script. __JE__ 

__Enumerate__
https://yuji.wordpress.com/2008/05/14/python-basics-of-python-dictionary-and-looping-through-them/
That is a link to some "hopefully" good info on iterating through data types. The article is a bit dated (2008) 
but contains a lot of useful insight. I think the python method .enumerate() fulfills the role of .iteritem() __JE__

__None__
A python object representing absolutely nothing. Here is an interesting article on it. http://pythoncentral.io/python-null-equivalent-none/
The tinyfasta uses it in the last class FastaParse for creating and storing a fasta_record instance. or something like that. So I included it in the framework we are working on. __JE__

__checking open/closed parentheses__
http://www.scientificpython.net/pyblog/checking-a-text-file-for-matching-parentheses-brackets-and-braces
Could be useful for finding tips in sets of closed parentheses.
*Nice! I like it. __JE__

