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
The 'brightness' and 'input' keys represent so-called "Features" of a monitor. The values of those keys are the valeus that are either get or set by our scripts. 

```shell
ddcutil capabilities --sn=DEADBEEF
Model: Something
MCCS version: 2.2
Commands:
   Op Code: 01 (VCP Request)
   Op Code: 02 (VCP Response)
   Op Code: 03 (VCP Set)
   Op Code: 07 (Timing Request)
   Op Code: 0C (Save Settings)
   Op Code: E3 (Capabilities Reply)
   Op Code: F3 (Capabilities Request)
VCP Features:
   Feature: 02 (New control value)
   Feature: 04 (Restore factory defaults)
   Feature: 08 (Restore color defaults)
   Feature: 10 (Brightness)
   Feature: 12 (Contrast)
   Feature: 14 (Select color preset)
      Values:
         04: 5000 K
         05: 6500 K
         08: 9300 K
         0b: User 1
   Feature: 16 (Video gain: Red)
   Feature: 18 (Video gain: Green)
   Feature: 19 (Unrecognized feature)
   Feature: 1A (Video gain: Blue)
   Feature: 4D (Unrecognized feature)
      Values: 00 01 (interpretation unavailable)
   Feature: 4E (Unrecognized feature)
   Feature: 4F (Unrecognized feature)
   Feature: 52 (Active control)
   Feature: 59 (6 axis saturation: Red)
   Feature: 5A (6 axis saturation: Yellow)
   Feature: 5B (6 axis saturation: Green)
   Feature: 5C (6 axis saturation: Cyan)
   Feature: 5D (6 axis saturation: Blue)
   Feature: 5E (6 axis saturation: Magenta)
   Feature: 60 (Input Source)
      Values:
         01: VGA-1
         03: DVI-1
         0f: DisplayPort-1
         11: HDMI-1
         12: HDMI-2
   Feature: 62 (Audio speaker volume)
   Feature: 65 (Unrecognized feature)
   Feature: 67 (Unrecognized feature)
   Feature: 68 (Unrecognized feature)
   Feature: 69 (Unrecognized feature)
   Feature: 6A (Unrecognized feature)
   Feature: 6B (Backlight Level: White)
   Feature: 6C (Video black level: Red)
   Feature: 6E (Video black level: Green)
   Feature: 70 (Video black level: Blue)
   Feature: 72 (Gamma)
      Invalid gamma descriptor: 50 64 78 8c a0
   ...
```

'sn' - The serial number of the monitor. In theory this is unique. In practice...there are exceptions.
