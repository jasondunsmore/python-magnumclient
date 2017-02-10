Python bindings to the OpenStack Magnum API
===========================================

This is a client for OpenStack Magnum API. There's a Python API (the
:mod:`magnumclient` module), and a command-line script (installed as
:program:`magnum`).

Python API
==========

To use python-magnumclient in a project, create a client instance
using the keystoneauth session API::

    from keystoneauth1 import loading
    from keystoneauth1 import session
    
    from magnumclient.client import Client
    loader = loading.get_plugin_loader('password')
    
    AUTH_URL = "http://auth.example.com:5000/v2.0"
    USERNAME = "user"
    PASSWORD = "password"
    PROJECT_NAME = "project"
    
    magnum_endpoint = "http://magnum.example.com:9511/v1"
    
    auth = loader.load_from_options(auth_url=AUTH_URL,
                                    username=USERNAME,
                                    password=PASSWORD,
                                    project_name=PROJECT_NAME)
    sess = session.Session(auth=auth)
    
    magnum = Client('1', endpoint_override=magnum_endpoint, session=sess)
    magnum.clusters.list()

For more information on keystoneauth API, see `Using Sessions`_.

.. _Using Sessions: http://docs.openstack.org/developer/keystoneauth/using-sessions.html

Command-line tool
=================

