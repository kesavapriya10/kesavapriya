# kesavapriya
The Chatbot.json file contains different types of tags to handle user queries. Chatbot.json file will have lot of messages that the user is likely to type in and mapping them to a group of appropriate responses. The tag on each dictionary in the file indicates the group that each message belongs too. With this data we will train a neural network to take a sentence of words and classify it as one of the tags in our file. Then we can simply take a response from those groups and display that to the user.The more tags, responses, and patterns you provide to the chatbot the better and more complex it will be.
 Extracting Data – Will take out the data we want from our JSON file. It needs all of the patterns and which class/tag they belong to. We also want a list of all of the unique words in our patterns, so following blank lists is required to store these values.
words = []
labels = []
docs_x = []
docs_y = []
Now I will loop through our JSON data and extract the data we want. For each pattern we will turn it into a list of words using nltk.word_tokenizer, rather than having them as strings. We will then add each pattern into our docs_x list and its associated tag into the docs_y list.

 Word Stemming - Stemming a word is attempting to find the root of the word. For example, the word "thats" stem might be "that" and the word "happening" would have the stem of "happen". We will use this process of stemming words to reduce the vocabulary of our model and attempt to find the more general meaning behind sentences.
 
 Developing a Model: After preprocessing all our data then we are ready to start creating and training a model. For Railway reservation I will use a standard feed-forward neural network with two hidden layers. The goal of network will be to look at a bag of words and give a class that they belong too (one of our tags from the JSON file).
 
 Making Predictions – With the help of above model, I will generate a response to any sentence the user types in. To do this we need to remember that our model does not take string input, it takes a bag of words. We also need to realize that our model does not spit out sentences, it generates a list of probabilities for all of our classes. This makes the process to generate a response look like the following:
– Get some input from the user
– Convert it to a bag of words
– Get a prediction from the model
– Find the most probable class
– Pick a response from that class

The bag_of_words function will transform our string input to a bag of words using our created words list. The chat function will handle getting a prediction from the model and grabbing an appropriate response from our JSON file of responses.


