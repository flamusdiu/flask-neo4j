Flask-Neo4j
===========
.. image:: https://secure.travis-ci.org/drichner/flask-neo4j.png?branch=master
   :target: http://travis-ci.org/drichner/flask-neo4j

.. image:: https://pypip.in/license/Flask-Neo4j/badge.png
    :target: https://pypi.python.org/pypi/Flask-Neo4j/
    :alt: License

A Flask extension that provides simple interaction with the Neo4j graph
database.

These capabilities are made possible by the fine library: `py2neo <http://book.py2neo.org>`_


Installation
------------
Using pip::

    pip install flask-neo4j

Usage
-----
Typical usage looks like this::

    from flask import Flask
    from flask.ext.neo4j import Neo4j
    from py2neo import Node,Relationship

    # Configuration
    GRAPH_DATABASE='http://localhost:7474/db/data/'

    app = Flask(__name__)
    app.config.from_object(__name__)
    graph_indexes = {'Species': Node}
    flask4j = Neo4j(app, graph_indexes).gdb
    print flask4j.neo4j_version
    nosferatu = Node('species',full_name='Dracula nosferatu',species_name='nosferatu')
    genus = Node('genus',name='Dracula')
    nosferatu_memberof_genus = Relationship(nosferatu,'Member-of',genus)
    flask4j.create(nosferatu_memberof_genus)



    # which all results in a graph that looks like:
    #  (species)-[:MEMBER_OF]->(genus)



Links
-----

* `py2neo documentation <http://http://py2neo.org>`_
