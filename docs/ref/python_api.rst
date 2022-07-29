
.. _python_api:

The Edge Python API
===================

EdgeSession
-----------

.. class:: edge.api.EdgeSession

    EdgeSession objects serve as your "entry point" into the Edge API.
    Currently there is no public way to construct these objects; you
    should always use the automatically-generated ``edge`` object present in
    new Jupyter notebooks.

    To access the Edge files API, use the :attr:`EdgeSession.files` property.

    .. property:: files
        :type: ~edge.api.Folder

        Provides access to the Edge file system for your organization.  The
        folder it returns is the "root folder", i.e. the base of the file
        tree.  You can open files and other folders as needed from here.

    .. property:: sources
        :type: ~edge.api.EdgeData

        Provides access to Data Connectors in Edge, for your organization.
        You can use this interface to access and download remote data.

    .. automethod:: search

.. class:: edge.api.SearchResult

    Represents a result from ``EdgeSession.search()``.

    .. autoproperty:: name

    .. autoproperty:: kind

    .. autoproperty:: uid


Files API
---------

.. class:: edge.api.Folder

    Represents a folder in the Edge file system.

    .. automethod:: list

    .. automethod:: list_files

    .. automethod:: list_folders

    .. automethod:: open

    .. automethod:: download

    .. automethod:: upload

    .. automethod:: make_folder

    .. automethod:: move

    .. automethod:: rename

    .. automethod:: delete


.. class:: edge.api.File

    Represents a file in the Edge file system.  You can get one of these via
    ``Folder.open(filename)``.  Please note files are read-only; to change a
    file's contents, upload (and overwrite) using ``Folder.upload``.

    This class also has all file-like methods defined on Python's
    ``io.RawIOBase`` interface, appropriate to a read-only file.

    .. autoproperty:: basename

    .. autoproperty:: size

    .. automethod:: read

    .. automethod:: write

    .. automethod:: seek

    .. automethod:: tell

    .. automethod:: download_url


Data Sources API
----------------

.. class:: edge.api.EdgeData

    This object is available at ``EdgeSession.sources``.

    .. automethod:: list_names

    .. automethod:: get

    .. automethod:: add

    .. automethod:: update

    .. automethod:: remove

SQL Data Connector
------------------

.. autoclass:: edge.api.SQLConnection
    :members:

.. autoclass:: edge.api.SQLTable
    :members:

S3 Data Connector
-----------------

.. autoclass:: edge.api.S3Connection
    :members:

.. autoclass:: edge.api.S3Folder
    :members:

.. autoclass:: edge.api.S3File
    :members:

OpenAPI Data Connector
----------------------

.. autoclass:: edge.api.OpenAPIConnection
    :members:
