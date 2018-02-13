passport-issue-632

# How to test

This example comes with a docker environment, and require just docker and docker-composer to run.
It's not necessary, but make easier to reproduce the problem. It was made to run on Linux, but should
work fine on Mac OS.

To run it, do: `./run.sh up`. This will bring up www and mysql containers, serving
the application on port 8888. Change the port on `docker-compose.yml` if necessary.

A helper command install is present: `./run.sh install` that will install composer dependencies,
fix permissions, migrate, install passport and create keys.

To reproduce the error, you can do the following curl request:

curl -X GET \
  http://localhost:8888/auth/user \
  -H 'authorization: Bearer ZeyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjZkYTJhMjYyY2NhZGJmMWRmZjNjODJmNmNkMTkyMWI3OTBmNTIzMDYyODM0NWExNjZkMTA3ZGExMTU3ZTdhMDQ2YmNlMmQwNWU4N2MzMTUxIn0.eyJhdWQiOiIyIiwianRpIjoiNmRhMmEyNjJjY2FkYmYxZGZmM2M4MmY2Y2QxOTIxYjc5MGY1MjMwNjI4MzQ1YTE2NmQxMDdkYTExNTdlN2EwNDZiY2UyZDA1ZTg3YzMxNTEiLCJpYXQiOjE1MTc3NjYzMTEsIm5iZiI6MTUxNzc2NjMxMSwiZXhwIjoxNTQ5MzAyMzExLCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.nplW9qcPgvvTqtkvCx61ohMDOI2tTt0ZTU_7gKfnlRghE5fZA671rTWQsLPGWeJQWb0AlGSh9fS10W8rJu1JVCvm4p1Ul4uNhhPckcr4QaXJornyYN8gHVy3-PEkuxPSZ5A7WRrxUJrgRDJv1-1I3pxgfkLSHAW4aHR2--FeA3oRtw5PeaFVF5e6CH3JBZVygrFm19qK8o9wj7H7VVb7ic0J-f0ymKGU0vhzDeyHtomr8_n3YSPh0vMCgoZXEQFjtsyjq1GMyMWG5TCSF9VojBiP9iQIciIgw4u6XKO756EIDj6-ZYiWy81r4ObDhB_D5nn-Un3ae5nwb6SrwDNkJ3wYBuiUVM869FoR9RsqL0aqYoCAbKALCyfCoU-oBunLSE2tsAIgOsjK2fmuD3hoRY7CetgBvfX5jUWhBoEP2XYTwVZYJ-5BnZjT91MyhW4KDW14G7yO-aDg2k6f8xXwRiMPTAEyX_3E-O3oCelXbpEwJ5CHKu8kZ_5HiqaLXniRxFGpBn3OzTg6wxZKd-ikU_rT0p9i3pZOirSR6RPYruQWkoNMfPJQmFBc9ycUwKVBgucyi5TqJ4Kxk1Efj0RP9Af90dTie0rSL3l-OBV9gP0q3vI2ii1nibAI2fLBio5wCleqyPJu8DVzPkZuF-VeZUEEjmOFeVKnVIecw3xkfB8' \
  -H 'content-type: application/json' \
  -H 'x-requested-with: XMLHttpRequest' \