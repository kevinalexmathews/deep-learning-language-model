## Training a Deep Learning Language Model Using Keras and Tensorflow
_A Code Pattern focusing on how to train a machine learning language model while using Keras and Tensorflow._

This Code Pattern will guide you through installing Keras and Tensorflow, downloading Yelp data and training a language model using recurrent neural networks, or RNNs, to generate text.

Using deep learning to generate information is a hot area of research and experimentation. In particular, the RNN deep learning model approach has seemingly boundless amounts of areas it can be applied to, whether it be to solutions to problems or areas of intrigue. One of these areas is text generation, which is what this Code Pattern introduces. Text generation is used in language translation, machine translation and spell correction. All of these examples are created through language models. This Code Pattern runs through exactly that: a language model using an LSTM (long short term memory) RNN. For some context, RNNs use networks with hidden layers of memory to predict the next step using the highest probability. By doing this, RNNs can use the text it is given to generate the next letters to form a word which eventually ends up in sentences and paragraphs. The LSTM part of the model allows you to build an even bigger RNN model with improved learning of long-term dependencies. This means an improved performance for those words and sentences we're generating!

Though training a language model is exciting, it is important to keep in mind that as much good as deep learning can do, it can be equally misused and misapplied for illegal approaches such as fake reviews. Fake reviews specifically are a very real problem for companies such as Amazon and Yelp, who rely on reviews to vouch for their products and businesses which are featured on their sites. As of writing this, it is very easy for businesses to pay for fake, positive reviews, which ultimately end up elevating their sales and revenue. Unfortunately this leads users to places and products fradulently and can potentially lead to someone having a negative experience or worse. In order to combat these abuses and illegal activity, we must first understand how to generate these false reviews and build a dataset of generated reviews. By learning how they're constructed and how to execute them we can prevent any misuse by using the same approach and comparing true and false datasets. Only then can we use our knowledge of generating text to prevent generated text. Seem crazy? Well this approach follows the University of Chicago's paper [Automated Crowdturfing Attacks and Defenses in Online Review Systems](https://arxiv.org/pdf/1708.08151.pdf) to generate reviews using Yelp's open data (part 1) and then use the data we've created to stop fake reviews (part 2). This is part 1. Let's go explore shall we?

The original yelp data used in this Code Pattern can be found [here](https://www.kaggle.com/c/yelp-recruiting/data) as well as in this repository under [data/](https://github.com/MadisonJMyers/Training-a-Deep-Learning-Language-Model-Using-Keras-and-Tensorflow/tree/master/data). 

### But what is Keras and Tensorflow?

If you've clicked on this Code Pattern I imagine you range from a deep learning expert to a beginner who's interested in learning more. Wherever you are on the spectrum, you probably think machine learning and deep learning are awesome (which they are) and have probably been exposed to some examples and terminology. You probably also understand some python and the fact that deep learning is a subset of machine learning (which is a subset of artifical intelligence as a whole). With those assumptions in mind, I can explain that Tensorflow is an open-source software library for machine learning, which allows you to keep track of all of your models and also see them with cool visualizations. Keras is a deep learning library that you can use in conjunction with Tensorflow and many other deep learning libraries. Keras is very user-friendly in that it allows you to complete a model (for example using RNNs) with very few lines of code, which makes every data scientist's (including myself) life much easier. It can also switch between libraries depending on what you're trying to do, saving you a great deal of headache and time.

![](doc/source/images/architecture.png)

## Flow

1. Download the yelp data.
2. Download and install Keras, Tensorflow and their prerequisites.
3. Explore how to run the Jupyter notebooks.
4. Train a language model to generate text and run it.
5. Analyze the result.

## Included components

* [Jupyter Notebook](http://jupyter.org/): An open source web application that allows you to create and share documents that contain live code, equations, visualizations, and explanatory text.
* [Keras](https://keras.io/): The Python Deep Learning library.
* [Tensorflow](https://www.tensorflow.org/): An open-source software library for Machine Intelligence.

## Featured technologies

* [Cloud](https://www.ibm.com/developerworks/learn/cloud/): Accessing computer and information technology resources through the Internet.
* [Data Science](https://medium.com/ibm-data-science-experience/): Systems and scientific methods to analyze structured and unstructured data in order to extract knowledge and insights.
* [Python](https://www.python.org/): Python is a programming language that lets you work more quickly and integrate your systems more effectively.

# Watch the Video
TBD


# Prerequisites

    1. Have python 3.0 or above installed.
    2. Install libraries, keras and tensorflow.
    
1. Have python 3.0 or above installed.

2. Install libraries, keras and tensorflow.

    Have pip installed.
    Install SciPy and NumPy.
    Install Pandas.
    Install zipfile.
    Install json.
    Install Tensorflow. 
    Go [here](https://www.tensorflow.org/install/) to follow the directions if you are not on a MacOS.
    For Mac users, ```pip install tensorflow-gpu``` will install the gpu version, which is what I used on my server.
    For Keras, you can go to [this](https://keras.io/#getting-started-30-seconds-to-keras) link. 
    You can also just ```pip install keras```.
    Or you can use git:
    
    ``` git clone https://github.com/fchollet/keras.git ```
    ``` cd keras ```
    ``` sudo python setup.py install ```

# Steps

This pattern runs through the steps below. Check out the notebook for the code!

    1. Start a Jupyter notebook.
    2. Run the notebook.
    3. Train a model.
    4. Analyze the result.

1. Start a Jupyter notebook.

* From here you can choose to work in terminal while using python or download jupyter notebook to follow along:
       ```pip install jupyter notebook```
* Once that is installed you can enter ```jupyter notebook``` in your terminal and a notebook should pop up in your browser.
* If a notebook was did not automatically pop up, go to the url given in your terminal.
* The notebook containing the code for this pattern is in this [repository](https://github.com/MadisonJMyers/Training-a-Deep-Learning-Language-Model-Using-Keras-and-Tensorflow/tree/master/notebooks). 
* Download the notebooks, data and files into the folder you started jupyter notebook in. Once you do that it should appear in the browser. Click on it to open it up.

![](doc/source/images/Screen%20Shot%202017-12-11%20at%202.10.50%20PM.png)

2. Run the notebook.
 
When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.
* At a scheduled time.
  * Press the `Schedule` button located in the top right section of your notebook
    panel. Here you can schedule your notebook to be executed once at some future
    time, or repeatedly at your specified interval.
    
![](doc/source/images/Screen%20Shot%202017-12-11%20at%202.11.11%20PM.png)    
    
3. Train a model.

* Make sure you collect all of the files into the same folder. Then run transfer_learn.py.

To help understand what we're doing here, in the file transfer_learn.py we use a keras sequential model of the LSTM variety, mentioned earlier. We use this variety so that we can include hidden layers of memory to generate more accurate text. Here the maxlen is automatically set to none. The maxlen refers to the maximum length of the sequence and can be none or an integer. We then use the Adam optimizer with categorical_crossentropy and begin by loading our transfer_weights. We define the sample with a temperature of 0.6. The temperature here is a parameter than can be used in the softmax function which controls the level of newness generated where 1 constricts sampling and leads to less diverse/more repetitive text and 0 has completely diverse text. In this case we are leaning slightly more towards repetition though in this particular model, we generate multiple diversities which we can compare to one anmother to see which works best for us. You'll also see the use of enumerate in the transfer_learn.py which ultimately allows us to create an automatic counter and loop over information. We then train the model and save our weights into transfer_weights. After executing you should see tensorflow start up and then various epochs running on your screen followed by generated text.

_See the notebook for further detail on what else you can do with the language model._
* For this Code Pattern you'll need to go into the file where you downloaded everything (should be on your server).
* Make sure you have everything in the same folder.
* Now type ``` python transfer_learn.py ``` and push enter.
* The model should be running and generating text based on the yelp data it was given.
* To learn more you can dive into the Yelp_Data.ipynb or open transfer_learn.ipynb to figure out how this language model works, in a more hands on way.

![](doc/source/images/architecture2.png)

As you can see in the diagram above, the inputed text is sent through several layers of the LSTM model and then sent through a dense layer followed by a softmax layer. This considers information and iterates over the data at a character level.

![](doc/source/images/architecture3.png)

This model takes inputed text and 0s and outputs generated text.

4. Analyze the result.

As you can see in the image below, you should expect to see text being generated with different diversities and then saved back into the weights. By this output you can see what different outputs are based on different diversities of text (more diverse vs less or more repetitive).

![](doc/source/images/Screen%20Shot%202017-12-07%20at%2011.16.22%20AM.png)

Congrats! Now you've learned how to generate text based on the data you've given it. Look out for the next Code Pattern which takes this generated data and learns how to detect the fake text vs the real, original text.

# Links

* [Create Data Science Experience Notebooks](https://datascience.ibm.com/docs/content/analyze-data/creating-notebooks.html)
* [Jupyter Notebook](http://jupyter.org/): An open source web application that allows you to create and share documents that contain live code, equations, visualizations, and explanatory text.
* [Keras](https://keras.io/): The Python Deep Learning library.
* [Tensorflow](https://www.tensorflow.org/): An open-source software library for Machine Intelligence.


# Learn more

* **Data Analytics Code Patterns**: Enjoyed this Code Pattern? Check out our other [Data Analytics Code Patterns](https://developer.ibm.com/code/technologies/data-science/)
* **AI and Data Code Pattern Playlist**: Bookmark our [playlist](https://www.youtube.com/playlist?list=PLzUbsvIyrNfknNewObx5N7uGZ5FKH0Fde) with all of our Code Pattern videos
* **Data Science Experience**: Master the art of data science with IBM's [Data Science Experience](https://datascience.ibm.com/)
* **Spark on IBM Cloud**: Need a Spark cluster? Create up to 30 Spark executors on IBM Cloud with our [Spark service](https://console.bluemix.net/catalog/services/apache-spark)

# License
[Apache 2.0](LICENSE)
