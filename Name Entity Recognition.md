#Entity Identify in Emails
##Motivation
I want to investigate how to recognize the same person in a large quantities of emails, even though he or she may change his 
or her email addresses, signatures, even names for many times.

##Background
Sadly, but luckily, there isn't any published work solving this problem. Thus, I started with some partial related work like 
__Name Entity Recognition (NER)__ and __Traceability__.

##Papers Summeray & Analysis
These papers below are divided into two parts. The first part is for __Name Entity Recognition (NER)__ in Email. The other part 
is about __Tracibility__ studies between documents and source code.

####Name Entity Recognition####
>[Minkov, Einat, Richard C. Wang, and William W. Cohen. "Extracting personal names from email: Applying named entity recognition to informal text." Proceedings of the conference on Human Language Technology and Empirical Methods in Natural Language Processing. Association for Computational Linguistics, 2005.
APA	]
(http://dl.acm.org/citation.cfm?id=1220631)

This work uses email-specific features to improve performance of person name recognizers for emails, and also use a 
recall-enhancing method to exploit name repetition across multiple documents.

#####Performance Improvement#####
Based on [conditional random fields (CRE)](https://en.wikipedia.org/wiki/Conditional_random_field), they use special attributes 
of emalil text to improve the performance. 
Basically, they use Basic, Dictionary and Email features together to improve the F performance.

See the table below, 
![alt text](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/t2.png "t2")
![alt text](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/t3.png "t3")

The observation is that email messages often include some structured, easy-to-recognize names, such as names within a header,
names appearing in automatically-generated phrases, as well as names in signature files or sign-offs. 


#####Improvement for Recall#####
They first look for multiple occurrences of names in a document.  Specifically, they take *single documment 
repetition* (SDR) and *multiple document repetition* (MDR) to improve the recall.
![f3](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/f3.png "f3")

Secondly, they also improve recall with Inferred Dictionaries. See one example and the improvement result below.
![f4](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/f4.png "f4")

That is based on the fact that a word *w* has appeared somewhere in a context that clearly indicates that it is a name 
does not increase the probability that it will be classified as a name in other, more ambiguous contexts.
      
>[Lawson, Nolan, et al. "Annotating large email datasets for named entity recognition with mechanical turk." Proceedings of the NAACL HLT 2010 Workshop on Creating Speech and Language Data with Amazon's Mechanical Turk. Association for Computational Linguistics, 2010.]
(http://dl.acm.org/citation.cfm?id=1866708&CFID=745380705&CFTOKEN=38686733)

####Tracibility####
>1. [Chen, Xiaofan. "Extraction and visualization of traceability relationships between documents and source code." Proceedings of the IEEE/ACM international conference on Automated software engineering. ACM, 2010.](http://dl.acm.org/citation.cfm?id=1859098)

dsajhfklajd dasfadsf
>2. [Chen, Xiaofan, and John Grundy. "Improving automated documentation to code traceability by combining retrieval techniques." Proceedings of the 2011 26th IEEE/ACM International Conference on Automated Software Engineering. IEEE Computer Society, 2011.]
(http://dl.acm.org/citation.cfm?id=2190177)




