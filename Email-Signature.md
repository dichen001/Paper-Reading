##Related Work 
 - **Year**-**Citation**-**Name**

1. 1998----28-----EMU- AN-E-MAIL-PREPROCESSOR-FOR-TEXT-TO-SPEECH
2. 1998----05-----E-mail-Signature-Block-Analysis
3. 1999----17-----Integrating-Geometrical-and-Linguistic-Analysis-for-Email-Signature-Block-Parsing
4. 2004----85-----Learning-to-Extract-Signature-and-Reply-Lines-from-Email
5. 2009----16-----Segmenting-Email-Message-Text-into-Zones
6. 2011----07-----Automatically-Locating-Salutation-and-Signature-Blocks-in-Emails
7. 2012----01-----Interpreting-Contact-Details-out-of-E-mail-Signature-Blocks

- **Development**
  - 1 --> 2 (Part of 1) <==> 3 (Detailed Version)
  - 4 Using ML, has a related open-source project using Python called [Talon](https://github.com/mailgun/talon)

## Details
### Signature Extraction
1. Parser Method
  - Parse each line into different functional class
  - Differentiate them according to the features of different block. 
  - For Signature parts, they usually have Email, URL, Phone Numbers, Miscs ect, once the portion of these parts exceed one threshould, they are marked as Sig.
2. ML Method
  - For each user, find last K lines which are identiccal for most of the emails.
  - An email message is represented by a set of features, and a classifier is
learned over this feature space.
