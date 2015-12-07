# ZEROTEST [![PyPI](https://img.shields.io/pypi/v/zerotest.svg)](https://pypi.python.org/pypi/zerotest) [![Travis](https://img.shields.io/travis/jjyr/zerotest.svg)](https://travis-ci.org/jjyr/zerotest)

Zerotest makes it easy to test API server, start a micro proxy, send requests, and generate test code by these behaviours.

## Install
Stable version: `pip install zerotest`

Develop version: `pip install git+https://github.com/jjyr/zerotest.git`

**zerotest require python2.7 or 3.3+**

## Quick Start
1. Start a local proxy to capture http traffic `zerotest server https://api.github.com -f octocat.data`

2. Make few requests `curl -i http://localhost:7000/users/octocat`

3. Press `C-c` to exit local proxy

4. Generate test code `zerotest generate octocat.data --ignore-all-headers > test_octocat.py`

5. Type `py.test test_octocat.py` to run test

## Usage

Type `zerotest -h` to see help message

### Server

Start local proxy server

`zerotest server http://target-endpoint.com [-f] [record_file.data]`

Type `zerotest server -h` to see help message

### Generate

Generate python test code from record data (the file generated by local proxy)

`zerotest generate [options] > test_file.py`

#### Ignore specific headers in comparison

Use option `--ignore-headers [date server ...]` or `--ignore-all-headers` to ignore headers comparison

#### Ignore specific fields

Use `--fuzzy-match` enable fuzzy matching mode, compare data schema instead the data itself, 
or you can use `--ignore-fields [view_count ...]` to specific ignored fields

Type `zerotest generate -h` to see help message

### Replay

Generate test and run it with `pytest`

`zerotest replay [generate options] [--pytest] [pytest options]`

Type `zerotest replay -h` to see help message


## Develop
Export debug flag `ZEROTEST_DEBUG=true` to see verbose logs during program or test running.

## Contributors
[Contributors](https://github.com/jjyr/zerotest/graphs/contributors)

## Contribute
* Open issue if found bugs or some cool ideas
* Feel free to ask if have any questions
* Testing is very important for a test tool, commit your test file together with pull request
