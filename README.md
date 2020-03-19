# Script: ripiRule.py Extract Objects from Config Files

Effectively the same as ripconfig.py, but use only for iRules or configuration objects which end with `\n}\n}`

```
}
}
```

# Script: ripconfig.py Extract Objects from Config Files

This script will parse through BIG-IP configuration files and extract common elements.

Ouptut will look like `tmsh list ...`

## Example:

Extract all BIG-IP DNS WideIP's from a given configuration file.

~~~ bash
./ripconfig.py bigip_gtm.conf -s 'gtm wideip'
gtm wideip a /Common/blount.jadams {
    load-balancing-decision-log-verbosity { pool-selection pool-traversal pool-member-selection pool-member-traversal }
    pools {
        /Common/blount_pool {
            order 0
        }
    }
}

gtm wideip a /Common/ripconfig.py { }
~~~

## Usage:
~~~ bash
./ripconfig.py -s 'gtm wideip' /var/tmp/generated-bigip_gtm.conf
~~~

~~~ bash
ripconfig.py -h
usage: ripconfig.py [-h] [-d DELIMITER] -s STRING
                    [configfile [configfile ...]]
  
positional arguments:
  configfile            Config File to Parse
  
optional arguments:
  -h, --help            show this help message and exit
  -d DELIMITER, --delimiter DELIMITER
                        Ending Delimiter; Default: ^}
  -s STRING, --string STRING
                        regex string to search in config file for
~~~


## Error Handling:

Built-in error handling should allow for straight-forward troubleshooting of this script.

~~~ bash
$ ripconfig.py
usage: ripconfig.py [-h] [-d DELIMITER] -s STRING
                    [configfile [configfile ...]]
ripconfig.py: error: argument -s/--string is required
~~~
