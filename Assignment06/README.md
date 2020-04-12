# Assignment06
@name Toby Chappell  
@student_id 2312642  
@email tchappell@chapman.edu  
@course CPSC 392
@assignment 6

The songs.csv file contains different features of songs from X different music genres. Your task is to use the built-in kMeans clustering algorithm in the scikit-learn library to find the hidden genres in the data. You can use the elbow method to first figure out how many genres there should be, and then come up with a way to reduce the number of attributes you are using for clustering. The idea here is to find out which property of a song is best in distinguishing different genres. 

Once done, add a lengthy note about how you would go about validating the findings from your model.

Next, since we haven't done a lot of pure Python coding, I want you to also write your own k-Means algorithm. There are plenty of implementations for kMeans on the internet. But please use them as inspiration to write your own code. To make things easy, your kMeans algorithm function can only use the k value of 2, and can be applied on 2 independent variables. I am leaving the implementation open ended so your independent variables can be in the form of a data frame, lists, etc. The convergence mechanism for your centroids is also left open ended, and you can choose any tolerance value for your function. Please don't forget to add comments to your code.
