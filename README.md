# ECL-exercise4
UZH CL Week 9

Bonus: Person Name Recognizer

After having denied features to recognize person names you will write your own Person Name Recognizer in Python.

As a basis for your Person Name Recognizer we provide a file with 2522 Swiss first names. You find the file \swiss names.txt" in the folder \bonus" of this exercise. The name list contains three tab-separated columns:

The first column indicates the gender of the name:

M: male first name
1M: male name, if rst part of name; else: mostly male name
?M: mostly male name
F: female first name
1F: female name, if rst part of name; else: mostly female name
?F: mostly female name
?: unisex name (can be any gender)
=: indicates a nickname: (short name) (long name)

The second column contains the first names.
The third column indicates the frequency of a name ranging from 1 (= rare name) to 9 (= very common name).

With your Person Name Recognizer you should be able to extract person names from the \SAC-Jahrbuch 1930" which is included in the \bonus" folder. It contains three tab-separated columns with the token, the PoS-tag and the lemma. To keep our approach simple you should search the yearbook only for names listed in \swiss names.txt".

First step: Save the names in \swiss names.txt" into a suitable Python data structure (e.g. a dictionary). In order to take full advantage of the available data you might also want to store gender and frequency information for each name in your data structure.

Extend your Python script in order to search the \SAC-Jahrbuch 1930" for rst names. Print the names found to check whether your code works properly.

Now, we want to find not only rst names but the full name (i.e. st name and last name). Let's start with a naive approach: Whenever we find a first name in the yearbook, we assume that the following line will contain the last name. Extract the tokens of the two lines (i.e. the rst column of each line) and print them out together or save them to a list. Your output should now look like this:

Hugo Müller
Blanche .
Ange ,
August Müller
Leone Brons

As you can see, we are already able to find person names. But at the moment we have many false positives, i.e. our person name recognizer returns matches that don't consist of rst and last names (e.g. \Ange ,"). To get an idea of the current precision of our person name recognizer let's do a simple evaluation. Go through the rst 100 matches manually: 

How many of the rst 100 matches are indeed person names? Write down the answer in your submission sheet. 

Now, improve your person name recognizer by taking full advantage of the available data: The \SAC-Jahrbuch 1930" includes in the second column the PoS-tag of each token. Note that person names are annotated with a variety of PoS-tags, including NE, NN, N P etc. But still, there is a simple way to improve your system by using PoS-tag information: Change your script in a way that the line following a rst name is only matched if it has the same PoS-tag as the rst name. Your system should now match: Hugo_NE Müller_NE, but not Blanche_NE ._$.. Your output should now look like this:

Hugo Müller
August Müller
Joseph Croux
Emile Rey
Emile Rey

Add the names you found to a list. It's time for some fun statistics and insights we can gain from our findings. Use your list to find the answers to the following questions:

How many names did you find in the \SAC-Jahrbuch 1930"?
How many men's (tags M, ?M and 1M), how many women's (tags F, ?F and 1F) and how many unisex names are there in the corpus?
How many of the person names in our corpus are frequent names in the Swiss population? We define \frequent names" as names with a frequency tag  7 in \swiss names.txt". Filter the frequent names out of your list and count them.
Some names occur several times in the yearbook. How many different names are there in the \SAC-Jahrbuch 1930"?
Which are the 5 most frequent names in our corpus, i.e. the ones that occur most often in the yearbook? (Hint: Simply count how often each name occurs. Don't consider the frequency tags in \swiss names.txt").

Optional: To further improve your system you have to make sure to find the full name, not only part of a name. Consider two major problems: 

What happens in your current system with names consisting of a first name, middle name and a last name (e.g. Ulrich Wilhelm Zuricher)? Can you adapt it in a way that it returns all parts of the name?
What about multi-part last names (e.g. Blanche de Peuterey, Christian von Mechel)? Can you adapt your system in order to account for these names?
