Quickstart
==========

You can use Silo for file handling from the local file system,
`Amazon S3 <http://aws.amazon.com/s3/>`_ and
`Apache Libcloud <https://libcloud.apache.org/>`_.

The quickstart guide shows an example of using Silo in the local filesystem so
can get started quickly and also you can read how you can use Silo for the
local filesystem, Amazon S3 and Apache Libcloud in detail.

Getting Started
----------

To get started let's open a file in the local file system::

    >>> from silo.storages.filesystem import FileSystemStorage
    >>> storage = FileSystemStorage('my_directory')

Now you will be able to access and modify any file within this directory using
the Silo API. For example, to write to a file::

    >>> with storage.open('foo.txt', 'w') as f:
    ...     f.write(u'Hello World!')
    ...
    12L

Note that if ``foo.txt`` does not exist in the directory, opening the file in the
write mode ``'w'`` will create the file. If the open mode is not specified the
default mode is ``'rb'``.

To read the file we just wrote to now::

    >>> with storage.open('foo.txt') as f:
    ...     f.read()
    ...
    'Hello World!'

You can also get the size of the file::

    >>> storage.size('foo.txt')
    12

And also check if a file exists with a certain name in the base directory::

    >>> storage.exists('bar.txt')
    False
    >>> storage.exists('foo.txt')
    True

You can also delete the file using the delete method::

    >>> storage.delete('foo.txt')
    >>> storage.exists('foo.txt')
    False
