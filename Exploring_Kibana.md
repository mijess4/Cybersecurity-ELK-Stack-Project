## Activity File: Exploring Kibana

- You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly.


- Today, you notice something strange in the logs and you want to take a closer look.


- Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:


⚠ Heads Up: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file.

### Instructions

1. Add the sample web log data to Kibana.


2. Answer the following questions:


- In the last 7 days, how many unique visitors were located in India?

  250 Unique Visitors.

- In the last 24 hours, of the visitors from China, how many were using Mac OSX?

  9 Unique visitors in the last 24 hours using Mac OSX.

- In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?

  404 errors: 33.333%
  503 errors: 0%

- In the last 7 days, what country produced the majority of the traffic on the website?

  Bangladesh.

- Of the traffic that's coming from that country, what time of day had the highest amount of activity?

  12pm.

- List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).

  gz: compressed files created using the gzip tool.

  css: files that can help define font, size, color, spacing, border and location of HTML information on a webpage. They are downloaded with their .html counterparts and rendered by the browser.

  zip: A lossless compression format that may contain one or more files or directories that have been compressed.

  deb: a debian (Linux) Software Package file. These files are installed when using the apt package manager.

  rpm: a Red Hat Software Package file. RPM stands for Red Hat Package Manager.

  Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.

- Locate the time frame in the last 7 days with the most amount of bytes (activity).
- In your own words, is there anything that seems potentially strange about this activity?

  Irregular activity as one visitor is using a higher number of bytes than the average usage of all other users.

- Filter the data by this event.

- What is the timestamp for this event?

  Oct 28, 2021 @ 15:00:0 

- What kind of file was downloaded?

  gz file.

- From what country did this activity originate?

  China.

- What HTTP response codes were encountered by this visitor?

  200

- Switch to the Kibana Discover page to see more details about this activity.

- What is the source IP address of this activity?

  1.145.31.121

- What are the geo coordinates of this activity?

  “Lat”: 28.28980556, “lon”: -81.43708333

- What OS was the source machine running?

  Windows 8

- What is the full URL that was accessed?

  https://artifacts.elastic.co/downloads/kibana/kibana-6.3.2-linux-x86_64.tar.gz	

- From what website did the visitor's traffic originate?

  http://www.elastic-elastic-elastic.com/success/aleksandr-serebrov	

- Finish your investigation with a short overview of your insights.

- What do you think the user was doing?

  This event appears to be a user downloading Kibana.

- Was the file they downloaded malicious? If not, what is the file used for?

  Kibana packages are not typically malicious, but they could be.

- Is there anything that seems suspicious about this activity?

  The coordinates for source, destination  and geo coordinates do not match.

- Is any of the traffic you inspected potentially outside of compliance guidelines?

  Not if it is an administrator remotely accessing and performing the task. 
