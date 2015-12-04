#Conference Central Application
The conference central application provides scalable cloud endpoints using Google app engine. Users can create and register for conferences, with details such as location, description, etc. An automated email will be sent to creator of conference on creation Users can also create and view sessions. Sessions can be added, deleted and fetched from the users profile as a wish-list type function. Additional queries provided to search conference sessions by name and duration. All session interaction is currently only implemented as a backend/API functionality and can be tested in the Google Developer console. If someone is speaking at more than on session they are set as the featured speaker.

See further project details below:


## Endpoints Implemented & Test Instructions

The following is a list of endpoints implemented and how to test them via the Google developer console

- conference.createSession
    - provide the following:
    - WebsafeConferenceKey(Long string at end of URL for conference)
    - date (year-month-day)
    - duration in minutes
    - name(session name)
    - startTime in 24 hour format(8:00, 13:00, etc)
    - Type of session
    - Speaker

- getConferenceSessions
    - Just copy in the websafeConferenceKey to retrieve all sessions for that conference
- Aditional Query: getConferenceSessionsByDuration
    - provide websafeConferenceKey and duration you are looking for
- Aditional Query: getConferenceSessionsByName
    - provide websafeConferenceKey and name of session you are looking for
- addSessionToWishlist
    -  provide websafeSessionkey(Found in output of session. You can use getConferenceSessions to find keys)
- getSessionsInWishlist *(old grading rubic requirment)*
    - just execute the app will find user info from login

- deleteSessionInWishlist
    - Provide websafeSessionKey you wish to delete
- getFeaturedSpeaker
    - If there is a speaker that has more than 1 session the speaker will be set as featured speaker in memcache

----
Problem Statement: "How can we query sessions not after 7 PM and not workshops?"

- the reason why this problem is difficult is that app engine cannot use [datastore](https://cloud.google.com/appengine/docs/python/datastore/queries?hl=en) to query multiple properties for inequalities.
- I think the simplest way to get around this would be to provide two separate queries. One each for both the time query and session type. Store results in a list Then using python(or language of application) to further filter the results you are looking for. Perhaps a better solution if this type of querying is prominent through the application would be to keep a stored list of sessions in a separate python list or dict. You would then be able to easily filer/manipulate the data in anyway before passing the results back through App engine or front-end(depending on how you would like to set up the architecture).

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

Session Properties are formatted in a logical manner in NDB so that when used outside the API they can maintain proper formatting as a developer would expect for ease of interaction. A name or description type field is a stringProperty, a date is a dateProperty, a reference to time is a timeProperty, duration in minutes is a Integer property.

Sessions are implemented similar to conferences as a standalone solution. They utilize a separate session form to copy data and return form objects respectively. SessionsKeys can be saved in profile as a wish-list for sessions to attend I use data validation in the form of a Try: to catch any non urlSafe strings before being saved to profile. Validation is also performed to make sure no repeated values are saved in wish-list.

FeaturedSpeaker is simply pulled from conference sessions into memcache and stored in a string when a name is listed as speaker for multiple sessions. Note that if sessions were not created recently the speaker may not show if memcache was flushed. I think a good redesign would be to have featuredSpeaker saved as a string in the conference ndb model.


## Improvements that could be done:
- Add resource containers to API endpoints for future compatibility and avoid degradation
- Provide better logging and formatted feedback to user
- add more flexible/useful query types for getting various session types
- implement one copy to form method to be shared with conferences and sessions
- add more data validation on sessions, such as making sure the session date is matched within dates of conferences.
- make use of the native data-store type KeyProperty for storing links to other ndb.Models.
- Store featured speakers for each conference in Conference Form so that multiple conferences could be queried seperatly for their featured speaker


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
- [Hnadle URLSafe validation - Stack overflow](http://stackoverflow.com/questions/20731851/how-to-properly-handle-wrong-urlsafe-key-provided)