# netbox-scanner
A scanner util for NetBox, because certain networks can be updated automagically.  ;)

## Installation
`netbox-scanner` is available as a Python package via PyPi, so you can install it using `pip`:

    $ pip3 install netbox-scanner

Note that `netbox-scanner` will require Nmap and an instance of NetBox ready to use.

## Usage
`netbox-scanner` can be used both in your programs or as a script to be used in shell.  To use `netbox-scanner` as a script, edit `netbox-scanner/config.py` with your setup, and run the command below:

    $ netbox-scanner.py

`netbox-scanner` will do the following tasks:

1. It will scan all networks defined in `netbox-scanner/config.py`.
2. For each discovered host it will:
    1. If host is in NetBox, description is different, and tag is set as defined in `netbox-scanner/config.py/TAG`, it'll be updated.
    2. If host is not in NetBox, it'll be created.
3. It will iterate through each network to find and delete hosts registered in NetBox that are not responsible to scan, and have the tag `netbox-scanner/config.py/TAG`.

This way, if some hosts in your networks that are monitored via `netbox-scanner` are eventually down, but you don't want to delete them, just make sure that it doesn't have the tag as set in `netbox-scanner/config.py/TAG`.

Of course, you can use `cron` to automatically run `netbox-scanner`.

## License
`netbox-scanner` is licensed under a MIT license --read `LICENSE` file for more information.
