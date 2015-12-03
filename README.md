#Conference Central Application

## Endpoints Implemented & Test Instructions

The following is a list of endpoints implemented and how to test them via the Google developer console

- conference.createSession
    - provide the following:
    - WebsafeConferenceKey(Long string at end of URL for conference)
    - date (year-month-day)
    - duration in minutes
    - name(session name)
    - startTime in 24 hour format
    - Type of session
    - Speaker

- getConferenceSessions
    - Just copy in the websafeConferenceKey to retrieve all sessions for that conference
- getConferenceSessionsByDuration
    - provide websafeConferenceKey and duration you want to search for
- getConferenceSessionsByName
    - provide websafeConferenceKey and name of session you want to search for
- addSessionToWishlist
    - provide websafeConferenceKey and websafeSessionkey(Found in output of session. You can use getConferenceSessions to find keys)
- getSessionsInWishlist
    - just execute the app will find user info from login
- getFeaturedSpeaker
    - If there is a speaker that has more than 1 session the speaker will be set as featured speaker in memcache

----
Problem Statement: "How can we query sessions not after 7 PM and not workshops?"

- the reason why this problem is difficult is that app engine cannot use [datastore](https://cloud.google.com/appengine/docs/python/datastore/queries?hl=en) to query multiple properties for inequalities. I think the simplest way to get around this would be to provide two separate inequality queries and combine the results.

##Design Choices
Properties for sessions are saved in their according value types:

```
    name            = ndb.StringProperty(required=True)
    highlights      = ndb.StringProperty()
    speaker         = ndb.StringProperty()
    duration        = ndb.IntegerProperty()
    typeOfSession   = ndb.StringProperty()
    date            = ndb.DateProperty()
    startTime       = ndb.TimeProperty()

```
- Session endpoints are implemented as standalone solutions
- implemented separate session copy form


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




## Other resources used:

- [P4 Getting Started and showcase - Udacity](https://www.youtube.com/watch?v=I4zukRZZ-z4)
- [App Engine: Cloud Endpoints](https://www.youtube.com/watch?v=uy0tP6_kWJ4)
- [App Engine: Cloud Endpoints, Pt 2](https://www.youtube.com/watch?v=9wNRUd9E1jM)
- [Various student posting in Udacity forums](https://discussions.udacity.com/c/nd004-p4-conference-organization-app)



