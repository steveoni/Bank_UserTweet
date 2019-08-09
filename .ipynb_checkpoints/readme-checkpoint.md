## Text Classification ON Bank Users Tweet.
Bank users have always encountered one issue or the other with their banks, and one of their main issue is that, most of their banks does not respond in time to their complain. And most of them voice out this complain via twitter most especially when they could not contained the issue at hand.

Textblob is used by most people for sentiment analysis which involves the classification of text into Neutral,Negative and Positive. But sometimes it does not perform very well, especially with this time of bank user tweet. Most of the users, used **polite words** to make their complains and such words are classifies as positive or neutral.

In this project, the text are classified base on the issue of emergency. so some text my start with `thanks`, and some other polite word but actually the user is complaining, using the normal method , this kind of text my not spike the emergency alarm. And sometimes the text gotten are not always complete, some of them are truncated, may during the process of extraction and cleaning of tweet, but yet we want the model to be able to still infer what the text is about and still classify them perfectly.

## Aproach
To create a model that could classify even when their is a mixture of polite word with the complains or when the text is truncated, the model should understand the language. That is, A language model is first built to predict the next word, using wikitext103, such a model is good with english text, then after the language model is fine tuned on the target task to create a langauge model for the task and then after this language model is used as a pretrained weigh for our classification problem, This memthod is called 
**ULMFIT** developed by Jeremy and Sebastain.

. The data is obtained from twitter `getBankTweet.ipynb`
. The data is cleaned to remove unwanted tags. The obatained data are stores in a `/clean` folder and the `clean_data.ipynb` obtained the data from the clean folder and also save the final clean data in it.
. The cleaned data are then imported into `sentimentUI` and saved has `bb.txt`. This provide a web interface to classify our data. use `python -m SimpleHTTPServer` to open the interface on the web. 
![img/dsn.png](img/dsn.png)
And when an error is encounterd, may be we forget to classsify a text, it output the index error notification, you can saved the model when not done using the `storage` button. when this is done it save the last index in the browser, and when you want to start classifying again it start from where you stopped(the index when you save it). and the `submit button` is to finally save the text as `.csv`
![img/dsn.png](img/img1.png)

. The classified data are then grouped together to form one data called `bank_data` in `work2.ipynb`
. Then the model is built with fastai using the data.

## Note 
i did not upload the pretrained model. The pretrained model for text do contains the tokens and the weights, the size about 1.3gig for all the weight that it was saved in.