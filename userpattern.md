
%title: Command-Line으로 탐색하는 사용자 패턴
%author: SK Planet Data Engineering Team 권정민
%date: 2015-08-27
%note: Run presentation with `mdp README.md` # https://github.com/visit1985/mdp

# UserPatternwithCommandLine

            __    __       _______. _______ .______         .______      ___   .___________..___________. _______ .______      .__   __.    ____    __    ____  __  .___________. __    __  
           |  |  |  |     /       ||   ____||   _  \        |   _  \    /   \  |           ||           ||   ____||   _  \     |  \ |  |    \   \  /  \  /   / |  | |           ||  |  |  | 
           |  |  |  |    |   (----`|  |__   |  |_)  |       |  |_)  |  /  ^  \ `---|  |----``---|  |----`|  |__   |  |_)  |    |   \|  |     \   \/    \/   /  |  | `---|  |----`|  |__|  | 
           |  |  |  |     \   \    |   __|  |      /        |   ___/  /  /_\  \    |  |         |  |     |   __|  |      /     |  . `  |      \            /   |  |     |  |     |   __   | 
           |  `--'  | .----)   |   |  |____ |  |\  \----.   |  |     /  _____  \   |  |         |  |     |  |____ |  |\  \----.|  |\   |       \    /\    /    |  |     |  |     |  |  |  | 
            \______/  |_______/    |_______|| _| `._____|   | _|    /__/     \__\  |__|         |__|     |_______|| _| `._____||__| \__|        \__/  \__/     |__|     |__|     |__|  |__| 
                                                                                                                                                                                            
             ______   ______   .___  ___. .___  ___.      ___      .__   __.  _______           __       __  .__   __.  _______    .___________.  ______     ______    __           _______.
            /      | /  __  \  |   \/   | |   \/   |     /   \     |  \ |  | |       \         |  |     |  | |  \ |  | |   ____|   |           | /  __  \   /  __  \  |  |         /       |
           |  ,----'|  |  |  | |  \  /  | |  \  /  |    /  ^  \    |   \|  | |  .--.  | ______ |  |     |  | |   \|  | |  |__      `---|  |----`|  |  |  | |  |  |  | |  |        |   (----`
           |  |     |  |  |  | |  |\/|  | |  |\/|  |   /  /_\  \   |  . `  | |  |  |  ||______||  |     |  | |  . `  | |   __|         |  |     |  |  |  | |  |  |  | |  |         \   \    
           |  `----.|  `--'  | |  |  |  | |  |  |  |  /  _____  \  |  |\   | |  '--'  |        |  `----.|  | |  |\   | |  |____        |  |     |  `--'  | |  `--'  | |  `----..----)   |   
            \______| \______/  |__|  |__| |__|  |__| /__/     \__\ |__| \__| |_______/         |_______||__| |__| \__| |_______|       |__|      \______/   \______/  |_______||_______/    
                                                                                                   
                                                                                                                                        
-> _*Command-Line으로 탐색하는 사용자 패턴*_ <- 

-> Data Engineering Team <-
-> 권정민 <-
-> jeongmin.kwon@sk.com <-

-> 2015-08-27 <-


-> _https://github.com/cojette/UserPatternwithCommandLine_ <-


------------------------------------------------------------------------------

# Outline


- Situation
- What is User Pattern?
- Simple Command-line tools
- Usage
- Conclusion


------------------------------------------------------------------------------

# Situation

+- 사용자들의 현황을 간단히 파악해야 할 때
|-- 신규 서비스 베타 테스트
|-- 로그 정의가 덜 된 상태에서 로그를 살펴볼 때
`-- 실험 및 테스트 후 현황 파악


------------------------------------------------------------------------------

# What is User Pattern?

- 강-약-약-중간-약-약-...
- 사용자들이 서비스를 사용하는 방식

- 5W 1H
┍━━━━━━━━━━━━━━━━━━━━━━━━━━┯━━━━━━━━━━━━━━━━┑
│    1차 (기본 지표)                                                          │      2차 (추가 분석)                       │  
├───────━━━━━━━━━━━──━━━━─━┼──────────━━━━━━┤
│ - Who : 사용자 (user id, ip... )                                         |  - Why : 왜 (purpose, target ...)       |
 |  - When : 언제 (timestamp)                                              |                                                     |
 |  - Where : 어디서 (page_id, action_id, category ... )           |                                                     |
 |  - What : 무엇을 (login, buy, action... )                              |                                                     |
 |  - How : 어떻게 (purchase method, device, reference ...)    |                                                     |
┕━━━━━━━━━━━━━━━━━━━━━━━━━━┷━━━━━━━━━━━━━━━━┙

- 5W로 사용자 패턴을 만들어서 확인하는 것만으로도 이후 추가 분석의 방향을 결정할 수 있음. 




------------------------------------------------------------------------------
# What can you know with User Pattern?

- - 전체 사용자 현황
 - 기본 지표의 시계열 파악
 - 요일별, 일별, 시간별 사용자 수
 - 컨텐츠별 사용자 수 및 접속 시간
 - 개별 사용자 현황
 - 서비스 접속 주기
 - 요일별, 일별, 시간별 사용 컨텐츠 및 사용 시간
 - 외부 데이터의 적합도 파악


 
-------------------------------------------------------------------------------
# Why Command Line?

- Agile

- Augmenting

- Scalable

- Extensible

- Ubiquitous


----------------------------------------------------------------------------------
# 5 Steps of Data Analysis

- Data Collection

- Data Cleansing

- Data Exploration

- Data Modeling

- Data interpretation


------------------------------------------------------------------------------
# Data Wrangling with .csv

- csv (https://ko.wikipedia.org/wiki/CSV_(파일_형식))
 - original : comma-separated values 
 - usual: character-separated values (included tab, other delimeter)
 - basic text log file format 

- csvkit (https://github.com/onyxfish/csvkit)
 - suite of utilities for working with cvs format
 - install: sudo apt-get install 


-------------------------------------------------------------------------------
# Data Collection with Command Line

- copy, mv, ...

- Controlling xlsx : in2csv
$ in2csv data/log_sample.xlsx > data/log_sample.csv

- Database : sql2csv
$ sql2csv --db 'sqlite:///data/iris.db' --query 'SELECT * FROM iris limit 5'

- Internet Download : curl
vagrant@data-science-toolbox:~$  curl -L -O https://github.com/onyxfish/csvkit/raw/master/examples/realdata/ne_1033_data.xlsx
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   158    0   158    0     0     24      0 --:--:--  0:00:06 --:--:--    39
100 65331  100 65331    0     0   4978      0  0:00:13  0:00:13 --:--:-- 15918
vagrant@data-science-toolbox:~$ 

---------------------
# Data Cleansing & Processing with Command Line

- Data check : csvlook + head
$ head -n 5 examples/testfixed_converted.csv | csvlook

- Syntax error check: csvclean

- Subset from xlsx : csvcut
$ csvcut -c begin, user_id, cont_id | csvlook

- Filtering: grep, csvgrep
$ csvgrep -c 1 -m ILLINOIS examples/realdata/FY09_EDU_Recipients_by_State.csv


- Controlling xlsx : in2csv
$ in2csv data/log_sample.xlsx > data/log_sample.csv

- Subset from xlsx : csvcut 
$ in2csv data/log_sample.xlsx | head | csvcut -c begin, user_id, cont_id | csvlook

- Database : sql2csv
$ sql2csv --db 'sqlite:///data/iris.db' --query 'SELECT * FROM iris limit 5'

- Internet Download : curl
$curl -s http://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data | head -n 5

------------------------------------------------------------------------------
# Data Exploration with Command Line

- Simple statistics : csvstat
$ csvstat --freq examples/realdata/FY09_EDU_Recipients_by_State.csv

  1. State Name: None
  2. State Abbreviate: None
  3. Code: None
  4. Montgomery GI Bill-Active Duty: 3548.0
  5. Montgomery GI Bill- Selective Reserve: 1019.0
  6. Dependents' Educational Assistance: 1261.0
  7. Reserve Educational Assistance Program: 715.0
  8. Post-Vietnam Era Veteran's Educational Assistance Program: 6.0
  9. TOTAL: 6520.0
 10. _unnamed: None



- Exploration with SQL : csvsql
$ csvsql --query  "select m.usda_id, avg(i.sepal_length) as mean_sepal_length from iris as i join irismeta as m on (i.species = m.species) group by m.species" examples/iris.csv examples/irismeta.csv

- Exploration with python : csvpy
$ csvpy examples/dummy.csv
Welcome! "examples/dummy.csv" has been loaded in a CSVKitReader object named "reader".
>>> reader.next()
[u'a', u'b', u'c']



------------------------------------------------------------------------------

# Data Modeling

- Other Command-line tools: BigML ...

- Programming pipeline : parallel with modeling code (python, R.. )

$ R CMD BATCH  sampleml.R
$ R -e 'hist(demo.data)' > hist.png


------------------------------------------------------------------------------

# Data I


Assume line is "/home/cojette/data.csv"

- `{}` : /home/jeroen/data.csv
- `{.}` : /home/jeroen/data
- `{/}` : data.csv
- `{/.}` : data

Example:

$ echo '/home/jeroen/data.csv' | parallel --dryrun "tar -czf {/.}.tar.gz {}"
tar -czvf data.tar.gz /home/jeroen/data.csv

Other placeholders:

- `{1}` : first argument
- `{2}` : second argument
- `{#}` : job number

------------------------------------------------------------------------------

# Usage: Named placeholders from CSV file


Use `head` and `csvlook` (from csvkit) to inspect data set:

$ head -n 6 tips.csv | csvlook
|--------+------+--------+--------+-----+--------+-------|
| bill | tip | sex | smoker | day | time | size |
|--------+------+--------+--------+-----+--------+-------|
| 16.99 | 1.01 | Female | No | Sun | Dinner | 2 |
| 10.34 | 1.66 | Male | No | Sun | Dinner | 3 |
| 21.01 | 3.5 | Male | No | Sun | Dinner | 3 |
| 23.68 | 3.31 | Male | No | Sun | Dinner | 2 |
| 24.59 | 3.61 | Female | No | Sun | Dinner | 4 |
|--------+------+--------+--------+-----+--------+-------|
^

$ head -n 6 tips.csv | parallel -C, --header : \
> "echo On {day}, {size} people had {time} for a total of '$'{bill}"
On Sun, 2 people had Dinner for a total of $16.99
On Sun, 3 people had Dinner for a total of $10.34
On Sun, 3 people had Dinner for a total of $21.01
On Sun, 2 people had Dinner for a total of $23.68
On Sun, 4 people had Dinner for a total of $24.59


------------------------------------------------------------------------------

# Usage: Specifying number of concurrent jobs


By default one job per core.

Just 10 jobs:

$ cat input | parallel --jobs 10

Twice the number of cores:

$ cat input | parallel --jobs 200%

Sometimes you only want one job at a time:

$ cat input | parallel -j1

Tip: use `htop` to see if you're maxing out your CPUs

------------------------------------------------------------------------------

# Example: Calling The New York Times API


Cartesian product of year and page:

$ parallel -j1 --progress --delay 0.1 --results results "curl -sL " \
> "'http://api.nytimes.com/svc/search/v2/articlesearch.json?q=New+'"\
> "'York+Fashion+Week&begin_date={1}0101&end_date={1}1231&page={2}'"\
> "'&api-key=${KEY}'" ::: {2009..2013} ::: {0..99} > /dev/null
^

Computers / CPU cores / Max jobs to run
1:local / 4 / 1

Computer:jobs running/jobs completed/%of started jobs/Average seconds to
complete
local:1/9/100%/0.4s

------------------------------------------------------------------------------

# Example: Calling The New York Times API


Structured output:

$ tree results | head
results
`-- 1
|-- 2009
| `-- 2
| |-- 0
| | |-- stderr
| | `-- stdout
| |-- 1
| | |-- stderr
| | `-- stdout

Combine output using `cat`:

$ cat results/1/*/2/*/stdout

------------------------------------------------------------------------------

# Usage: Executing pipeline on remote instances


Get hostname of all instances:

$ parallel --nonall --sshloginfile instances hostname
ip-172-31-23-204
ip-172-31-23-205

Install GNU Parallel:

$ parallel --nonall --slf instances "sudo apt-get install -y parallel"

------------------------------------------------------------------------------

# Aside: Obtain list of EC2 instances


$ aws ec2 describe-instances | jq '.Reservations[].Instances[] | '\
> '{public_dns: .PublicDnsName, state: .State.Name}'
{
"state": "running",
"public_dns": "ec2-54-88-122-140.compute-1.amazonaws.com"
}
{
"state": "stopped",
"public_dns": null
}


$ aws ec2 describe-instances | jq -r '.Reservations[].Instances[] | '\
> 'select(.State.Name=="running") | .PublicDnsName' > instances
$ cat instances
ec2-54-88-122-140.compute-1.amazonaws.com
ec2-54-88-89-208.compute-1.amazonaws.com

------------------------------------------------------------------------------

# Parallelizing your Python or R code


Six-step recipe to create a reusable command-line tool:

1. Copy and paste code into a file
2. Add execute permissions using `chmod`
3. Define a so-called shebang
4. Remove the fixed input part
5. Add a parameter
6. Optionally extend your PATH


------------------------------------------------------------------------------

# Parallelizing your Python or R code


Top n words in Python:

#!/usr/bin/env python
import re
import sys
from collections import Counter
num_words = int(sys.argv[1])
text = sys.stdin.read().lower()
words = re.split('\W+', text)
cnt = Counter(words)
for word, count in cnt.most_common(num_words):
print "%7d %s" % (count, word)

^
$ cat data/76.txt | ./top-words.py 3
6441 and
5082 the

^
$ ls data/*.txt | parallel --tag "cat {} | ./top-words.py 10"


------------------------------------------------------------------------------

# Parallelizing your Python or R code


Top n words in R:

#!/usr/bin/env Rscript
n <- as.integer(commandArgs(trailingOnly = TRUE))
f <- file("stdin")
lines <- readLines(f)
words <- tolower(unlist(strsplit(lines, "\\W+")))
counts <- sort(table(words), decreasing = TRUE)
counts_n <- counts[1:n]
cat(sprintf("%7d %s\n", counts_n, names(counts_n)), sep = "")
close(f)

^
$ cat data/76.txt | ./top-words.R 3
6441 and
5082 the
3666 i

^
$ ls data/*.txt | parallel --tag "cat {} | ./top-words.R 10"

------------------------------------------------------------------------------

# Example: Using your command-line tool remotely


Custom command-line tool that outputs sum of numbers:

$ cat sum
#!/usr/bin/env bash
paste -sd+ | bc
^

$ chmod u+x sum
^

$ seq 3
1
2
3
$ seq 3 | ./sum
6

^
$ seq 1000 | parallel -N100 --basefile sum --pipe --slf instances './sum' |
> ./sum
500500


------------------------------------------------------------------------------

# Conclusion


- Handful command-line tools for simple data analysis 
- Has a bit of a learning curve
- Handful of options cover 90% of use cases
- Can speed up ordinary pipelines and code


------------------------------------------------------------------------------

# Reference
## Data Science at the Command Line

- Author:
- Published by O'Reilly in October 2014
- Overview of all tools on _http://datascienceatthecommandline.com_



