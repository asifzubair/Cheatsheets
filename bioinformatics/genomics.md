# Genomics #

* [GGD](http://www.gettinggeneticsdone.com/2012/04/awk-command-to-count-total-unique-and.html): Useful `awk` script.  

```shell
gzip -d -c myfile.fq.gz | awk '((NR-2)%4==0){read=$1;total++;count[read]++}END{for(read in count)\
{if(!max||count[read]>max){max=count[read];maxRead=read};if(count[read]==1){unique++}}; \
print total,unique,unique*100/total,maxRead,count[maxRead],count[maxRead]*100/total}'
```
The output would look something like this for RNA-seq data:  
`99115 60567 61.1078 ACCTCAGGA 354 0.357161`

This is telling you: 
```
- The total number of reads (99,115).  
- The number of unique reads (60,567).  
- The frequency of unique reads as a proportion of the total (61%).  
- The most abundant sequence (useful for finding adapters, linkers, etc).  
- The number of times that sequence is present (354).  
- The frequency of that sequence as a proportion of the total number of reads (0.35%).  
```

* GGD: Useful [oneliners](https://github.com/stephenturner/oneliners)  

---

**References:**  
GGD: http://www.gettinggeneticsdone.com

**Bioinformatics**
* https://wikis.utexas.edu/display/bioiteam/SSC+Intro+to+NGS+Bioinformatics+Course
* http://www.personal.psu.edu/iua1/2015_fall_852/main_2015_fall_852.html
