# Twig Templates

## Was ist Twig
- Twig ist eine Template-Engine für die Programmiersprache PHP
- Einsatz bei Django, Drupal, und vielen weiteren Frameworks
- Ziel: Thema "View" vereinfachen/vereinheitlichen

## Twig Basis

=== "Basis"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Twig Example</title>
    </head>
    <body>
        <table border="1" style="width: 80%;">
            <thead>
                <tr>
                    <td>Product</td>
                    <td>Description</td>
                </tr>
            </thead>
            <tbody>
                {% for product in products %}
                <tr>
                    <td>{{ product.name }} </td>
                    <td>{{ product.description}} </td>
                </tr>
                {% endfor %}
            </tbody>
        </table>
    </body>
    </html>
    ```
    
=== "Aufruf"

    ```php
    // Idee: Welches Twig-Template mit welchen Models rendern
    echo $twig->render('index.html', ['products' => $products]);
    ```

## Twig-Auftrag Design

Ein Twig-Template hat immer die Dateiendung `.twig.html`.
Als erstes erstellt man das Basis Template, auf welches alle späteren Templates basieren sollen.

=== "./views/base/layout.twig.html"

    ```html
    <!doctype html>
    <html lang="en">

    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
      <link rel="stylesheet" href="css/style.css">
      <title>{{ title }}</title>

    </head>

    <body>

      <!-- Include der Navbar -->
      {{ include('base/header.twig.html') }}


      <!-- Begin page content -->
      <main role="main" class="mx-5">

        <!-- Der Content Block kann von Subtemplates überschrieben werden -->
        {% block content %}
        Das ist Default-Text auf dem Layout, falls der Content-Block nicht von Sub-Templates überschrieben wird
        {% endblock %}

      </main>


      <!-- Include Footer -->
      {{ include('base/footer.twig.html') }}

      <!-- Include von js-Imports -->
      {{ include('base/corejs.twig.html') }}
    </body>

    </html>
    ```
    
- Mit `{{ include() }}` können weitere Templates eingebunden werden.
- Mit ``{% block content %}`` & ``{% endblock %}`` wird ein bereich definiert der später durch ein Subtemplate überschrieben werden soll.

=== "./views/home/index.twig.html"

    ```html
    {% extends "base/layout.twig.html" %}

    {% block content %}

    <!-- Überschreibt den Content-Block -->
    <h1> Dieser block wurde vom Subtemplate ./views/home/index.twig.html überschrieben <\h1>
    {% endblock %}
    ```
- Mit `{% extends ""%}` wird das Basis-Layout eingebunden.
- Mit `{% block content %}` & `{% endcontent %}` wird der definierte bereich im `extends` template überschrieben.

So können beliebig weitere templates erstellt werden welche auf das base/layout basieren.

## Twig-Auftrag Logik
!!! Abstract "Auftrag"
    - Erweitern sie die Vorlage um ein eigenes Datenelemnt (Flugzeuge?) <- Controller, Model, View
    - Fügen Sie eine "Dropdown-Box" mit Twig hinzu (Internet Recherche)
    - Dokumentieren Sie Ihre Lösung

??? success "Lösung"
    
    === "Controller"

        ```php
        <?php

        class Flugzeug extends Controller
        {
            private $flugzeugArray = array();
            public function index($name = '')
            {
                $this->addFlugzeug("HB-KGF", "Sonaca S201");
                $this->addFlugzeug("HB-KGG", "Sonaca S201");


                echo $this->twig->render('flugzeug/index.twig.html', ['title' => "Flugzeug", 'flugzeuge' => $this->flugzeugArray] );                 
                //echo $this->twig->render('base/layout.twig.html', ['title' => "Titel Page"] );
            }

            private function addFlugzeug($name, $type)
            {
                $flugzeug = $this->model('Flugzeug');
                $flugzeug->type = $type;
                $flugzeug->name = $name;

                array_push($this->flugzeugArray, $flugzeug);
            }
        }
        ```

    === "Model"

        ```php
        <?php
        class Flugzeug
        {
            public string $name;
            public string $type;
        }
        ```

    === "View"

        ```html
        {% extends "base/layout.twig.html" %}

        {% block content %}
        <table border="1" style="width: 80%;">
            <thead>
                <tr>
                    <td><b>Marke</b></td>
                    <td><b>Typ</b></td>
                </tr>
            </thead>
            <tbody>
                {% for flugzeug in flugzeuge %}
                <tr>
                    <td>{{ flugzeug.name }}</td>
                    <td>{{ flugzeug.type }}</td>
                </tr>
                {% endfor %}
            </tbody>
        </table>

        <select name="package">
            {% for flugzeug in flugzeuge %}
               <option value="{{ flugzeug.name }}"{% if package.id == selectedPlan %} selected="selected"{% endif %}>{{ flugzeug.name }}</option>
            {% endfor %}
        </select>

        {% endblock %}
        ```