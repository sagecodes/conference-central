App Engine application for the Udacity training course.

## Products
- [App Engine][1]

## Language
- [Python][2]

## APIs
- [Google Cloud Endpoints][3]

## Setup Instructions
1. Update the value of `application` in `app.yaml` to the app ID you
   have registered in the App Engine admin console and would like to use to host
   your instance of this sample.
1. Update the values at the top of `settings.py` to
   reflect the respective client IDs you have registered in the
   [Developer Console][4].
1. Update the value of CLIENT_ID in `static/js/app.js` to the Web client ID
1. (Optional) Mark the configuration files as unchanged as follows:
   `$ git update-index --assume-unchanged app.yaml settings.py static/js/app.js`
1. Run the app with the devserver using `dev_appserver.py DIR`, and ensure it's running by visiting your local server's address (by default [localhost:8080][5].)
1. (Optional) Generate your client library(ies) with [the endpoints tool][6].
1. Deploy your application.

## Other resources used:

* [App Engine Architecture and Services][7]
* [Managing Your App][8]
* [Datastore Introduction][10]
* [Datastore Query, Index and Transaction][11]
* [Memcache Basics][12]
* [Task Queue Basics][13]
* [App Engine: Cloud Endpoints][14]
* [App Engine: Cloud Endpoints, Pt 2][15]
* [Various student posting in Udacity forums][16]

[1]: https://developers.google.com/appengine
[2]: http://python.org
[3]: https://developers.google.com/appengine/docs/python/endpoints/
[4]: https://console.developers.google.com/
[5]: https://localhost:8080/
[6]: https://developers.google.com/appengine/docs/python/endpoints/endpoints_tool
[7]: https://www.youtube.com/watch?v=QJp6hmASstQ
[8]: https://www.youtube.com/watch?v=hQLSoIAC-lk
[10]: https://www.youtube.com/watch?v=fQazhzcC-rg
[11]: https://www.youtube.com/watch?v=d4CiMWy0J70
[12]: https://www.youtube.com/watch?v=TGl81wr8lz8
[13]: https://www.youtube.com/watch?v=22n06z0rq4c
[14]: https://www.youtube.com/watch?v=uy0tP6_kWJ4
[15]: https://www.youtube.com/watch?v=9wNRUd9E1jM
[16]: https://discussions.udacity.com/c/nd004-p4-conference-organization-app


