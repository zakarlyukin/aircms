.. CAPMS documentation master file, created by
   sphinx-quickstart on Tue Mar 20 17:43:06 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to CAPMS's documentation!
=================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

Data push/pull API
==================
HOST — doiot.ru

Push sensors' data to storage
-----------------------------
https://HOST/php/sensors.php?h=<hash>

POST data: L=<login>&t=<timestamp>&d="{'c':<co>,'d':<dust>}"

login — need to get, show in query, not secret information;
timestamp — current Unix timestamp;
co — CO-sensor value in ppm, -1 if absent;
dust — dust-sensor value for PM2.5pm in mcg/m3, -1 if absent;
hash = sha1(sha1(<token>) + sha1("L=<login>&t=<timestamp>&d=\"{'c':<co>,'d':<dust>}\""));
token — need to get, not show in query, SECRET information.

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
