#Conference Central Application

##Tasks completed:
- Sessions
- wishlist
- Additional Queries
- Featured Speaker

Extra credit problem: "How can we query sessions not after 7 PM and not workshops?"


## Products
- [App Engine](https://cloud.google.com/appengine/docs)

## Language
- [Python](https://www.python.org/)

## APIs
- [Google Cloud Endpoints](https://cloud.google.com/appengine/docs/python/endpoints/)

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

## Grading Endpoint Test Instructions



## Other resources used:

- [P4 Getting Started and showcase - Udacity](https://www.youtube.com/watch?v=I4zukRZZ-z4)
- [App Engine: Cloud Endpoints](https://www.youtube.com/watch?v=uy0tP6_kWJ4)
- [App Engine: Cloud Endpoints, Pt 2](https://www.youtube.com/watch?v=9wNRUd9E1jM)
- [Various student posting in Udacity forums](https://discussions.udacity.com/c/nd004-p4-conference-organization-app)



