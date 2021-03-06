
===============
ProdigyHelmsman
===============

Demo REST API to do enquiries of the details of a country.

    The strange name comes from the name of an entity and  helmsman whois also a navigator hence looking for details of a country.  The strange name  also contribute to finding a unique name on yPI and at the same time not squatting useful names on the public domain.

==========
Developing
==========

To do any development, you must install Reahl in a virtual environment.  For detailed instructions please refer to the Reahl website (https://www.reahl.org/docs/5.1/tutorial/gettingstarted-install.d.html) The basic steps are as follow:

1. Prerequisites (for these instructions)

    - Linux 20.4 (debian)
    - Python 3.8
    - Git 2.25.1

2. Install a virtual environment

    - You can setup the virtual environment in a different directory than from your development directory.
    - Make sure you have sufficient rights to the directory directories.
    - Install the virtual environment
    - Activate the virtual environment
    - The prompt should change to indicate that your virtual environment is active.

.. code-block:: bash

    $ sudo chmod 777 /usr/local
    $ python3 -m venv /usr/local/prodigyhelmsman_env
    $ source /usr/local/prodigyhelmsman_env/bin/activate

3. Install Reahl in the virtual environment

    - Change to or create the directory where you want to install your project.  Your home directory might be the safest for now.
    - The instructions below will prepare Reahl to connect to a Sqlite database.
    - Add/replace the ``mysql`` parameter in the instruction below depending on your requirement.

.. code-block:: bash

    $ cd ~
    $ pip3 install reahl[declarative,sqlite,dev,doc]

4. Clone the project from GitHub

.. code-block:: bash

    $ git clone https://github.com/hendrikdutoit/ProdigyHelmsman

5. Configure ProdigyHelmsman

.. code-block:: bash

    $ cd ./ProdigyHelmsman/
    $ reahl setup develop -N
    $ reahl createdbuser etc
    $ reahl createdb etc
    $ reahl createdbtables etc

6. Load test data

    - The database is empty.
    - The ``demosetup`` procedure will load test data into the database

.. code-block:: bash

    $ reahl demosetup

7. Start the simulator

    - The simulator server is now operational on http://localhost:8000

.. code-block:: bash

    $ reahl serve etc

8. Run a sample

    - Open-up another session
    - Run the enquire_country script.
    - Start the ``enquire_country`` with command line option "1".  This will connect to the local server.  Option "2" will connect to www.prodigyhelmsman.co.za

.. code-block:: bash

    $ cd ~
    $ cd ./ProdigyHelmsman/
    $ python3 prodigyhelmsman/enquire_country.py 1
    API Endpoint: list_countries
    Method: _list_countries_method
    {'cca3': 'AUS', 'cca2': 'AU', 'name_common': 'Australia', 'curr_iso': 'AUD'}
    {'cca3': 'SWZ', 'cca2': 'SZ', 'name_common': 'Eswatini', 'curr_iso': 'ZAR'}
    {'cca3': 'SWZ', 'cca2': 'SZ', 'name_common': 'Eswatini', 'curr_iso': 'SZL'}
    {'cca3': 'DER', 'cca2': 'DE', 'name_common': 'Federal Republic of Germany', 'curr_iso': 'EUR'}
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'ZAR'}
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'LSL'}
    {'cca3': 'ZAF', 'cca2': 'ZA', 'name_common': 'South Africa', 'curr_iso': 'ZAR'}
    {'cca3': 'GBR', 'cca2': 'GB', 'name_common': 'United Kingdom', 'curr_iso': 'GBP'}
    {'cca3': 'USA', 'cca2': 'US', 'name_common': 'United States of America', 'curr_iso': 'USD'}
    200

    API Endpoint: list_countries filter currency=LSL (Lesotho loti)
    Method: _list_countries_method?curr_iso=LSL
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'LSL'}
    200

    API Endpoint: find_country filter cca3 = ZAF
    Method: _find_country_method?cca=ZAF
    {'cca3': 'ZAF', 'cca2': 'ZA', 'name_common': 'South Africa'}
    200

    API Endpoint: find_country filter cca3 = ZA
    Method: _find_country_method?cca=ZA
    {'cca3': 'ZAF', 'cca2': 'ZA', 'name_common': 'South Africa'}
    200

    API Endpoint: delete_country where cca = ZA
    Method: _delete_country_method
    {'cca3': 'AUS', 'cca2': 'AU', 'name_common': 'Australia', 'curr_iso': 'AUD'}
    {'cca3': 'SWZ', 'cca2': 'SZ', 'name_common': 'Eswatini', 'curr_iso': 'ZAR'}
    {'cca3': 'SWZ', 'cca2': 'SZ', 'name_common': 'Eswatini', 'curr_iso': 'SZL'}
    {'cca3': 'DER', 'cca2': 'DE', 'name_common': 'Federal Republic of Germany', 'curr_iso': 'EUR'}
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'ZAR'}
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'LSL'}
    {'cca3': 'ZAF', 'cca2': 'ZA', 'name_common': 'South Africa', 'curr_iso': 'ZAR'}
    {'cca3': 'GBR', 'cca2': 'GB', 'name_common': 'United Kingdom', 'curr_iso': 'GBP'}
    {'cca3': 'USA', 'cca2': 'US', 'name_common': 'United States of America', 'curr_iso': 'USD'}
    200
    {'cca3': 'AUS', 'cca2': 'AU', 'name_common': 'Australia', 'curr_iso': 'AUD'}
    {'cca3': 'SWZ', 'cca2': 'SZ', 'name_common': 'Eswatini', 'curr_iso': 'ZAR'}
    {'cca3': 'SWZ', 'cca2': 'SZ', 'name_common': 'Eswatini', 'curr_iso': 'SZL'}
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'ZAR'}
    {'cca3': 'LSO', 'cca2': 'LS', 'name_common': 'Lesotho', 'curr_iso': 'LSL'}
    {'cca3': 'ZAF', 'cca2': 'ZA', 'name_common': 'South Africa', 'curr_iso': 'ZAR'}
    {'cca3': 'GBR', 'cca2': 'GB', 'name_common': 'United Kingdom', 'curr_iso': 'GBP'}
    {'cca3': 'USA', 'cca2': 'US', 'name_common': 'United States of America', 'curr_iso': 'USD'}

9. Notes

    - The ``reahl unit`` wack the database i.e. the database will be empty after a unit test
    - Use the reahl ``demosetup`` to refresh the database
    - If you are using ``sqlite``, you must stop the server before loading data into the database.  Sqlite can only handle one connection at a time.
    - Stop the server whilst executing the unit tests.  The unit test start its own server, but ``sqlite`` has a problem with multiple connections.



=======
Testing
=======

1. This project uses ``reahl unit`` to run execute pytest.

2. To run the tests
    - Make sure the server is stopped <ctrl-c>

.. code-block:: bash

    $ cd ~
    $ cd ./ProdigyHelmsman/
    $ reahl unit
    REAHLWORKSPACE environment variable not set, defaulting to /home/rtinstall
    ================================================= test session starts ==================================================
    platform linux -- Python 3.8.10, pytest-6.2.5, py-1.11.0, pluggy-1.0.0
    rootdir: /home/rtinstall/ProdigyHelmsman
    collected 4 items

    tests/test_prodigyhelmsman.py ...<html data-reahl-rendered-state="" class="no-js">
    <head>
    <script>
              function switchJSStyle(d, fromStyle, toStyle) {
                  var r=d.querySelectorAll("html")[0];
                  r.className=r.className.replace(new RegExp("\\b" + fromStyle + "\\b", "g"),toStyle)
            };
              (function(d) { switchJSStyle(d, "no-js", "js"); })(document);
            </script><title>API</title>
    <link rel="stylesheet" href="/static/reahl.css" type="text/css">
    <link rel="stylesheet" href="/static/reahl.runningonbadge.css" type="text/css">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <link rel="stylesheet" href="/static/bootstrap-4.5.3/css/bootstrap.css" type="text/css">
    <link rel="stylesheet" href="/static/bootstrap-4.5.3/css/reahl-patch.css" type="text/css">
    <link rel="stylesheet" href="/static/reahl.files.css" type="text/css">
    <link rel="stylesheet" href="/static/reahl.carousel.css" type="text/css">
    <link rel="stylesheet" href="/static/reahl.datatable.css" type="text/css">
    </head>
    <body>
    <div id="_reahl_out_of_bound_container"></div>
    <script type="text/javascript">
    window.QUnit = true;
    </script>

    <script type="text/javascript" src="/static/jquery-3.5.1/jquery-3.5.1.js"></script>
    <script type="text/javascript" src="/static/jquery/jquery.validate-1.19.3.modified.js"></script>
    <script type="text/javascript" src="/static/jquery/jquery.ba-bbq-1.3pre.js"></script>
    <script type="text/javascript" src="/static/jquery/jquery.blockUI-2.70.0.js"></script>
    <script type="text/javascript" src="/static/jquery/jquery.form-4.3.0.js"></script>
    <script id="reahl-jqueryready" type="text/javascript">
    jQuery(document).ready(function($){
    $('body').addClass('enhanced');

    });
    </script>

    <script type="text/javascript" src="/static/js-cookie-2.2.1/js.cookie.js"></script>
    <script type="text/javascript" src="/static/jquery-ui-1.12.1.custom/jquery-ui.js"></script>
    <script type="text/javascript" src="/static/underscore-umd-min.1.13.1.js"></script><script>var underscore = _;</script>
    <!--[if lt IE 9]>
    <script type="text/javascript" src="/static/html5shiv-printshiv-3.7.3.js"></script><![endif]-->
    <!--[if lte IE 9]>
    <script type="text/javascript" src="/static/IE9.js"></script><![endif]-->
    <script type="text/javascript" src="/static/reahl.hashchange.js"></script>
    <script type="text/javascript" src="/static/reahl.ajaxlink.js"></script>
    <script type="text/javascript" src="/static/reahl.primitiveinput.js"></script>
    <script type="text/javascript" src="/static/reahl.textinput.js"></script>
    <script type="text/javascript" src="/static/reahl.validate.js"></script>
    <script type="text/javascript" src="/static/reahl.form.js"></script>
    <script type="text/javascript" src="/static/holder-2.9.9.js"></script>
    <script type="text/javascript" src="/static/popper-1.16.1/popper.js"></script>
    <script type="text/javascript" src="/static/bootstrap-4.5.3/js/bootstrap.js"></script>
    <script type="text/javascript" src="/static/reahl.bootstrapform.js"></script>
    <script type="text/javascript" src="/static/reahl.pagination.js"></script>
    <script type="text/javascript" src="/static/reahl.files.js"></script>
    <script type="text/javascript" src="/static/reahl.bootstrappopupa.js"></script>
    <script type="text/javascript" src="/static/reahl.bootstrapcueinput.js"></script>
    <script type="text/javascript" src="/static/reahl.bootstrapfileuploadli.js"></script>
    <script type="text/javascript" src="/static/reahl.bootstrapfileuploadpanel.js"></script>
    </body>
    <p>This is the ProdigyHelmsman API. Methods:</p>
    <ul></ul>
    <li><p>delete_country [['post']]: /api/_delete_country_method</p></li>
    <li><p>find_country [['get']]: /api/_find_country_method</p></li>
    <li><p>list_countries [['get']]: /api/_list_countries_method</p></li>
    <li><p>log_in [['post']]: /api/_log_in_method</p></li>
    </html>

    logging in with admin@realhelmsman.co.za[topsecret]
    .

    ================================================== 4 passed in 1.66s ===================================================

=======================================
Connecting to www.prodigyhelmsman.co.za
=======================================

The API server is currently active on www.prodigyhelmsman.co.za.  To connect to www.prodigyhelmsman.co.za:

.. code-block:: bash

    $ cd ~
    $ cd ./ProdigyHelmsman/
    $ python3 prodigyhelmsman/enquire_country.py 2


.. toctree::
    :maxdepth: 2
    :caption: Contents
    :numbered:

    api
    examples
    faq
