# UDS_rus
Russian locale for UDS Enterprise www.udsenterprise.com

## Instruction
Add russian locale in language list
```
/var/server/server/settings.py
LANGUAGES = (
  ('es', ugettext('Spanish')),
  ('en', ugettext('English')),
  ('fr', ugettext('French')),
  ('de', ugettext('German')),
  ('pt', ugettext('Portuguese')),
  ('it', ugettext('Italian')),
  ('ar', ugettext('Arabian')),
  ('ru', ugettext('Russian'))
#  ('ca', ugettext('Catalan')),
)
```

Create locale folder and copy files with dictionary
```
mkdir /var/server/uds/locale/ru/
cd /var/server/uds/locale/ru/
wget https://github.com/andreyvbobrov/UDS_rus/blob/master/django.po
wget https://github.com/andreyvbobrov/UDS_rus/blob/master/djangojs.po
```

Compile files
```
root@UDS-server:/var/server/uds# pwd
/var/server/uds
 
root@UDS-server:/var/server/uds# django-admin.py makemessages -all
processing locale es
processing locale ru
processing locale zh_CN
processing locale ca
processing locale pt
processing locale en
processing locale eu
processing locale ar
processing locale de
processing locale fr
processing locale it
 
root@UDS-server:/var/server/uds# django-admin.py compilemessages
processing file djangojs.po in /var/server/uds/locale/ru/LC_MESSAGES
processing file django.po in /var/server/uds/locale/ru/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/fr/LC_MESSAGES
processing file django.po in /var/server/uds/locale/fr/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/en/LC_MESSAGES
processing file django.po in /var/server/uds/locale/en/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/pt/LC_MESSAGES
processing file django.po in /var/server/uds/locale/pt/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/zh_CN/LC_MESSAGES
processing file django.po in /var/server/uds/locale/zh_CN/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/ca/LC_MESSAGES
processing file django.po in /var/server/uds/locale/ca/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/de/LC_MESSAGES
processing file django.po in /var/server/uds/locale/de/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/it/LC_MESSAGES
processing file django.po in /var/server/uds/locale/it/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/ar/LC_MESSAGES
processing file django.po in /var/server/uds/locale/ar/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/eu/LC_MESSAGES
processing file django.po in /var/server/uds/locale/eu/LC_MESSAGES
processing file djangojs.po in /var/server/uds/locale/es/LC_MESSAGES
processing file django.po in /var/server/uds/locale/es/LC_MESSAGES
```

Check catalog
```
root@UDS-server:/var/server/uds# ls -la /var/server/uds/locale/ru/LC_MESSAGES
total 144
drwxr-xr-x 2 uds www-data   4096 May 21 12:51 .
drwxr-xr-x 3 uds www-data   4096 Apr 17 10:01 ..
-rw-r--r-- 1 uds www-data   2846 May 21 15:31 django.mo
-rw-r--r-- 1 uds www-data 105402 May 21 15:31 django.po
-rw-r--r-- 1 uds www-data    378 May 21 15:31 djangojs.mo
-rw-r--r-- 1 uds www-data  21015 Apr 17 10:01 djangojs.po
```

Restart apache
```
root@UDS-server:/var/server/uds# systemctl restart apache2
```
