#Entity Identify in Emails
##Motivation
I want to investigate how to recognize the same person in a large quantities of emails, even though he or she may change his 
or her email addresses, signatures, even names for many times.

##Background
Sadly, but luckily, there isn't any published work solving this problem. Thus, I started with some partial related work like __Name Entity Recognition (NER)__ and __Traceability__.

##Papers Summeray & Analysis
These papers below are divided into two parts. The first part is for __Name Entity Recognition (NER)__ in Email. The other part is about __Tracibility__ studies between documents and source code.

####Name Entity Recognition
>[Minkov, Einat, Richard C. Wang, and William W. Cohen. "Extracting personal names from email: Applying named entity recognition to informal text." Proceedings of the conference on Human Language Technology and Empirical Methods in Natural Language Processing. Association for Computational Linguistics, 2005.
APA	](http://dl.acm.org/citation.cfm?id=1220631)

This work uses email-specific features to improve performance of person name recognizers for emails, and also use a recall-enhancing method to exploit name repetition across multiple documents.

#####Performance Improvement
Based on [conditional random fields (CRE)](https://en.wikipedia.org/wiki/Conditional_random_field), they use special attributes of emalil text to improve the performance.  Basically, they use Basic, Dictionary and Email features together to improve the F performance.

See the table below, 
![alt text](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/t2.png "t2")

Result:
![alt text](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/t3.png "t3")

The observation is that email messages often include some structured, easy-to-recognize names, such as names within a header, names appearing in automatically-generated phrases, as well as names in signature files or sign-offs. 


#####Improvement for Recall
They first look for multiple occurrences of names in a document.  Specifically, they take *single documment repetition* (SDR) and *multiple document repetition* (MDR) to improve the recall.
![f3](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/f3.png "f3")

Secondly, they also improve recall with Inferred Dictionaries. See one example and the improvement result below.
![f4](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/f4.png "f4")

That is based on the fact that a word *w* has appeared somewhere in a context that clearly indicates that it is a name does not increase the probability that it will be classified as a name in other, more ambiguous contexts.
      
>[Lawson, Nolan, et al. "Annotating large email datasets for named entity recognition with mechanical turk." Proceedings of the NAACL HLT 2010 Workshop on Creating Speech and Language Data with Amazon's Mechanical Turk. Association for Computational Linguistics, 2010.](http://dl.acm.org/citation.cfm?id=1866708&CFID=745380705&CFTOKEN=38686733)

---
It turns out that this paper is not so related to my research goals.  It focus on designing a competitive bonus system for improving NER from Mechanical Turk.

####Traceability
>1. [Chen, Xiaofan. "Extraction and visualization of traceability relationships between documents and source code." Proceedings of the IEEE/ACM international conference on Automated software engineering. ACM, 2010.](http://dl.acm.org/citation.cfm?id=1859098)
>2. [Chen, Xiaofan, and John Grundy. "Improving automated documentation to code traceability by combining retrieval techniques." Proceedings of the 2011 26th IEEE/ACM International Conference on Automated Software Engineering. IEEE Computer Society, 2011.](http://dl.acm.org/citation.cfm?id=2190177)

These two works are done by the same author for building a automated traceability finder between documents and codes.  They are helpful because they offer some hints for traceability extraction in massive text data.  The first work is just a prototype, and the second one has completed and integrated many features in.  No need to read 1, just go with 2.

##### Core Method  
Incorporating **Regular Expression (RE), Key Phrases(KP)**, and **Clustering** into a **Vector Space Model (VSM)** to overcoming the three main limitations of VSM. 
  1. Very few true links are retrieved at high cut points. 
  2. Many fault links are captured at low cut points. 
  3. VSM misses links in the following two situations: 
     + Class names that do not follow a common naming convention strategy; 
     + Documents that use different words to describe related classes. 

1. **RE** is used to get more true links at high cut points. It can correctly capture all documents directly containing class names and return few unrelated documents, thus it largely expands the retrieved link sets at high cut points but doesn't change the fault links recovered by VSM.

2. **KP** tries to recover links missed by VSM.  It assumes the code are well commented and are closely related to classes.  The result shows  adding the extracted key phrases to the VSM queries does help for the following two situations, but also introduce many fault links when cut points are low.
  +When class names don't follow a naming convention, like 'RefAddr'.
  +Documents implicitly mentioning a class but not explicitly using the same word as the class name, like a class named 'Media' but referred as 'medium' in documents.

3. **Clustering** is used after the first two steps, then for every classname it gets, it run clustering among all the possible links, and filter out the unrelated ones. The results show it eliminates fault links at low cut points by refining existing retrieved traceability links.

**Time-Consumption:**

![f-value](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/time.png)

**F-Performance:**

![f-value](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/f.png)

**Overview:**

![f-value](https://raw.githubusercontent.com/dichen001/Paper-Reading/master/img/sys.png)
