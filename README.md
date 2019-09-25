# LearningPython
Basics of Python

### Table of Contents
+ Circumference
+ Area Code
+ Gene Name

## Circumference
```
#!/usr/bin/python
import sys
import re
pi = 3.14159
r = 3
radius = str( 2 * pi * r)
print ('The circumference of a circle of radius ' + str(r) + ' is ' + radius)
```
## Area Code
```
#!/usr/bin/python
import sys
import re
phone = '602-343-8747'
match = re.match(r'(\d\d\d)' ,str(phone))
if match:
    print ('The area code is: ' + match.group(1))
```
## Gene Name
### Installation
First, download the file, Homo_sapiens.GRCh37.75.gtf.gz, from http://ftp.ensembl.org/pub/release-75/gtf/homo_sapiens using wget, and place this file within a directory called data within your home directory. Unzip this file with gunzip, gunzip Homo_sapiens.GRCh37.75.gtf.gz
### Usage
Run with ./gene_name.py ~/data/Homo_sapiens.GRCh37.75.gtf

```
#!/usr/bin/python
import sys 
import re
import fileinput
my_file= sys.argv[1]
for each_line_of_text in fileinput.input(my_file):
    if re.match(r'.*\t.*\tgene\t', each_line_of_text):
        gene_name_matches = re.findall('gene_name \"(.*?)\"', each_line_of_text)
        match = re.search(r'(\d)+(\s+)(\w+)(\s+)(\w+)(\s+)(\w+)(\s+)(\w+)(\s+)', each_line_of_text)
        chr_match = match.group(1)
        startPos_matches = match.group(7)
        endPos_matches = match.group(9)

        gene_name_matches = (re.sub('(\[\')|(\'\])', '\"', str(gene_name_matches)))

        print ('{' + 'geneName:' + str(gene_name_matches) + ',' + 'chr:' + str(chr_match) + ',' + 'startPos:' + str(startPos_matches) + ',' + 'endPos:' + str(endPos_matches) + '}')
```

