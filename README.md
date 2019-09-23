# django-tinymce4-lite

## Installatioon de tinymce4 django

```bash
1.
pip install django-tinymce4-lite

2.
pip install django-filebrowser-no-grappelli

3.
pip install pyenchant


## setting.py


INSTALLED_APPS = (
    ...
    'tinymce',
    'filebrowser',
)

## Config 1

DEFAULT = {
    'selector': 'textarea',
    'theme': 'modern',
    'plugins': 'link image preview codesample contextmenu table code lists',
    'toolbar1': 'formatselect | bold italic underline | alignleft aligncenter alignright alignjustify '
               '| bullist numlist | outdent indent | table | link image | codesample | preview code',
    'contextmenu': 'formats | link image',
    'menubar': False,
    'inline': False,
    'statusbar': True,
    'width': 'auto',
    'height': 360,
}


## Config 2

TINYMCE_DEFAULT_CONFIG = {
    'height': 360,
    'width': 900,
    'cleanup_on_startup': True,
    'custom_undo_redo_levels': 20,
    'selector': 'textarea',
    'theme': 'modern',
    'plugins': '''
            textcolor save link image media preview codesample contextmenu
            table code lists fullscreen  insertdatetime  nonbreaking
            contextmenu directionality searchreplace wordcount visualblocks
            visualchars code fullscreen autolink lists  charmap print  hr
            anchor pagebreak
            ''',
    'toolbar1': '''
            fullscreen preview bold italic underline | fontselect,
            fontsizeselect  | forecolor backcolor | alignleft alignright |
            aligncenter alignjustify | indent outdent | bullist numlist table |
            | link image media | codesample |
            ''',
    'toolbar2': '''
            visualblocks visualchars |
            charmap hr pagebreak nonbreaking anchor |  code |
            ''',
    'contextmenu': 'formats | link image',
    'menubar': True,
    'statusbar': True,
}


### urls.py

from filebrowser.sites import site
urlpatterns = [
    ...
    path('tinymce/', include('tinymce.urls')),
    path('admin/filebrowser/', site.urls),
    ...
]



### models.py

from tinymce import HTMLField

class MyModel(models.Model):
    ...
    content = HTMLField('Content')
    
    
    
## lancer les static

python manage.py collectstatic

```

### 
