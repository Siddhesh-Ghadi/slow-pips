# Slow Pips
Python3 script to get install timings of pip packages.

The script reads a `requirments.txt` file, records install time of each module from it & displays a sorted table based on timings. By default, it will look for `requirements.txt` file in `current working directory`, `-r` flag can be used to override this behavior by providing a file path. `-f` flag can be used to force reinstall of the module. The output formatting is inspired by a similar tool called [slow-deps](https://davidwalsh.name/slow-deps) which is for npm packages. 

## Usage

The script depends on pip3. Ensure it is present on the system.

```bash
# install required pip modules for running the script
pip3 install tqdm prettytable

# run the script
python3 slow-pips.py
```

## Help

```bash
$ python3 slow-pips.py -h
usage: slow-pips.py [-h] [-r REQUIRMENTS] [-f]

Script to get install timings of pip packages.

optional arguments:
  -h, --help            show this help message and exit
  -r REQUIRMENTS, --requirments REQUIRMENTS
                        requirments.txt file path
  -f, --force           force reinstall of the modules
```

## Example

```bash
$ cat requirments.txt
awscli
bottle
paste
boto
wheel
twine
markdown
python-slugify
python-bcrypt
arrow
redis
psutil
requests
requests-aws
numpy
```

```bash
$ python3 slow-pips.py -f
Using pip 9.0.3 from /usr/lib/python3.6/site-packages (python 3.6)

Analyzing 15 dependencies...
100%|███████████████████████████████████████████████████████████████████████████████████████████████████████| 15/15 [04:21<00:00, 17.41s/it]
Results
+----------------+------------+
|     Module     |    Time    |
+----------------+------------+
|     numpy      |  03m 18s   |
|    markdown    |  00m 16s   |
|     awscli     |  00m 14s   |
|     twine      | 00m 05s(F) |
|     redis      |  00m 04s   |
|     psutil     |  00m 03s   |
|  requests-aws  |  00m 02s   |
|     paste      |  00m 02s   |
| python-bcrypt  |  00m 02s   |
|      boto      |  00m 02s   |
|    requests    |  00m 01s   |
|     arrow      |  00m 01s   |
|     wheel      |  00m 01s   |
| python-slugify |  00m 01s   |
|     bottle     |  00m 01s   |
+----------------+------------+
Total Time Taken: 04m 21s
(F) in table represents failed installation.
```