# Let's Go Splunking

Week 18 Homework
Leo Katz

## The Need for Speed

Splunk search:
`source="server_speedtest.csv" | eval ratio='DOWNLOAD_MEGABITS'/'UPLOAD_MEGABITS' | sort _time | table _time IP_ADDRESS DOWNLOAD_MEGABITS UPLOAD_MEGABITS ratio`

4. Answer the following questions:
	- Based on the report created, what is the approximate date and time of the attack?
	ANSWER:	The attack took place on 2/23/20 at 14:30:00.  It was at this time that the Download speed began to drop sharply.  It was not until 2/23/20 at 23:30:00 that the speed returned to normal.
	
	- How long did it take your systems to recover?
	ANSWER:	It took the systems approximately 9 hours to recover.

Please ignore in the screenshots where I mistakenly labelled this exercise as HW 19.	
	- [Speed Test Report 1] (https://drive.google.com/file/d/1jHIFFLcBoZFDAcgSc4GIMeOudRrQyC_P/view?usp=sharing)
	- [Speed Test Report 2] (https://drive.google.com/file/d/1qQBDyzUO_aAL6sgEOiSMbwSGyNbNsuMc/view?usp=sharing)

## Are We Vulnerable?

Splunk search:
`source="nessus_logs.csv" host="nessus_logs_host" dest_ip="10.11.36.23" | eval CRITICAL=IF(severity="critical", "Critical", "Non-Critical") | stats count by CRITICAL`

	- [Nessus Alert 1] (https://drive.google.com/file/d/1fwAO651mZbEEOMhnjGootTLdk8vgtUpW/view?usp=sharing)
	- [Nessus Alert 2] (https://drive.google.com/file/d/1x-3LbMGq7kGByD_6FCGVXBGLQbTSJLD6/view?usp=sharing)

## Drawing the (Base)Line

Splunk search:
`source="Administrator_logs.csv" name="An account failed to log on"`

2. When did the brute force attack occur?
	ANSWER:	The attack took place on 2/21/20, starting at 09:00:00 and ending at 14:00:00.  
	
3. Determine a baseline of normal activity and a threshold that would alert if a brute force attack is occurring.
	ANSWER: 
	- The average quantity of normal log-ons in an hour is roughly 26.  
	- The quantity of log-ons during the brute force attack was 68 or more.
	Therefore, I set the threshold at 50 log-ons.  
	
	- [Brute Force Alert] (https://drive.google.com/file/d/1DqJ5yjwpU27EvbnJ8M0CT3oM_ywO1aip/view?usp=sharing)
