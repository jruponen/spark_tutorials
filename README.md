These instructions and some files needed in the tutorials are provided at: https://github.com/jruponen/spark_tutorials.

General Spark tutorials are found at: https://developer.ibm.com/clouddataservices/docs/spark/tutorials-and-samples/


##STEP 1: Create your Apache Spark service in Bluemix

1. Login to Bluemix.net

2. Go to Catalog

3. Find "Apache Spark" service and click on it

4. For the Service name, enter the following:
	Service name: [your initials] Apache Spark  (e.g JR Apache Spark)

5. Press Create

Once you have this step done, Apache Spark introduction page will open for you.
Notice on the page:
  * Work with Notebooks and Spark (Notebooks button will take you Spark service interface) 
  * Run Spark Applications
  * Monitor Spark Usage
  * Learn (link to Spark service documentation in Bluemix)
  * Discover (link to Learning Center for tutorials, samples etc)

##STEP 2: Set up an Object Storage for your Spark instance

Object Storage is an OpenStack Swift based repository in bluemix where you can store uploaded data files, analysis notebooks etc.

1. On the Spark introduction page, press Notebooks

2. Notice the navigation bar (tabs) on the left:
  * Services: List of your other Bluemix services that you may use with Spark to read and write data
  * Data: Connections providing links to your existing data sources
  * Analytics: Your stored Spark Notebooks and instances of Spark you have set up
  * Exchange: Shared Notebooks that you may want to re-use

3. Click "Analytics" on the left

4. Click "Instances" on the top

5. Click on your instance (e.g "JR Apache Spark")

6. Click "Object Storage" on the top

7. Press "Add Object Storage"

**Note:** Only one Object Storage is allowed per your Bluemix organization. If you had one created already (or if you are adding another instance of Spark), you may re-use your existing Object Storage by going to "Bluemix" tab and selecting an existing one.

8. Fill in the following values:
  * Name:		Service name  (e.g "JR Apache Spark objectstore")
  * Space:		dev (or whatever your space is named as)
  * Plan:		Free
  * Container name:	notebooks

9. Press "Create"

Now that you have Apache Spark service up and running, associated with an Object Storage, you may continue to tutorials.

##TUTORIAL 1: Getting Started on Notebooks with Precipitation Analysis

In this tutorial, you'll learn the very basics of using Spark to analyze data with Jupyter Notebooks, using iPython language.
("Scala" is another language option with Spark that you can learn in other tutorials later on).

1. Click "Analytics" on the navigation bar

2. Click "New Notebook" button
	Notice, that there are three ways you can create new analysis notebooks:
  * Blank (start with a blank one)
  * From File (upload an existing Notebook file from your computer)
  * From URL (upload an existing Notebook file from network)
  * Start from a Sample template

3. Let's create your first tutorial Notebook from a sample

	Two alternative samples exist: "Custom" and "Original".
	The "Custom" one provides some extra information that beginners may found useful (recommended).
	The "Original" one is almost similar and is provided with Apache Spark already, but is missing some basic info.
	In the end, they both really do the same, analysis of precipitation data, and you may choose either one.

	Custom sample:
	https://raw.githubusercontent.com/jruponen/spark_tutorials/master/Precipitation%20Analysis.ipynb

  * Within the Spark service, go to Analytics and press "New Notebook"
  * Select "From URL"
  * Provide the name: "Precipitation Analysis"
  * For Notebook URL, copy paste the URL above (for "Precipitation Analysis.ipynb" file)
  * Press "Create Notebook"

	Original sample:

  * Within the Spark service, go to Analytics and press "New Notebook"
  * Select "Samples"
  * Select "Precipitation Analysis"
  * Press "Create Notebook"
	
4. Follow instructions in the sample Notebook to complete the tutorial.
	Make sure you go through each step.

5. After you have completed the first tutorial, you may want to save & checkpoint your Notebook.

As you may have noticed, there is really no option to "close" your Notebook. You may navigate away from your Notebook and come back later. Your analysis just continues to run on Spark kernel until you stop it. In order to stop your Notebook from running, you can either go to "Analytics" page, find your Notebook, click on it's "Actions" and select "Stop Kernel". You may also do this with the Notebook open by selecting from top menu "Kernel" and "Interrupt".

**Extra challenge**  
What were the answers to extra questions in the end of Notebook:
  * Which country has the most steep positive trend in precipitation?
  * Which were the top 5 countries with most steep positive trends in their precipitation?

##TUTORIAL 2 (optional): Analytics Notebooks and Apache Spark

This tutorial is optional simply because:
  * This is a **big data** exercise involving a large file download (200MB) and then even larger file upload (1.17GB)!
  * A fast network connection would be required in order to be able to complete this tutorial during the class session.

This exercise is a bit more envolving. You'll working with raw daily weather data from weather stations and it shows you how to work with RDD (Resilient Distributed Datasets) in Spark. You'll also learn how to use Spark SQL to make queries to the data.

You may try it now, but if you find it too slow to upload the 1.17GB file during the session, complete this tutorial at later time.

1. Click "Analytics" on the navigation bar

2. Click "New Notebook" button

3. Select "Samples"

4. Select the second sample, "Analytics Notebooks and Apache Spark"

5. Press "Create Notebook"

6. Follow instructions in the sample Notebook.
	Make sure you go through each step.

Here's a direct link to the file you are supposed to download for daily weather data in 2015 (file size approx 200MB):
ftp://ftp.ncdc.noaa.gov/pub/data/ghcn/daily/by_year/2015.csv.gz

After extracted 2015.csv (file size 1.17GB), you can add the required header on Mac or Linux using the command line:
```
$ echo 'STATION,DATE,METRIC,VALUE,C5,C6,C7,C8' | cat - 2015.csv > temp && mv temp 2015.csv
```

**Extra challenge**  
What was the answer to extra question in the end of Notebook:
  * For the top 10 station with the most snow days, what is the average minimum temperature during recorded snowfall?


##TUTORIAL 3: Analyze NYC taxi data

This is relatively simple analysis but it shows you how to get data for analysis directly from an external site via REST API call.  
**Update on 2016-03-30:** In addition, there are now few optional steps that show you how to export data from your Notebook, to be used somewhere else.

The sample Notebook is available at:
https://raw.githubusercontent.com/jruponen/spark_tutorials/master/NYC%20taxidata%20example%20with%20data%20export%20options.ipynb

1. Click "Analytics" on the navigation bar

2. Click "New Notebook" button

3. Select "From URL"

4. Provide the name: "NYC taxidata example"

5. For Notebook URL, copy paste the URL above (for "NYC taxidata example.ipynb" file)

6. Press "Create Notebook"

7. Follow instructions in the sample Notebook.
	Make sure you go through each step.


**Extra challenge:**
In the end of the Notebook you were asked what other insight could you derive from the data.
Did you find any?


##TUTORIAL 4: NY Motor Vehicle Accident Analysis

Here you'll analyze vehicle collisions data from NYPD and learn more about creating insightful visualizations in Notebook.
Although containing all collision data from 2012 the data set to dowload & upload is still reasonable in size, 149MB.

1. Click "Analytics" on the navigation bar

2. Click "New Notebook" button

3. Select "Samples"

4. Select the second sample, "NY Motor Vehicle Accidents Analysis"

5. Press "Create Notebook"

6. Follow instructions in the sample Notebook.
	Make sure you go through each step.


##TUTORIAL 5 (Optional): Data integration

This tutorial is optional and for your reference only since it does not perform any analysis on data.
It shows you how you can load data on your Notebook from either Object Storage, Cloudant or dashDB, using either Python or PySpark. Use it as your reference when you have self-collected data into one of these stores and will need to load it on your Notebook.
It is especially useful when working with Node-RED - Cloudant - dashDB - Spark combination (see the next tutorial).

To access this sample Notebook, perform the following

1. Click "Analytics" on the navigation bar

2. Click "New Notebook" button

3. Select "Samples"

4. Select the second sample, "Data integration"

5. Press "Create Notebook"

6. Follow instructions in the sample Notebook.
	Make sure you go through each step.


##TUTORIAL 6: Set up Node-RED and Cloudant for data collection

This is a fairly quick setup but extremely valuable to you for collecting and processing data, as you'll learn in later tutorials.
In short, here you'll set up yourself a Node-RED application for handling data streams and a Cloudant noSQL data store.

**Background information:**  

Node-RED is open source (http://nodered.org) and has become very popular in creating and processing data streams, either with simple JavaScript knowledge or even with no coding at all! Node-RED can be extended with number of freely available nodes and you may also develop new ones by yourself. In Bluemix you may also leverage number of other capabilities like trying out some IBM Watson API's with Node-RED that will help you build more advanced analytic and cognitive solutions, or you may want to test out Internet-of-Things (IoT) capabilities in Bluemix to read data from machines and sensors.


To set up your Node-RED & Cloudant environment, perform the following:

1. Login to Bluemix.net

2. Click "Account and Support" icon in the top right corner

3. Make sure your region is set to "US South" 

4. Go to Catalog

5. Click "Node-RED Starter Community" boilerplate

6. Enter the following Name & Host:
	- Name: [your initials]NodeRED	(e.g JRNodeRED)
	- Host: [your initials]NodeRED	(e.g JRNodeRED)

7. Press Create

Your newly created Node-RED application is now staging (= starting).
It may take a while to be provisioned on a server in Bluemix data center.
Meanwhile, you may want to download and install the CF Command Line Interface (press the blue button).
CF is useful since you can then also use Bluemix from command line, without a graphical user interface.

Once your application is started, go to it's Overview page.
You have now created:
- SDK for Node.js runtime with Node-RED data stream editor installed
- Cloudant NoSQL data store

##TUTORIAL 7: Analyze crime data in Cloudant data store

**Pre-req**: You must have to have completed tutorial 6 in order to proceed with this one.

**Tutorial:**
https://developer.ibm.com/clouddataservices/docs/spark/tutorials-and-samples/use-python-notebook-to-load-cloudant-data-into-spark/

Follow the Procedures 1 & 2, observing the additional notes on below:

**Note 1**: In procedure 1, step 1, you are supposed to do the following:
  * Click on the Cloudant service icon from your Node-RED application dashboard in Bluemix
  * Press "Launch" (Cloudant user interface will then open)

**Note 2**: In procedure 1, step 5, you are asked for your Cloudant password.
This is a complex password created by the system. To see this password and copy it to clipboard, press "Show Credentials" on your Cloudant service icon on the Node-RED application dashboard. Once the replication event has been submitted, it will take just few moments to create your local replicate. Go to "Databases" tab and verify that you now have "crimes" database with 272 docs in it.

**Note 3**: In procedure 2, steps 9 through 18, instead of series of copy/paste you may also create the notebook from this URL:
https://raw.githubusercontent.com/cloudant-labs/spark-cloudant/master/examples/ipython/python_Cloudant.ipynb

**Note 4**: To add your Cloudant credentials on the Notebook, do the following:
  * Go to your Bluemix Dashboard and click on your Node-RED application icon
  * Under Cloudant icon, click "Show Credentials"
  * To read from Cloudant database set the values of host, username, password and database name on your Notebook in the following format:
```
read_db_name = "crimes"
cloudantdata = sqlContext.read.format("com.cloudant.spark")\
.option("cloudant.host",'aa1e8db0-7b86-415c-81eb-41615ab4119c-bluemix.cloudant.com')\
.option("cloudant.username",'aa1e8db0-7b86-415c-81eb-41615ab4119c-bluemix')\
.option("cloudant.password",'e74eed5af8ecfae41fa9bb650d6dbcf26c778bc3833647e1ceedae197f579d10')\
.load(read_db_name)
```
  * To write to Cloudant, set the values again as:
```
write_db_name = "crimes_filtered"
disturbDf.select("properties").write.format("com.cloudant.spark")\
.option("cloudant.host","kache.cloudant.com")\
.option("cloudant.username","kache")\
.option("cloudant.password","xxxxx")\
.save("write_db_name")
```

##TUTORIAL 8: Collect tweets into Cloudant data store

This is fairly simple task to do, see tutorial video here:
https://developer.ibm.com/clouddataservices/docs/dashdb/get/store-tweets-using-bluemix-node-red-cloudant-and-dashdb/

**IMPORTANT NOTE: DESPITE INSTRUCTED ON THE VIDEO, DO NOT USE CLOUDANT DATABASE NAME "NODERED" !!**
"nodered" database name is already reserved for storing your Node-RED flows and you DO NOT want to mess it up by storing tweets in the same database. Instead, in your Cloudant node on the Node-RED, use a database name like "tweets". Don't worry if it does not exist, it will be then created.

As with previous tutorial, you can now read your collected tweets from Cloudant to your Spark for analysis.
(This was also instructed in the "Data Integration" tutorial)

In addition to storing tweets in Cloudant, you may also use Cloudant to set up a dashDB SQL data store ("Data Warehouse") that will then have near real-time replicated copies of your collected tweets. This step is also briefly shown in the tutorial video. There are three clear benefits in adding dashDB warehouse on top of Cloudant:
1) it's a SQL store so you may connect basically any analytic tool directly to it
2) it has R runtime built-in so you may also use R language and RStudio to create your analysis
3) it's an "analytic" data warehouse, meaning that it can perform your calculations on the data very fast

As obvious, dashDB data can also be read from Spark directly.
This is instructed in Scala tutorial here: https://developer.ibm.com/clouddataservices/docs/spark/tutorials-and-samples/load-and-analyze-dashdb-data-with-spark/.
And also in the "Data Integration" tutorial shown earlier.

After collected some tweets, see what kind of analysis you can perform with them.
**Important:** Remember to stop collecting the tweets after a while or your database may fill up fast.
To stop collection on Node-RED, just delete the wire to the Cloudant node and re-deploy the flow.


##ADDITIONAL TUTORIALS:

**Load Cloudant Data in Apache Spark using a Scala Notebook**
https://developer.ibm.com/clouddataservices/docs/spark/tutorials-and-samples/load-and-filter-cloudant-data-with-spark/

**Sentiment Analysis of Twitter Hashtags using Spark Streaming**
Use Apache Spark Streaming in combination with IBM Watson to perform sentiment analysis and track how a conversation is trending on Twitter.
https://developer.ibm.com/clouddataservices/sentiment-analysis-of-twitter-hashtags/

**Using the Machine Learning library**
https://developer.ibm.com/clouddataservices/docs/spark/tutorials-and-samples/use-the-machine-learning-library/

**Build a custom library for Apache Spark and deploy it to a Jupyter Notebook**
https://developer.ibm.com/clouddataservices/start-developing-with-spark-and-notebooks/

##SELF-PACED LEARNING OF SPARK FUNDAMENTALS:
Access courses at: http://bigdatauniversity.com.
Complete courses "Spark Fundamentals I" and "Spark Fundamentals II".
Additionally, see other courses directed for Data Scientists (http://bigdatauniversity.com/learn/data-science/).

### Quick instructions to setup Spark standalone on your own machine ###  
Note: **Spark standalone** is a good option to run Spark for testing and learning purposes. It is not to be used for production purposes.

1. Download Spark
(http://spark.apache.org/downloads.html)
2. Extract
Extract to directory of your choice, e.g:  
```
./Spark/spark-1.6.1-bin-hadoop2.6
```
3 Optional: Export JAVA_HOME  
On Mac OS X:
```
$ export JAVA_HOME=$(/usr/libexec/java_home) 
```
4. Start Spark Master
```
$ cd /Spark/spark-1.6.1-bin-hadoop2.6
$ ./sbin/start-master.sh
```
5. Verify Spark Master
In browser, open: http://localhost:8080(http://localhost:8080)  
Copy paste Spark URL address:	spark://localhost:7077

6. Start worker(s)
```
$ ./bin/spark-class org.apache.spark.deploy.worker.Worker spark://localhost:7077
```
7. Verify Spark worker
In browser, open (or refresh): http://localhost:8080(http://localhost:8080)  
Should now see one worker attached to the master.
8. Try interactive Scala shell
```
$ ./bin/spark-shell --master spark://localhost:7077
```
or
```
$ ./bin/spark-shell --master local[2]
```
9. Try interactive Python shell
```
$ ./bin/pyspark --master spark://localhost:7077
```
or
```
$ ./bin/pyspark --master local[2]
```
