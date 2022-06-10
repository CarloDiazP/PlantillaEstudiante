<div align="center">
<table>
    <theader>
        <tr>
            <td><img src="https://github.com/rescobedoq/pw2/blob/main/epis.png?raw=true" alt="EPIS" style="width:50%; height:auto"/></td>
            <th>
                <span style="font-weight:bold;">UNIVERSIDAD NACIONAL DE SAN AGUSTIN</span><br />
                <span style="font-weight:bold;">FACULTAD DE INGENIERÍA DE PRODUCCIÓN Y SERVICIOS</span><br />
                <span style="font-weight:bold;">ESCUELA PROFESIONAL DE INGENIERÍA DE SISTEMAS</span>
            </th>
            <td><img src="https://github.com/rescobedoq/pw2/blob/main/abet.png?raw=true" alt="ABET" style="width:50%; height:auto"/></td>
        </tr>
    </theader>
    <tbody>
        <tr><td colspan="3"><span style="font-weight:bold;">Formato</span>: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación</td></tr>
        <tr><td><span style="font-weight:bold;">Aprobación</span>:  2022/03/01</td><td><span style="font-weight:bold;">Código</span>: GUIA-PRLD-001</td><td><span style="font-weight:bold;">Página</span>: 1</td></tr>
    </tbody>
</table>
</div>

<div align="center">
<span style="font-weight:bold;">INFORME DE LABORATORIO</span><br />
<span>(formato estudiante)</span>
</div>


<table>
<theader>
<tr><th colspan="6">INFORMACIÓN BÁSICA</th></tr>
</theader>
<tbody>
<tr><td>ASIGNATURA:</td><td colspan="5">Programación Web 2</td></tr>
<tr><td>TÍTULO DE LA PRÁCTICA:</td><td colspan="5">Django</td></tr>
<tr>
<td>NÚMERO DE PRÁCTICA:</td><td>05</td><td>AÑO LECTIVO:</td><td>2022 A</td><td>NRO. SEMESTRE:</td><td>III</td>
</tr>
<tr>
<td>FECHA DE PRESENTACIÓN:</td><td colspan="2">12-Jun-2022</td><td>HORA DE PRESENTACIÓN:</td><td colspan="2">11:55</td>
</tr>
<tr><td colspan="4">INTEGRANTE (s):
<ul>
<li>Diaz/Portilla, Carlo Rodrigo</li>
<li>-</li>
<li>Ticona/Hareth, Anthony Joaquín</li>
<li>-</li>
<li>-</li>
</ul>
</td>
<td>NOTA:</td><td>Pendiente</td>
</tr>
<tr><td colspan="6">DOCENTES:
<ul>
<li>Richart Smith Escobedo Quispe (rescobedoq@unsa.edu.pe)</li>
</ul>
</td>
</tr>
</tbody>
</table>

<!-- Reportes -->

## SOLUCIÓN Y RESULTADOS

---

I. SOLUCIÓN DE EJERCICIOS/PROBLEMAS <br>
* La organización del repositorio es la siguiente
    ```sh
	   └───Laboratorio5-Pweb2
	    │
	    ├───E
	    │
	    ├───E
	    │
	    └───E
    ```
* Paso 1: **Agregar .gitignore**
    
    Para empezar con el repositorio, se agrega un archivo <code>.gitignore</code> con las siguientes rutas, especificadas en https://github.com/django/django/blob/main/.gitignore.
    ```sh
        *.egg-info
        *.pot
        *.py[co]
        .tox/
        __pycache__
        MANIFEST
        dist/
        docs/_build/
        docs/locale/
        node_module/
        test/coverage_html/
        test/.coverage
        build/
        test/report/
    ```
    Estos serán los archivos que no necesitamos hacer <code>git add</code> y <code>git commit</code>

* Paso 2: **Activación del entorno virtual**

    Para activar el entorno virtual usaremos <code>virtualenv</code> indicando que será un entorno virtual para python3, ejecutaremos el siguiente comando.
    ```sh
        ❯ virtualenv -p python3 .
    ```
    Este comando va a crear 2 carpetas <code>Lib/</code> y <code>Scripts/</code> y un archivo <code>pyvenv.cfg</code>. Agregamos <code>Lib/</code> y <code>Scripts/</code> al archivo <code>.gitignore</code> ya que estos varian dependiendo del sistema operativo y solo conservaremos haremos commit del archivo <code>pyvenv.cfg</code>.
    Activaremos el entorno virtual (Windows) con el siguiente comando:
    ```sh
        ❯ .\Scripts\activate.ps1
    ```
    
* Paso 3: **Instalación Django**

    Una vez con el entorno virtual activado, ejecutaremos el comando que instala Django:
    ```sh
        ❯ pip install Django
    ```
    Ahora para estar seguros de que nuestro entorno virtual tiene Django, usaremos el comando <code>pip freeze</code> y ahora notamos la versión de Django:
    ```sh
        ❯ pip freeze
        asgiref==3.5.2
        Django==4.0.5
        sqlparse==0.4.2
        tzdata==2022.1
    ```

* Paso 4: **Creación del proyecto**

    Para crear el proyecto con Django, usaremos el siguiente comando:
    ```sh
        ❯ django-admin startproject mysite .
    ```
    Donde indicamos que vamos a crear un proyecto <code>startproject</code> que se va a llamar <code>mysite</code> y el <code>.</code> indicará que lo va a crear en el directorio actual.
    Notamos que se ha creado un archivo <code>manage.py</code> y un directorio que tiene el nombre de nuestro proyecto <code>mysite</code>.

* Paso 5: **Cambiar la configuración**

    A continuación editaremos el archivo <code>vim mysite/settings.py</code> y vamos a cambiar la zona horaria y el idioma.
    ```python
        ...
        LANGUAGE_CODE = 'es'

        TIME_ZONE = 'America/Lima'
        ...
    ```

* Paso 6: **Configurar la base de datos**

    Asegurándonos que nos encontramos en el ruta actual del archivo <code>manage.py</code>, vamos a ejecutar el siguiente comando para crear una base de datos en nuestro blog:
    ```sh
        ❯ python manage.py migrate
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
    ```
    Notaremos que nos aparece los <code>... OK</code>, entonces la base de datos está lista, también nos crea un nuevo archivo <code>db.sqlite3</code> el cual también agregaremos al archivo <code>.gitignore</code>.

* Paso 7: **Creación de la aplicación**

    En este paso vamos a crear una aplicación <code>blog</code>, entonces para crearla usaremos <code>startapp</code>:
    ```sh
        ❯ python manage.py startapp blog
    ```
    Este comando va a crear <code>startapp</code> una aplicación y para indicar el nombre usaremos <code>blog</code>.
    Notaremos que se ha creado un nuevo directorio con la siguiente estructura:
    ```sh
        blog
        ├── __init__.py
        ├── admin.py
        ├── apps.py
        ├── migrations
        │   └── __init__.py
        ├── models.py
        ├── tests.py
        └── views.py
    ```
    Debido a que es una aplicación nueva, tenemos que indicar a Django que vamos a utilizarla, para esto vamos a editar el archivo <code>mysite/settings.py</code>:
    ```python
        INSTALLED_APPS = [
            'django.contrib.admin',
            'django.contrib.auth',
            'django.contrib.contenttypes',
            'django.contrib.sessions',
            'django.contrib.messages',
            'django.contrib.staticfiles',
            'blog.apps.BlogConfig',
        ]
    ```
    
* Paso 8: **Creación del modelo Post**

    Ahora vamos a definir las entradas de cada Post que hagamos en nuestro blog, para eso editaremos el archivo <code>blog/models.py</code>:
    ```sh
        ❯ vim .\blog\models.py
    ```
    ```python
        from django.db import models
        from django.conf import settings
        from django.utils import timezone

        # Create your models here.

        class Post(models.Model):
            author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
            title = models.CharField(max_length=200)
            text = models.TextField()
            created_date = models.DateTimeField(
                    default=timezone.now)
            published_date = models.DateTimeField(
                    blank=True, null=True)

            def publish(self):
                self.published_date = time.now()
                self.save()

            def __str__(self):
                return self.title
    ```
    Entonces, para cada entrada de nuestro blog tendrá un autor, titulo, texto y la fecha en la que se creó.

* Paso 9: **Agregando los nuevos modelos**

    Para agregar el nuevo modelo Post que acabamos de crear tendremos que ejecutar <code>makemigrations</code> y luego <code>migrate</code> de la siguiente manera:
    ```sh
        ❯ python manage.py makemigrations blog
    ```
    Aquí se preparó un archivo de migración y está listo para realizar un <code>migrate</code>:
    ```sh
        ❯ python manage.py migrate blog
    ```
    Vamos a saber que ya está listo por el <code>... OK</code>

* Paso 10: **Registrar el modelo en admin**

    Vamos a registrar el modelo Post en el admin de Django, para poder crear nuevas entradas en nuestro blog. Para eso vamos a editar el archivo <code>blog/admin.py</code> y lo registramos:
    ```sh
        ❯ vim .\blog\admin.py
    ```
    ```python
        ...
        admin.site.register(Post)
        ...
    ```
---

II. SOLUCIÓN DEL CUESTIONARIO

* ¿Cuál es un estándar de codificación para Python? Ejemplo: Para PHP en el proyecto Pear https://pear.php.net/manual/en/standards.php
  
  

* ¿Qué diferencias existen entre EasyInstall, pip y PyPM?

  

* En un proyecto Django que se debe ignorar para usar git. Vea: https://github.com/django/django/blob/main/.gitignore. ¿Qué otros tipos de archivos se deberían agregar a este archivo?

  
  
* Utilice <code>python manage.py shell</code> para agregar objetos. ¿Qué archivos se modificaron al agregar más objetos?

  
  
---

III. CONCLUSIONES

- 
    
---
    
## RETROALIMENTACIÓN GENERAL
 <pre>
 
 </pre>
---
    
### REFERENCIAS Y BIBLIOGRAFÍA
<ul>
    <li>https://tutorial.djangogirls.org/es/django_start_project/</li>
    <li>https://github.com/django/django/blob/main/.gitignore</li>
</ul>