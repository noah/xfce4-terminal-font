#!/usr/bin/env python
# -*- coding: utf-8 -*-

# xfce4-terminal-font.py -- programmatically change the font size of an
# xfce4-terminal.
#
# Copyright © 2013 Noah K. Tilton <noahktilton@gmail.com>
#
# License: GPLv2 or later.

# working with xfce4-terminal-0.6.2-1

if __name__ == "__main__":

    import sys

    PM = ["+", "-"]
    if len(sys.argv) != 2 or sys.argv[1] not in PM:
        sys.exit("Usage {0} {1}".format(sys.argv[0], "/".join(PM)))

    delta = int("{0}1".format(sys.argv[1]))

    import os
    import re
    from configparser import RawConfigParser

    # read input file
    f = os.path.join(os.environ["XDG_CONFIG_HOME"], "xfce4", "terminal", "terminalrc")
    c = RawConfigParser()
    c.optionxform = str # make keys case-sensitive
    c.read(f)
    font, size = re.search(r'^(.*) (\d+)$', c['Configuration']['FontName']).group(1, 2)
    size = int(size) + delta
    c['Configuration']['FontName'] = "{0} {1}".format(font, size)

    with open(f, 'w') as c_new:
        c.write(c_new)
