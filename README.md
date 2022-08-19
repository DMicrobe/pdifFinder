# PdifFinder
Author:     Shao Mengjie

Email:      xiaotinghua@zju.edu.cn

institute:  Key laboratory of Microbiol technology and Bioinformatics of Zhejiang Province

This program is designed for annotation of antimicrobal resistance(AMR), pdif site and pdif-ARGs module in bacteria.

### Install:
PdifFinder is a python3.X script, running on linux. 
You should install BLAST and add it in environment variable, you can download from `https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/`. BLAST version is 2.10.1 in bacant.

* One:
  You can download from github by `git clone https://github.com/mjshao06/pdifFinder.git`. Then execute `python setup.py install`.
* Two:
  You can install BacAnt from [PyPI](https://pypi.org/project/PdifFinder) by `pip install PdifFinder`.


### Run:
PdifFinder can accept FASTA and GENBANK format file(single or multi sequences in one file). Attention on GENBANK format file, it should follow standard format.
There are three input parameter, "-i" means FASTA, "-g" means GENBANK, "-d" means input dir contains FASTA or GENBANK.
* Simply, you can just run:
```
pdifFinder -n FASTA -o outdir
pdifFinder -g GENBANK -o outdir
pdifFinder -d inputdir -o outdir
```
* For more parameter, you can run:
```
bacant -h
```
* Here are some import parameter:

parameter  | description
---- | -----
--nucleotide(-n) | FASTA file
--genbank(-g) | GENBANK file
--indir(-d) | input dirname
--resultdir(-o) | output dirname
--map(-c) | output graph format,default is circle

### Databases:
We have updated database to v2.0(2021.05.11) since BacAnt-v3.3.1. You can download from [here](http://bacant.net/static/database/v2.0/bacant-db-v2.0.tar.gz).
User can define their custom databases, and when run bacant ,just add parameter -p(--path) for databases dirname.
Here are databases structure:

<pre>
  .
  ├── AMRDB
  │   ├── sequence.fasta         Resistance gene reference sequences in FASTA format
  │   │                     sequence id must be database name~~~gene~~~accession~~~description,
  │   │                     eg:  ncbi~~~1567214_ble~~~NG_047553.1~~~BLEOMYCIN BLMA family bleomycin binding protein
  │   ├── Res.nhr
  │   ├── Res.nin
  │   └── Res.nsq
  │   └── Res.ndb
  │   └── Res.not
  └── TransposonDB
      ├── Transposon.fasta  Transposon reference sequences in FASTA format
      │                     sequence id must be description|accession,eg: Tn2009|CP001937
      ├── Transposon.nhr
      ├── Transposon.nin
      └── Transposon.nsq
</pre>      
### Output:

filename  | description
---- | -----
*.gb | GENBANK format annotation
AMR.tsv | filtered resistance annotation
AMR.possible.tsv | all possible resistance annotation
replicon.tsv | replicon annotation
integron.filter.tsv | most like integron
integron.detail.tsv | integron_finder result,detail descripton of integron structure
transposon.filter.tsv | transposon element after overlap screen
transposon.possible.tsv | all possible transposon element
annotation.html | output visualization
