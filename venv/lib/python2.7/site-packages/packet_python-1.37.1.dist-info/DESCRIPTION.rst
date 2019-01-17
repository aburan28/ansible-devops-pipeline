Packet
======

A Python client for the Packet API.

.. figure:: https://travis-ci.org/packethost/packet-python.svg?branch=master
   :alt: Build Status

   travis build status badge

Installation
------------

The packet python api library can be installed using pip:
``pip install packet-python``

Package information available here:

https://pypi.python.org/pypi/packet-python

Documentation
-------------

Full Packet API documenation is available here:
https://www.packet.net/developers/api/

Examples
--------

List projects
~~~~~~~~~~~~~

.. code:: python

    import packet
    manager = packet.Manager(auth_token="yourapiauthtoken")

    projects = manager.list_projects()
    for project in projects:
        print(project)

List plans
~~~~~~~~~~

.. code:: python

    import packet
    manager = packet.Manager(auth_token="yourapiauthtoken")

    plans = manager.list_plans()
    for plan in plans:
        print(plan)
        if 'cpus' in plan.specs:
            print(plan.specs['cpus'][0]['count'])

Creating a Device
~~~~~~~~~~~~~~~~~

.. code:: python

    import packet
    manager = packet.Manager(auth_token="yourapiauthtoken")

    device = manager.create_device(project_id='project-id',
                                   hostname='node-name-of-your-choice',
                                   plan='baremetal_1', facility='ewr1',
                                   operating_system='ubuntu_14_04')
    print(device)

Checking the status and rebooting a Device
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    import packet
    manager = packet.Manager(auth_token="yourapiauthtoken")

    device = manager.get_device('device-id')
    print(device.status)
    device.reboot()

Listing all devices, limiting to 50 per page
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Packet API defaults to a limit of 10 per page*

.. code:: python

    import packet
    manager = packet.Manager(auth_token="yourapiauthtoken")
    params = {
        'per_page': 50
    }
    devices = manager.list_devices(project_id='project_id', params = params)
    print(devices)

Contributing
------------

-  Check out the latest master to make sure the feature hasn't been
   implemented or the bug hasn't been fixed yet.
-  Check out the issue tracker to make sure someone already hasn't
   requested it and/or contributed it.
-  Fork the project.
-  Start a feature/bugfix branch.
-  Commit and push until you are happy with your contribution.
-  You can test your changes with the ``test/tests.sh`` script, which is
   what travis uses to check builds.

Credits
-------

CargoCulted with much gratitude from:
https://github.com/koalalorenzo/python-digitalocean

Copyright
---------

Copyright (c) 2017 Packet Host. See `License <LICENSE.txt>`__ for
further details.

Changes
-------

See the `Changelog <CHANGELOG.md>`__ for further details.

Changelog
=========

All notable changes to this project will be documented in this file.

The format is based on `Keep a
Changelog <http://keepachangelog.com/en/1.0.0/>`__. This project adheres
to `Semantic Versioning <http://semver.org/spec/v2.0.0.html>`__.

[1.37.1] - 2018-01-08
---------------------

Fixed
~~~~~

-  Version number in setup.py

[1.37.0] - 2018-01-08
---------------------

Added
~~~~~

-  Spot Market Support
-  Ability to specify ssh keys on device creation

[1.36.0] - 2017-10-16
---------------------

Added
~~~~~

-  Better tests using PacketMockManager
-  Test on 2.7 and 3.[3-6]
-  Changelog

Changed
~~~~~~~

-  Use tox for testing

[1.35] - 2017-08-04
-------------------

Fixed
~~~~~

-  Some tests were broken

[1.35]
------

Added
~~~~~

-  ``public_ipv4_subnet_size``

[1.34] - 2017-08-04
-------------------

Added
~~~~~

-  Custom iPXE and ``always_pxe`` setting
-  Volume coloning
-  Device Tags

Fixed
~~~~~

-  Handling of error messages from api response

[1.33] - 2017-03-15
-------------------

Fixed
~~~~~

-  Default payment method


