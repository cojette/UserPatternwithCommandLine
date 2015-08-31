

-> The User Pattern Analysis with <-
 
	  ______   ______   .___  ___. .___  ___.      ___      .__   __.  _______         __       __  .__   __.  _______           
	 /      | /  __  \  |   \/   | |   \/   |     /   \     |  \ |  | |       \       |  |     |  | |  \ |  | |   ____|          
	|  ,----'|  |  |  | |  \  /  | |  \  /  |    /  ^  \    |   \|  | |  .--.  |______|  |     |  | |   \|  | |  |__             
	|  |     |  |  |  | |  |\/|  | |  |\/|  |   /  /_\  \   |  . `  | |  |  |  |______|  |     |  | |  . `  | |   __|            
	|  `----.|  `--'  | |  |  |  | |  |  |  |  /  _____  \  |  |\   | |  '--'  |      |  `----.|  | |  |\   | |  |____           
	 \______| \______/  |__|  |__| |__|  |__| /__/     \__\ |__| \__| |_______/       |_______||__| |__| \__| |_______|   




-> JeongMin Kwon <-

-> cojette@gmail.com <-


-> 2015-08-27 <-

-> _http://bit.ly/1NINdeF_ <-

------------------------------------------------------------------------------


# Outline


- Situation

- What is User Pattern?

- Case with Simple Command-line tools

- Conclusion

------------------------------------------------------------------------------


# Situation


- Grasping user/service status

- Beta-test for new services

- Examining poor-defined log

- Experiment/Test Evaluation

- Development based data analysis 


 > For myself only : *Ad-hoc data analysis *

------------------------------------------------------------------------------


# What is User Pattern?

- regular and predictuable action of users 

- 5W1H

┍━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┯━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┑
│    Basic Indicator                                       │      Predict        	       │  
├───────━━━━━━━━━━━──━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━─┼─────────━━━━━━━━━━━━━━━━━━━━━━━━━━─━━━━━━┤
│ - Who :user id, ip...                         |  - Why : purpose, target ...       |
| - When : timestamp                                 |                                          |
| - Where : page_id, action_id, category ...     |                                          |
| - What : login, buy, action...                   |                                          |
| - How : purchase method, device, reference ...   |                                          |
┕━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┷━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┙

 - Basic Indicators cover lots of decision problems

----------------------------------------------------------------------------------------------------


# What can you know with User Pattern?


- Total user status

- Time series insights of metrics

- user count and durations

- Understanding each user

- Service login term

- contents and duration per each weekday, hour, month

- ...and many more

-----------------------------------------------------------------------------------


# Example : Item purchase log analysis


- Background: Launching new temporary items in a small mobile game
 
- Goal: Understanding users shopping time, items users react
  - If users do not react to new items, new items will be removed

- log: flat file

	$ head tr_sample.csv
	id,type,user_id,description,del_item_id,gem,bean,recip,recdate
	1963179,13,13465,,200002,0,0,113.32.91.206,2015-07-01 00:00:01.000000
	1963180,9,2910, 산책  ,,2,0,211.187.227.229,2015-07-01 00:00:01.000000
	1963181,9,12341,건강관리,,0,110,202.43.69.142,2015-07-01 00:00:01.000000


 - Details: log overview, sell count, sell status per hour and users, and more


------------------------------------------------------------------------------


# 5 Steps of Data Analysis


- Data Collection

- Data Cleansing 

- Data Exploration 

- Data Modeling 

- Data interpretation 

------------------------------------------------------------------------------


# 5 Steps of Data Analysis


- Data Collection 

- Data Cleansing 

- Data Exploration 


  > Data Wrangling 
	
  *- Command Line Tool: Ubiquitous, Extensible, Agile*

-------------------------------------------------------------------------------


# Data Wrangling with .csv


- csv (http://www.ietf.org/rfc/rfc4180.txt)

 - original : comma-separated values 

 - usual: character-separated values (included tab, other delimeter)

 - basic text log file format 


- csvkit (https://github.com/onyxfish/csvkit)

 - suite of utilities for working with cvs format

 - install: sudo apt-get install 

-------------------------------------------------------------------------------


# Data Collection with Command Line


- copy, mv, ...

- Internet Download : curl

    $  curl -L -O https://github.com/cojette/UserPatternwithCommandLine/log_sample.xlsx

      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100   158    0   158    0     0     24      0 --:--:--  0:00:06 --:--:--    39
    100 65331  100 65331    0     0   4978      0  0:00:13  0:00:13 --:--:-- 15918


- Controlling xlsx : in2csv

    $ in2csv data/log_sample.xlsx > data/log_sample.csv


- Database : sql2csv

    $ sql2csv --db 'sqlite:///data/iris.db' --query 'SELECT * FROM iris limit 5'

---------------------------------------------------------------------------------------------------------------------------

 
# Data Cleansing & Processing with Command Line


- Data check : csvlook + head

	$ head -n 5 tr_sample.csv |csvlook
    	|----------+------+---------+------------------+-------------+-----+------+-----------------+-----------------------------|
    	|  id      | type | user_id |    description   | del_item_id | gem | bean | recip           | recdate                     |
    	|----------+------+---------+------------------+-------------+-----+------+-----------------+-----------------------------|
    	|  1963179 | 13   | 13465   |       	       | 200002      | 0   | 0    | 113.32..06      | 2015-07-01 00:00:01.000000  |
    	|  1963180 | 9    | 2910    | 산책             |             | 2   | 0    | 211.187..29     | 2015-07-01 00:00:01.000000  |
    	|  1963181 | 9    | 12341   | 건강관리         |             | 0   | 110  | 202.43..42      | 2015-07-01 00:00:01.000000  |
    	|  1963182 | 9    | 6286    | 뮤지컬           |             | 0   | 1000 | 218.153..281    | 2015-07-01 00:00:04.000000  |
    	|----------+------+---------+------------------+-------------+-----+------+-----------------+-----------------------------|


- Syntax error check: csvclean

	$ csvclean tr_sample.csv
	No errors.

----------------------------------------------------------------------------------------------------

 
# Data Cleansing & Processing with Command Line


- Subset from xlsx : csvcut

	$ csvcut -c 1,3,5,6,9  tr_sample.csv | csvlook |head
	|----------+---------+-------------+-----+-----------------------------|
	|  id      | user_id | del_item_id | gem | recdate                     |
	|----------+---------+-------------+-----+-----------------------------|
	|  1963179 | 13465   | 200002      | 0   | 2015-07-01 00:00:01.000000  |
	|  1963180 | 2910    |             | 2   | 2015-07-01 00:00:01.000000  |
	|  1963181 | 12341   |             | 0   | 2015-07-01 00:00:01.000000  |
	|  1963182 | 6286    |             | 0   | 2015-07-01 00:00:04.000000  |


- Filtering: grep, csvgrep

	$ csvgrep -c 5 -m 200003 tr_sample.csv |head -n 3 | csvlook
	|----------+------+---------+-------------+-------------+-----+------+-----------+-----------------------------|
	|  id      | type | user_id | description | del_item_id | gem | bean | recip     | recdate                     |
	|----------+------+---------+-------------+-------------+-----+------+-----------+-----------------------------|
	|  1963185 | 13   | 7410    |             | 200003      | 0   | 0    | 223.18..3 | 2015-07-01 00:00:05.000000  |
	|  1963188 | 13   | 7410    |             | 200003      | 0   | 0    | 223.18..3 | 2015-07-01 00:00:06.000000  |
	|----------+------+---------+-------------+-------------+-----+------+-----------+-----------------------------|

------------------------------------------------------------------------------


# Data Exploration with Command Line


- Simple statistics : csvstat

	$ csvstat --unique tr_sample.csv 
  	1. id: 500
  	2. type: 4
  	3. user_id: 110
  	4. description: 82

	$ csvstat --freq tr_sample.csv
	1. id: { "1963208": 1, "1963209": 1, "1963204": 1, "1963205": 1, "1963206": 1 }
	2. type: { "9": 332, "13": 98, "4": 69, "12": 1 }
	3. user_id: { "10684": 24, "2910": 19, "231": 13, "12778": 12, "11124": 12 }
	4. description: { "보너스": 78, "룰렛": 75, "건강관리": 12, "토크": 11, "보너스": 9 }

------------------------------------------------------------------------------


# Data Exploration with Command Line


- Exploration with SQL : csvsql
	
		$ csvsql --query "select substr(recdate, 15,2) as hour, count(1) 
		> from tr_sample group by substr(recdate, 15,2)" tr_sample.csv | csvlook
		|-------+-----------|
		|  hour | count(1)  |
		|-------+-----------|
		|  00   | 108       |
		|  01   | 122       |
		|  02   | 119       |
		|  03   | 98        |
		|  04   | 53        |
		|-------+-----------|


- Exploration with Python : csvpy
	
	$csvpy tr_sample.csv
	Welcome! "tr_sample.csv" has been loaded in a CSVKitReader object named "reader".
	In [1]: reader.next()
	Out[1]: 
	[u'1963179',
	 u'13',
	 u'13465',

------------------------------------------------------------------------------


# More Exploration

- Check users who bought items 2 or more times : items they bought, reaction for new items

	$ csvsql --query "select user_id from (select user_id, count(1) as cnt from tr_sample group by user_id)
	> where cnt >=2" tr_sample.csv >tr_user.csv

	$ csvjoin -c "user_id, user_id" tr_user.csv tr_sample.csv >tr_up.csv

	$ head -n 5 tr_up.csv |csvlook
	|----------+---------+------+---------+-------------+-------------+-----+------+------------+-----------------------------|
	|  user_id | id      | type | user_id | description | del_item_id | gem | bean | recip      | recdate                     |
	|----------+---------+------+---------+-------------+-------------+-----+------+------------+-----------------------------|
	|  231     | 1963189 | 9    | 231     | SNS포스팅   |             | 0   | -90  | 180.70..18 | 2015-07-01 00:00:06.000000  |
	|  231     | 1963204 | 13   | 231     |             | 200004      | 0   | 0    | 180.70..18 | 2015-07-01 00:00:16.000000  |
	|  231     | 1963235 | 9    | 231     | 토크        |             | 0   | 210  | 180.70..18 | 2015-07-01 00:00:38.000000  |
	|  231     | 1963236 | 9    | 231     | 건강관리    |             | 0   | 110  | 180.70..18 | 2015-07-01 00:00:38.000000  |
	|----------+---------+------+---------+-------------+-------------+-----+------+------------+-----------------------------|

---------------------------------------------------------------------------------


# More Exploration


	$ csvstat tr_up.csv
  	1. user_id
		<type 'int'>
		Nulls: False
		Min: 231
		Max: 13482
		Sum: 4303878
		Mean: 8855.71604938

	$ csvsql --query "select substr(recdate, 15, 2) as hour, del_item_id, count(1) as cnt from tr_up 
	> where length(del_item_id) > 2 group by substr(recdate, 15, 2) , del_item_id" tr_up.csv |csvlook
	|-------+-------------+------|
	|  hour | del_item_id | cnt  |
	|-------+-------------+------|
	|  00   | 200001      | 3    |
	|  00   | 200002      | 3    |
	|  00   | 200003      | 11   |
	|  00   | 200004      | 3    |

--------------------------------------------------------------------------------


# Data Modeling


- Other Command-line tools: BigML ...


- Programming pipeline : modeling code (python, R.. )

	$ R CMD BATCH  sampleml.R
	$ R -e 'hist(demo.data)' > hist.png
  
  - parallizing modeling code: parallel 

	$ ls data/*.txt | parallel --tag "cat {} | ./user_cluster.R 10"


- Pandashells: shell pipeline with the statistical and visualization tools of the python data-stack
 (https://github.com/robdmc/pandashells)

	$ p.example_data -d tips | p.plot -x total_bill -y tip -s 'o' --title 'Tip Vs Bill' > test.png

---------------------------------------------------------------------------------


# Conclusion


- Data Analysis: Back To The Basic

- User Pattern : Useful, important and easy 

- csvkit: Handful command-line tools for simple data analysis 

 - Handful of options cover 90% of use cases

- Useful for Ad-hoc analysis : Can speed up ordinary pipelines and code


------------------------------------------------------------------------------


# Reference


## Data Science at the Command Line

- Author: Jeroen Janssens 

- Published by O'Reilly in October 2014

- Overview of all tools on _http://datascienceatthecommandline.com_


## csvkit

- csv*** --help


## pandashells 

-> _Thank you for listening._ <-
