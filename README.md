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

#### Importing data to your local instance of Grafana

    csvtodata <CSV file> | import localhost

#### Archived data

As we generate useful data sets we will commit them to this repository in the `data` directory.
Thus, we can recreate the dashboards from scratch if we need to, or you can create a local instance with all of the same data.

#### Viewing data

* Create a new dashboard in Grafana via drop-down menu near top-left corner.
* Click on title of dashboard and select edit.
* In metrics tab, select metric such as `skink.*.*.*.*.result`.
* In display tab, specify display style. Points style is good for checking the data.
* Select "Back to dashboard" in top tool bar.

#### Matt's server

Matt is running a Grafana instance at MQ internal address 10.46.35.0.
We are importing data to that instance when we have it.

    csvtodata <CSV file> | import 10.46.35.0

#### Dashboard definitions

Grafana can export dashboard definitions as JSON.
We will be putting useful ones in the dashboards folder of this repository so you can import them into your Grafana instances if you want.
For example, `dashboards/ReachSafety-Loops.json` contains a dashboard that can be used to visualise the data for the ReachSafety-Loops category of the SV-COMP.
