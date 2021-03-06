Clickatell Python Library
================================

Master: [![Build Status](https://secure.travis-ci.org/arcturial/clickatell-python.png?branch=master)](http://travis-ci.org/arcturial/clickatell-python)

This library allows easy access to connecting the [Clickatell's](http://www.clickatell.com) different messenging API's.

The library supports both version **2** and **3** of Python.

1. Installation
------------------

You can install this library via PIP as part of you requirements file.

```
pip install clickatell
```

[Clickatell Python PyPI](https://pypi.python.org/pypi?name=clickatell&version=0.0.1&:action=display)

2. Usage
------------------

The library currently supports the `Http` and `Rest` protocols.

### HTTP API

``` python
from clickatell.http import Http

clickatell = Http(username, password, apiID)
response = clickatell.sendMessage(['1111111111'], "My Message")

for entry in response:
    print(entry['id'])
    # entry['id']
    # entry['destination']
    # entry['error']
    # entry['errorCode']
```

### REST API

``` python
from clickatell.rest import Rest

clickatell = Rest(token);
response = clickatell.sendMessage(['1111111111'], "My Message")

for entry in response:
    print(entry['id'])
    # entry['id']
    # entry['destination']
    # entry['error']
    # entry['errorCode']
```

### Sending to multiple numbers

The `sendMessage` call `to` parameter can take an array of numbers. If you specify only a single number like `clickatell.sendMessage(1111111111, "Message")` the library will automatically convert it to an array for your convenience.

3. Supported API calls
------------------

The available calls are defined in the `clickatell.Transport` interface.

``` python

def sendMessage(self, to, message, extra={})

def getBalance(self)

def stopMessage(self, apiMsgId)

def queryMessage(self, apiMsgId)

def routeCoverage(self, msisdn)

def getMessageCharge(self, apiMsgId)

```

4. Dealing with extra parameters in sendMessage
--------------------------------------

For usability purposes the `sendMessage` call focuses on the recipients and the content. In order to specify and of the additional parameters defined
in the [Clickatell document](http://www.clickatell.com), you can use the `extra` parameter and pass them as a dictionary.