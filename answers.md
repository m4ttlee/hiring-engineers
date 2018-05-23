5/22/2018 - Matt Lee

For all referenced screenshots, these should be uploaded to the repo. If not, please refer to: https://drive.google.com/drive/folders/1Zqz5rcJkE-1aCFksUctqIJTX7vWt2mWT?usp=sharing 

+++++++++++++++++
Collecting Metrics
  - Add tags in the Agent config file and show us a screenshot of your host and its tags on the Host Map page in Datadog.
      -**COMPLETED. Added tags in the config file: "region:us-west-2, env:aws, role:ubuntu1".**
      -**IMAGE REFERENCED: Refer to "1-tags1", "1-tags2"**
  - Install a database on your machine (MongoDB, MySQL, or PostgreSQL) and then install the respective Datadog integration for that database.
      -**COMPLETED. Installed PostgreSQL, and its respective Datadog integration.**
      -**IMAGE REFERENCED: Refer to "2-postgres1", "2-postgres2", "2-postgres3", "2-postgres4", "2-postgres5"**
  - Create a custom Agent check that submits a metric named my_metric with a random value between 0 and 1000.
      -**COMPLETED. Created a custom agent check in python that creates a random value between 0 & 1000 named "my_metric".**
      -**IMAGE REFERENCED: Refer to "3-customMetric1", "3-customMetric2"**
  - Change your check's collection interval so that it only submits the metric once every 45 seconds.
      -**COMPLETED. Added a wait timer in the agent check. **
      -**IMAGE REFERENCED: Refer to "4-customMetric1", "4-customMetric2", "4-customMetric3"**
  - Bonus Question Can you change the collection interval without modifying the Python check file you created?
      -**COMPLETED. Changed the collection interval with modifying the mymetric.yaml file to include the "min_collection_interval" parameter. **
      -**IMAGE REFERENCED: Refer to "5bonus-customMetric2","5bonus-customMetric2", "5bonus-customMetric3"** 
      
+++++++++++++++++      
Visualizing Data:
Utilize the Datadog API to create a Timeboard that contains:
  - Your custom metric scoped over your host.
  - Any metric from the Integration on your Database with the anomaly function applied.
  - Your custom metric with the rollup function applied to sum up all the points for the past hour into one bucket
      -**COMPLETED. Created a Timeboard via Datadog API with the above three metrics. **
      -**IMAGE REFERENCED: "Visualizing_Data_1", "Visualizing_Data_2".** 
Please be sure, when submitting your hiring challenge, to include the script that you've used to create this Timeboard.
  -**COMPLETED. Referenced here: ""Visualizing_Data_2"" and refer to uploaded script here: https://drive.google.com/open?id=1ug8WelXZw4IcX0VFr09_Ejx5oJDsIbiZ**

Once this is created, access the Dashboard from your Dashboard List in the UI:

  - Set the Timeboard's timeframe to the past 5 minutes
      -**COMPLETED. Refer to "Visualizing_Data_past5Mins".**
  - Take a snapshot of this graph and use the @ notation to send it to yourself.
      -**COMPLETED. Refer to "Visualizing_Data_3".**
  - Bonus Question: What is the Anomaly graph displaying?
      -**The anomaly graph is displaying a visualwhen a metric is behaving differently than it has in the past, taking into account trends including seasonal day-of-week and time-of-day patterns. In this case, it's displaying an anomaly of the database create table counts and noting it to be an abnormal spike. This is well-suited for metrics with strong trends and recurring patterns that are hard or impossible to monitor with threshold-based alerting.**

+++++++++++++++++
Monitoring Data
Since you’ve already caught your test metric going above 800 once, you don’t want to have to continually watch this dashboard to be alerted when it goes above 800 again. So let’s make life easier by creating a monitor.

Create a new Metric Monitor that watches the average of your custom metric (my_metric) and will alert if it’s above the following values over the past 5 minutes:
  - Warning threshold of 500
  - Alerting threshold of 800
  - And also ensure that it will notify you if there is No Data for this query over the past 10m.
Please configure the monitor’s message so that it will:
  - Send you an email whenever the monitor triggers.
  - Create different messages based on whether the monitor is in an Alert, Warning, or No Data state.
  - Include the metric value that caused the monitor to trigger and host ip when the Monitor triggers an Alert state.
      -**COMPLETED. Please see monitor definitions: "MonitoringData_1"
      
When this monitor sends you an email notification, take a screenshot of the email that it sends you.
      - **COMPLETED. Refer to "MonitoringData_0" for email screenshot.**
Bonus Question: Since this monitor is going to alert pretty often, you don’t want to be alerted when you are out of the office. Set up two scheduled downtimes for this monitor:
  - One that silences it from 7pm to 9am daily on M-F,
  - And one that silences it all day on Sat-Sun.
  - Make sure that your email is notified when you schedule the downtime and take a screenshot of that notification.
      -**COMPLETED. Refer to "MonitoringData_2", "MonitoringData_3", "MonitoringData_4"**

+++++++++++++++++      
Collecting APM Data:
Given the following Flask app (or any Python/Ruby/Go app of your choice) instrument this using Datadog’s APM solution:

Bonus Question: What is the difference between a Service and a Resource?
  - **A service is the set of the processes that are defined by the user when instrumenting with Datadog. In my app's case, the primary service is the sqlite service that is being tracked in its usage. A resource is the particular query to the service. In my app's case, these are the SQL queries as seen in the "APM_4" image.**

Provide a link and a screenshot of a Dashboard with both APM and Infrastructure Metrics.
   - **COMPLETED: Set up my python app with APM, and created the following dashboard called "Matt's Dashboard" that has both Infrastructure and APM metrics. Refer to "APM_1", "APM_2" and "APM_3". The current link to the dashboard is: https://app.datadoghq.com/dash/817934/matts-dashboard?live=true&page=0&is_auto=false&from_ts=1527033243068&to_ts=1527036843068&tile_size=l&fullscreen=false.** 
   
Please include your fully instrumented app in your submission, as well.
   - **COMPLETED: Please find the python app called 'scraper.py' in the repo. If hard to find, it's also here in the following link: https://drive.google.com/open?id=1ii4J6warzc9DqdSjqb4vQS2XMdaWiXsq. This is a python app that is using Twitter's API to pull in relevant targeted tweets, creating and storing the tweets in a database.** 
   
Final Question:
Datadog has been used in a lot of creative ways in the past. We’ve written some blog posts about using Datadog to monitor the NYC Subway System, Pokemon Go, and even office restroom availability!

Is there anything creative you would use Datadog for?
   - **I'd love to see how Datadog could monitor the spike of web traffic and its impact on site functionality (page loads, commenting, etc) on social sites like Reddit. I've seen this traffic take down a variety of services on the site itself, from popular AMA's, SuperBowl games, and premiere movie releases. It'd be great for them to be proactive, prevent outages and deprecation of core services **
