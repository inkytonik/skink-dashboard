#### Running grafana using docker

    ./grafana

    http://localhost:80     Grafana web interface
    http://localhost:81     Graphite web interface

    Grafana username: admin
    Grafana password: admin

#### Generating data

Use Skink bench setup to conduct a run. You should get a 'results-verified'
directory containing a CSV file such as

    skink.2017-09-19_0356.results.sv-comp17.Test.xml.bz2.merged.csv

#### Converting data to Graphite triples

    csvtodata <CSV file>

#### Importing data

    csvtodata <CSV file> | import

#### Viewing data

* Create a new dashboard in Grafana via drop-down menu near top-left corner.
* Click on title of dashboard and select edit.
* In metrics tab, select metric such as `skink.*.*.*.*.result`.
* In display tab, specify display style. Points style is good for checking the data.
* Select "Back to dashboard" in top tool bar.
