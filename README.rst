
#################################
DivineAPI - The astrology API 
#################################
 Free and open API. Needs no authentication
|Travis| |Docs| |Maintenance yes| |SayThanks| |Paypal|
    
    
.. image:: https://divineapi.com/assets/images/logo.svg
   :height: 412px
   :width: 898px
   :alt: divineapi logo
   :align: center

What is divineAPI?
==============
Divine API allows developers to access and integrate the functionality of astrology with other applications. The API retrieves daily horoscopes for yesterday, today, and tomorrow.

Feel free to contribute on `Github <http://github.com/divineapi/horoscope-api>`_.




Why divineAPI?
==========
Divine API is for a developer who wants an API that provides horoscope info for sun signs such as Lucky Number, Lucky Color, Mood, Color, Compatibility with other sun signs, description of a sign for that day etc.

URL
===
.. code-block:: python

    POST: https://divineapi.com/api/1.0/get_daily_horoscope.php


Parameters
==========
sign : 
   Name of the sign.

   List of all signs - aries, taurus, gemini, cancer, leo, virgo, libra, scorpio, sagittarius, capricorn, aquarius and pisces.


date : 
   Current Date in Y-m-d Format (Ex: 2020-12-25)
   Date can be today,tomorrow or yesterday


Usage
=====
.. code-block:: text

    POST: https://divineapi.com/api/1.0/get_daily_horoscope.php?sign= <sign> &day= <day>


Example 
=======
The following example is for sun sign aries - 


cURL
^^^^
.. code-block:: python

    curl -X POST \
    'https://divineapi.com/api/1.0/get_daily_horoscope.php?sign=aries&day=today'


Python
^^^^^^
.. code-block:: python

    import requests

    params = (
    ('sign', 'aries'),
    ('day', 'today'),
    )

    requests.post('https://divineapi.com/api/1.0/get_daily_horoscope.php/', params=params)


Node.js
^^^^^^^
.. code-block:: javascript

    var request = require('request');

    var options = {
    url: 'https://divineapi.com/api/1.0/get_daily_horoscope.php',
    method: 'POST'
    };

    function callback(error, response, body) {
    if (!error && response.statusCode == 200) {
        console.log(body);
    }
    }

    request(options, callback);


PHP
^^^
.. code-block:: php

    <?php

        //This function can be used in any PHP framework like laravel, wordpress, drupal, cakephp etc.

        function api_call($sign, $day) {
            $api_call = curl_init('https://divineapi.com/api/1.0/get_daily_horoscope.php?sign='.$sign.'&day='.$day);
            curl_setopt_array($api_call, array(
                CURLOPT_POST => TRUE,
                CURLOPT_RETURNTRANSFER => TRUE,
                CURLOPT_HTTPHEADER => array(
                    'Content-Type: application/json'
                )
            ));
            $response = curl_exec($api_call);
            if($response === FALSE){
                die(curl_error($api_call));
            }
            $responseData = json_decode($response, TRUE);
            return $responseData;
        }

        $ObjData = api_call('aries', 'today');
        var_dump($ObjData);

    ?>
    
    
jQuery Ajax
^^^^^^
.. code-block:: javascript

    $.ajax({
   type:'POST',
   url:'https://divineapi.com/api/1.0/get_daily_horoscope.php',
   success:function(data){
   console.log(data);
   }
    });


ECMAScript (ES6)
^^^^^^
.. code-block:: javascript

    const URL = 'https://divineapi.com/api/1.0/get_daily_horoscope.php?sign=aries&day=today';
    fetch(URL, {
        method: 'POST'
    })
    .then(response => response.json())
    .then(json => {
        const date = json.current_date;
        console.log(date);
    });


Vue.JS using axios
^^^^^^^^^^^^^^^^^^
.. code-block:: html

    <ul id="divine">
        <li>Current Date: {{data.current_date}}</li>
        <li>Compatibility: {{data.compatibility}}</li>
        <li>Lucky Number: {{data.lucky_number}}</li>
        <li>Lucky Time: {{data.lucky_time}}</li>
        <li>Color: {{data.color}}</li>
        <li>Date Range: {{data.date_range}}</li> 
        <li>Mood: {{data.mood}}</li>
        <li>Description: {{data.description}}</li>
    </ul>

.. code-block:: javascript

    const URL = 'https://divineapi.com/api/1.0/get_daily_horoscope.php?sign=aries&day=today';
    new Vue({
        el: '#api',
        data() {
                return {
                data: {}
            }
        },
        created() {
            axios.post(URL).then((response) => {
                this.data = response.data
            })
        }
    })


ReactJS with ES6
^^^^^^
.. code-block:: jsx
    
    import React, { Component } from 'react';

    class Horoscope extends Component {
        constructor(props){
            super(props);
            this.state = {
              json: {}
            }
        }
        
        componentDidMount () {
            const URL = 'https://divineapi.com/api/1.0/get_daily_horoscope.php?sign=aries&day=today';
            fetch(URL, {
                method: 'POST'
            }).then(response => response.json())
            .then(json => { this.setState({json}); });
        }
        
        render() {
            return (
              <div>
                  Current Date: {this.state.json.current_date} <br />
                  Compatibility: {this.state.json.compatibility} <br />
                  Lucky Number: {this.state.json.lucky_number} <br />
                  Lucky Time: {this.state.json.lucky_time} <br />
                  Color: {this.state.json.color} <br />
                  Date Range: {this.state.json.date_range} <br />
                  Mood: {this.state.json.mood} <br />
                  Description: {this.state.json.description} <br />
              </div>
            );
        }
    }

    export default Horoscope;


Response
^^^^^^^^
.. code-block:: json

    {"current_date": "June 23, 2017", "compatibility": " Cancer", "lucky_time": " 7am",
     "lucky_number": " 64", "color": " Spring Green", "date_range": "Mar 21 - Apr 20",
     "mood": " Relaxed", "description": "It's finally time for you to think about just
      one thing: what makes you happy. Fortunately, that happens to be a person who feels
      the same way. Give yourself the evening off. Refuse to be put in charge of anything."}


Tests
=======
.. code-block:: text

    pip install nose
    nosetests tests

Projects using Divine API
========================

.. raw:: html

   <table> 
    <tr>
      <th>Repository</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/Bratanov/community-driven-radio">Community Driven Radio</a>
      </td>
      <td>A radio station driven by the community</td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/andreslopezrm/WatchOS_Swift_Horoscope">Horoscope Apple Watch App</a>
      </td>
      <td>Apple Watch Application for Horoscope</td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/sergeKashkin/daily_scope">Your Daily Horoscope</a>
      </td>
      <td>React app which shows your daily horoscope</td>
    </tr>
    
    </table>


Used Divine API in your project? Check out the `contributing guidelines <https://github.com/sameerkumar18/aztro/blob/master/contributing.md>`_ for this list and let us know. we love PRs :)


API Wrappers
============

For Python - `PyAztro <https://github.com/sameerkumar18/pyaztro>`_ (pip install pyaztro)

For NodeJS - `aztro-js <https://github.com/srijitcoder/aztro-js>`_ (npm install aztro-js)


License
=======

2021 Sameer Kumar

Licensed under the Apache License, Version 2.0 (the "License");

    http://www.apache.org/licenses/LICENSE-2.0



Contact
=======

Questions? Suggestions? Feel free to contact me at sam+aztro-ghreadme@sameerkumar.website


Buy me a coffee 🥤
=====================

If this project helped you reduce the development time, please consider donating :) 

.. image:: https://i.giphy.com/media/513lZvPf6khjIQFibF/giphy.webp
    :target: https://www.buymeacoffee.com/sameerkumar


Credits
=======

"aztro" was created by `Sameer Kumar <https://sameerkumar.website>`_ and these awesome individual `contributors <https://github.com/sameerkumar18/aztro/graphs/contributors>`_

Source of horoscope updates - http://astrology.kudosmedia.net/

Please feel free to use and adapt this small API.

    
.. |Docs| image:: https://readthedocs.org/projects/aztro/badge/?version=latest
    :target: https://aztro.readthedocs.io/en/latest/?badge=latest
    
.. |Maintenance yes| image:: https://img.shields.io/badge/Maintained%3F-yes-green.svg
   :target: https://gitHub.com/sameerkumar18/pyaztro


.. |Travis| image:: https://travis-ci.org/sameerkumar18/aztro.svg?branch=master
    :target: https://travis-ci.org/sameerkumar18/aztro

.. |SayThanks| image:: https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg
    :target: https://saythanks.io/to/sameer18051998%40gmail.com

.. |Paypal| image:: https://img.shields.io/badge/Paypal-Donate-blue.svg
    :target: https://www.buymeacoffee.com/sameerkumar

.. Indices and tables
.. ==================

.. * :ref:`genindex`
.. * :ref:`modindex`
.. * :ref:`search`
