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

* login — need to get, show in query, not secret information;
* timestamp — current Unix timestamp;
* co — CO-sensor value in ppm, -1 if absent;
* dust — dust-sensor value for PM2.5pm in mcg/m3, -1 if absent;
* hash = sha1(sha1(<token>) + sha1("L=<login>&t=<timestamp>&d=\"{'c':<co>,'d':<dust>}\""));
* token — need to get, not show in query, SECRET information.

Pull sensors' data from storage
-------------------------------

* Get devices list:
  https://HOST/php/guiapi.php?devices
  JSON-answer example:
  ::
    {
      "data":[
        {"id":"1","lat":"11.111","lon":"22.222"},
        {"id":"2","lat":"55.144641","lon":"61.393387"}
      ],
      "debug":[]
    }

* Get current relative values. Count as different between last and prelast values:
  http://HOST/php/guiapi.php?T=0
  JSON-answer example:
  ::
    {
      "data":[
      {
        "id":"29195",
        "device_id":"2",
        "temperature":"-8",
        "wind_speed":"2",
        "wind_direction":"e",
        "pressure":"746",
        "humidity":"45",
        "co":0,
        "dust":-1,
        "ts":"2018-03-13 13:47:32"
      }
      ],
        "debug":[]
    }



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
