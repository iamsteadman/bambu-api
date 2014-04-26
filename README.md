# Bambu API

Quickly expose your models to a JSON or XML API, authenticated via HTTP or OAuth.

## About Bambu API

This package allows you to easily expose Django models to RESTful endpoints which can
send data in XML or JSON format.

## Installation

Install the package via Pip:

```
pip install bambu-api
```

Add it to your `INSTALLED_APPS` list:

```python
INSTALLED_APPS = (
    ...
    'bambu.api'
)
```

Add `bambu.api.urls` to your URLconf:

```python
urlpatterns = patterns('',
    ...
    url(r'^', include('bambu.api.urls')),
)
```

The prefix should be kept blank, as the package exposes two main URL stems:
`/api/`, wherein the RESTful endpoints live, and `/docs/` where auto-generated
documentation for each endpoint is found.

## Basic usage

You define API endpoints like Django admins, and register them in a similar way.

Teka the Django 'polls' app as an example. Within the polls directory, you'd
create a file called api.py. A simple API endpoint would be defined like this:

```python
from bambu import api
from myproject.polls.models import Question

class QuestionAPI(api.ModelAPI):
    pass

api.site.register(Question, QuestionAPI)
```

This registers the `QuestionAPI` endpoint for the `Question` model. The endpoint
is then accessible at `/api/polls/question.json`.

## Full documentation

Full documentation can be found at [ReadTheDocs](http://bambu-api.readthedocs.org/).

## Questions or suggestions?

Find me on Twitter (@[iamsteadman](https://twitter.com/iamsteadman))
or [visit my blog](http://steadman.io/).
