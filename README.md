# MalloDroid

MalloDroid is a small tool built on top of the [Androguard](https://github.com/androguard/androguard) reverse engineering framework able to analyze Android apps for broken TLS certificate validation.

This fork is a Python 3 converted and enhanced version of the original [MalloDroid](https://github.com/sfahl/mallodroid) combined with the patches provided by [@luckenzo](https://github.com/luckenzo/mallodroid).

## Installation

In order to use MalloDroid you have to install both Python 3 and Androguard

```bash
pip3 install -U androguard
```
and then clone this git repository by running
```bash
git clone https://github.com/stfbk/mallodroid.git
```

## Usage
Once in the right directory, run
```bash
./mallodroid.py <parameters>
```
where

### Parameters

- `-h|--help`   show the help message
- `-f|--file <PATH_TO_APK>` analyze the target apk
- `-x|--xml` shop XML output
- `-o <PATH_TO_FILE>` store the XML output to a file (\***New!**\*)
- `-j|--java` show Java code results for non-XML output
- `-d|--dir <DIR>` store in *DIR* decompiled apk's Java code for further analysis

example: `./mallodroid.py -f ExampleApp.apk -x`

## Internal API (\*New!\*)

You can now import MalloDroid with `import mallodroid` and execute it with `mallodroid.main(*args)`. 

`*args` should have:

* `args=['-args','--like','a','bash','call']`,

  *Demonstrative example:*

  `mallodroid.main(args=['-f','ExampleApp.apk','-x'])`

* `stdout_suppress=False`,

  Suppress all output sent to `STDOUT`. Default to `False`.

  *Demonstrative example:*

  `mallodroid.main(args=['-f','ExampleApp.apk','-x'],stdout_suppress=True)`

* `stderr_suppress=False`

  Suppress all output (errors) sent to `STDERR`. Default to `False`.

  *Demonstrative example:*

  `mallodroid.main(args=['-f','ExampleApp.apk','-x'],stderr_suppress=True)`

Complete example:

```python
import mallodroid

raw_results = mallodroid.main(args=['-f','ExampleApp.apk','-x'],stdout_suppress=False,stderr_suppress=True)

print(raw_results)
```

## License

As mandated by the [original script](https://github.com/sfahl/mallodroid/blob/master/mallodroid.py), MalloDroid is free software: you can redistribute it and/or modify it under the terms of the GNU Lesser General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. You may obtain a copy of the License at

```
https://www.gnu.org/licenses/lgpl-3.0.html
```

MalloDroid is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU Lesser General Public License for more details.
