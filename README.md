# Spam Filter
Identifying spam messages from ham using naive-bayes classification.

<b>1.	Introduction</b>
   
    The current project demonstrates the use of naïve-bayes algorithm to filter spam from ham messages. 

<b>2.	Data Collection</b>

  <t>

     URL : http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/

     Source : Gómez JM, Almeida TA, Yamakami A. On the validity of
     a new SMS spam collection. Proceedings of the 11th IEEE International
 	  Conference on Machine Learning and Applications. 2012
  </t>

<b>3.	Implementation</b>

  <t>
  1.	Step-1 : Exploring and preparing the data
                Data is loaded into R atmosphere from the csv file.
  2.	Step-2 : Cleaning and standardizing the data
                Popular “tm” package is used for cleaning and standardizing the data. This includes creating an SMS corpus. 
                Then, the following cleaning process are executed:
                
               
                i.	Transformation to lower case.
                ii.	Removal of numbers.
                iii.	Removal of stop words such as ‘to’, ‘and’, ‘but’ and ‘or’ using stopWords() function. removeWords() contains a
                list of ‘stop words’.
                iv.	Removal of punctuation.
                v.	Stemming i.e., transforming words into base form. Ex: learning, learned, learns to learn using the “SnowBallC” package.
               
                
  3.	Step-3 : Training a model on the data.
  4.	Step-4 : Evaluation of model performance
  </t>
<b>  4.	Summary</b>

  <t>
  
     The use of naïve-bayes classifier is demonstrated for text classification. 
     The text data was prepared for analysis by using specialized R packages for Text processing and visualization. 
     Finally, the model was able to classify 98 percent of all the messages correctly as spam and ham.
  </t>
