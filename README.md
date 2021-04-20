# What am I?
Just some basic scripts to control my monitors from the command line

# How do I work?
Barely! And that's being generous. 

## But seriously, how does this work?

The underlying magic is [ddcutil](https://www.ddcutil.com/).

The rest was just painful, *painful* trial and error.

The monitors are defined as a dictionary of the form
```python
'MonitorName': {
  'sn': 'ABCDEFG',
  'brightness': 'xAA',
  'input': 'xBB',
  'inputs': {
    'DVI-1': 'x01',
    'HDMI-1': 'x11',
  }
}
```
