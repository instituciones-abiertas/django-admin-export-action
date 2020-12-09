# Django Admin Export Action

Generic export action for Django's Admin

## Quickstart

Install Django Admin Export Action::

``` python
pip install django-admin-export-action
```

Include it on INSTALLED_APPS::

```
'admin_export_action',
```

Add to urls:

``` python 
    url(r'^export_action/', include("export_action.urls", namespace="export_action")),
```

## Configuration

By default the export action will be added sitewide, which means for every app and every admin registered model.

You can disable this behaviour and decide to add manually the export action only in the models you desired:

``` python

# settings.py

ADMIN_EXPORT_ACTION = {
    'ENABLE_SITEWIDE': False
}

# model admin
from admin_export_action.admin import export_selected_objects

class MyModelAdmin(models.ModelAdmin):
    # ...
    actions = [export_selected_objects, ]

```

## Usage

Go to an admin page where the export action is enabled, select objects, run the action.

In the next page:
- select the fields you want to export
- select the output format
- select whether to get raw choices values or not
- select whether to include table header (field verbose name) or not
- click the "Export" button

## Features

* Generic or ready to use action to enable export data from Admin.
* Automatic traversal of model relations.
* Selection of fields to export.
* Can export to XSLx, CSV, JSON and HTML.

## Running Tests

Does the code actually work?

    cd testapp/app
    source <YOURVIRTUALENV>/bin/activate
    (myenv) $ pip install -r requirements.txt
    (myenv) $ python manage.py test


## Security

This project assumes staff users are trusted. There may be ways for users to manipulate this project to get more data access than they should have.

## Credits

This project is developed by Otto srl, and originally foked from [fgmacedo/django-export-action](https://github.com/fgmacedo/django-export-action)
