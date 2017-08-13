.. _quickstart:

Quickstart Guide
================

Eager to get started? This page gives a good introduction in how to get started
with goodreads_api_client.

Installation
------------

First, make sure you have goodreads_api_client installed:

.. code-block:: bash

    $ pip install goodreads_api_client

Now let's get started with a simple example.

Basic Usage
-----------

Make sure you have a Goodreads developer key first

Import goodreads_api_client

Begin by importing the Requests module:

    >>> import goodreads_api_client as gr

Create a client:

    >>> client = gr.Client(developer_key='<YOUR_DEVELOPER_KEY>')

Call the API:

    >>> book = client.Book.show('1128434')

This will give you back an `OrderedDict` with the contents of the Goodreads API response, minus some generally useless request metadata. That means you could do a transformation like:

    >>> keys_wanted = ['id', 'title', 'isbn']
    >>> reduced_book = {k:v for k, v in book.items() if k in keys_wanted}
    >>> reduced_book
    {'id': '1128434', 'title': 'The Last Wish (The Witcher, #1)', 'isbn': '0575077832'}

:class:`Book <goodreads_api_client.resources.Book>` is just one of many resources goodreads_api_client supports. For the full list, see :ref:`api-resources`. For the methods available for a given resource, see the individual resource class.
