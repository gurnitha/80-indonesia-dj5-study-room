# 80-indonesia-dj5-study-room
Mengisi 80 tahun Kemerdekaan Indonesia dengan membuat aplikasi STUDY ROOM menggunakan Django 5


## 1. SETUP

#### 1. Membuat lingkungan virtual

        modified:   README.md
        new file:   venv312507/Scripts/Activate.ps1
        new file:   venv312507/Scripts/activate
        new file:   venv312507/Scripts/activate.bat
        new file:   venv312507/Scripts/deactivate.bat
        new file:   venv312507/Scripts/pip.exe
        new file:   venv312507/Scripts/pip3.12.exe
        new file:   venv312507/Scripts/pip3.exe
        new file:   venv312507/Scripts/python.exe
        new file:   venv312507/Scripts/pythonw.exe
        new file:   venv312507/pyvenv.cfg

#### 2. Menginstal Django versi 5.0.7

        modified:   .gitignore
        modified:   README.md


## 2. PROYEK

#### 1. Menginisiasi proyek Django

        config
        ├── config
        │   ├── __init__.py
        │   ├── asgi.py
        │   ├── settings.py
        │   ├── urls.py
        │   └── wsgi.py
        └── manage.py

        1 directory, 6 files

        modified:   README.md
        new file:   config/config/__init__.py
        new file:   config/config/asgi.py
        new file:   config/config/settings.py
        new file:   config/config/urls.py
        new file:   config/config/wsgi.py
        new file:   config/manage.py

#### 2. Menjalankan development server 

#### 3. Melihat tampilan default laman Django 

#### 4. Mencoba mengakses admin panel menggunakan default urls 

#### 5. Mengaktifkan aplikasi default bawaan Django 

#### 6. Membuat superuser

#### 7. Login menggunakan kredensial superuser

#### 8. Mengeksplor admin panel dengan mengupdate data superuser 


## 3. SETTING

#### 1. Memodifikasi struktur proyek

        src
        ├── README.md
        ├── config
        │   ├── __init__.py
        │   ├── asgi.py
        │   ├── settings.py
        │   ├── urls.py
        │   └── wsgi.py
        └── manage.py

        modified:   .gitignore
        modified:   README.md
        renamed:    config/config/__init__.py -> config/__init__.py
        renamed:    config/config/asgi.py -> config/asgi.py
        renamed:    config/config/settings.py -> config/settings.py
        renamed:    config/config/urls.py -> config/urls.py
        renamed:    config/config/wsgi.py -> config/wsgi.py
        renamed:    config/manage.py -> manage.py
        deleted:    venv312507/Scripts/Activate.ps1
        deleted:    venv312507/Scripts/activate
        deleted:    venv312507/Scripts/activate.bat
        deleted:    venv312507/Scripts/deactivate.bat
        deleted:    venv312507/Scripts/pip.exe
        deleted:    venv312507/Scripts/pip3.12.exe
        deleted:    venv312507/Scripts/pip3.exe
        deleted:    venv312507/Scripts/python.exe
        deleted:    venv312507/Scripts/pythonw.exe
        deleted:    venv312507/pyvenv.cfg

#### 2. Menseting bahasa dan waktu

        # LANGUAGE_CODE = "en-us"
        LANGUAGE_CODE = "id"

        # TIME_ZONE = "UTC"
        TIME_ZONE = "Asia/Jakarta"

        modified:   README.md
        modified:   config/settings.py

#### 3. Menseting path untuk static dan media file

        # Language: Bahasa Indoneia
        LANGUAGE_CODE = "id"
        # Time zone: Jakarta
        TIME_ZONE = "Asia/Jakarta"

        # Path for Static files in development
        STATIC_URL = '/static/'
        STATIC_ROOT = [BASE_DIR / 'static'] 
        # Path for Media files in development
        MEDIA_URL = '/media/'
        MEDIA_ROOT = [BASE_DIR / 'media']

        # config/urls.py

        from django.conf import settings
        from django.conf.urls.static import static
        from django.contrib import admin
        from django.urls import path

        urlpatterns = [
            path("admin/", admin.site.urls),
        ]

        if settings.DEBUG:
            urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

        modified:   README.md
        modified:   config/settings.py
        modified:   config/urls.py


## 4. DATABASE

#### 1. Membuat MySQL database

        mysql> CREATE DATABASE 80_indonesia_dj5_study_room;
        Query OK, 1 row affected (3.85 sec)

#### 2. Menghubungkan proyek dengan database

        DATABASES = {
            'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'xx',
            'USER': 'root',
            'PASSWORD': '',
            'HOST':'localhost',
            'PORT':'3306',
            }
        }

        C:\Users\ING\Desktop\80-indonesia-dj5-study-room\src(main -> origin)
        (venv312507) λ python manage.py check

        ...
        django.core.exceptions.ImproperlyConfigured: Error loading MySQLdb module.
        Did you install mysqlclient?

#### 3. Menginstal MySQL driver (mysqlclient)

        C:\Users\ING\Desktop\80-indonesia-dj5-study-room\src(main -> origin)
        (venv312507) λ pip install mysqlclient
        Collecting mysqlclient
          Using cached mysqlclient-2.2.4-cp312-cp312-win_amd64.whl.metadata (4.6 kB)
        Using cached mysqlclient-2.2.4-cp312-cp312-win_amd64.whl (203 kB)
        Installing collected packages: mysqlclient
        Successfully installed mysqlclient-2.2.4

        (venv312507) λ python manage.py check
        System check identified no issues (0 silenced)


## 5. SUPERUSER ADMIN 

#### 1. Mengaktifkan aplikasi default Django

        C:\Users\ING\Desktop\80-indonesia-dj5-study-room\src(main -> origin)
        (venv312507) λ python manage.py migrate
        ...
          File "C:\Users\ING\Desktop\80-indonesia-dj5-study-room\venv312507\Lib\site-packages\MySQLdb\connections.py", line 195, in __init__
            super().__init__(*args, **kwargs2)
        django.db.utils.OperationalError: (1049, "Unknown database 'xx'")

        # Pembetulan nama database dan jalankan migrasi lagi

        C:\Users\ING\Desktop\80-indonesia-dj5-study-room\src(main -> origin)
        (venv312507) λ python manage.py migrate
        Operations to perform:
          Apply all migrations: admin, auth, contenttypes, sessions
        Running migrations:
          Applying contenttypes.0001_initial... OK
          Applying auth.0001_initial... OK
          Applying admin.0001_initial... OK
          Applying admin.0002_logentry_remove_auto_add... OK
          Applying admin.0003_logentry_add_action_flag_choices... OK
          Applying contenttypes.0002_remove_content_type_name... OK
          Applying auth.0002_alter_permission_name_max_length... OK
          Applying auth.0003_alter_user_email_max_length... OK
          Applying auth.0004_alter_user_username_opts... OK
          Applying auth.0005_alter_user_last_login_null... OK
          Applying auth.0006_require_contenttypes_0002... OK
          Applying auth.0007_alter_validators_add_error_messages... OK
          Applying auth.0008_alter_user_username_max_length... OK
          Applying auth.0009_alter_user_last_name_max_length... OK
          Applying auth.0010_alter_group_name_max_length... OK
          Applying auth.0011_update_proxy_permissions... OK
          Applying auth.0012_alter_user_first_name_max_length... OK
          Applying sessions.0001_initial... OK