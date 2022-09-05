# 2 Programmierauftrag

!!! abstract "Übungs Auftrag"
    Erstellen Sie in Ihrem Docker-Compose-Basisprojekt ein Formular mit einem Eingabefeld. Der Eingabewert
    soll wieder auf einer Webseite ausgegeben werden (Auftrag 2 aus der letzen Präsentation).

??? success "Lösung"
    
    ````php
    <form action="index.php" method="post">
       <input type="text" name="name" />
       <br>
       <input type="submit" />
    </form>

    <?php echo $_POST['name']; ?>
    ````

## Formular Bier
!!! abstract "Formular Bier Auftrag"
    Erstellen Sie Formular Bier. <br>
    Für die Firma *Brauerei Locher* müssen Sie ein Interessen-Formular erstellen, welches folgenden Inhalt abdeckt: <br>
    
    - Anrede (Radiobutton: Mann, Frau, undefiniert)
    - Name, Adresse
    - Mailadresse
    - Auswahl der Interessen an Produkten:
        - Nicht alkoholische Getränke
        - Schnäpse
        - Bier
    - Freitext für Bemerkungen

??? success "Lösung"

    ### Formular

    === "Code"

        ````html linenums="1"
        <html>
        <head>
           <title>Brauerei Locher</title>
        </head>

        <h1>Brauerei Locher</h1>
        <h2>Interessen-Formular</h2>


        <body>
           <form action="auswertung.php" method="POST">
              <table>
                 <tr>
                    <td>Anrede:</td>
                 </tr>
                 <tr>
                    <td>
                       <input type="radio" id="herr" name="anrede" value="herr" checked>
                       <label for="herr">Herr</label>
                    </td>
                 </tr>
                 <tr>
                    <td>
                       <input type="radio" id="frau" name="anrede" value="frau" checked>
                       <label for="frau">Frau</label>
                    </td>
                 </tr>
                 <tr>
                    <td>
                       <input type="radio" id="undefiniert" name="anrede" value="undefiniert" checked>
                       <label for="undefiniert">Undefiniert</label>
                    </td>
                 </tr>
                 <tr>
                    <td>Name:</td>
                    <td><input type="text" name="name"></td>
                 </tr>
                 <tr>
                    <td>Adresse:</td>
                    <td><input type="text" name="adresse"></td>
                 </tr>
                 <tr>
                    <td>E-Mail:</td>
                    <td><input type="email" name="email"></td>
                 </tr>
                 <tr>
                    <td>
                       <label for="interessen">Interesse</label>
                    </td>
                    <td>
                       <select name="interessen" id="interessen">
                          <option value="nicht alkoholische getraenke">Nicht alkoholische Getränke</option>
                          <option value="schnaepse">Schnäpse</option>
                          <option value="bier">Bier</option>
                       </select>
                    </td>
                 </tr>
                 <tr>
                    <td>Bemerkungen</td>
                    <td>
                       <textarea id="bemerkungen" name="bemerkungen" rows="4" cols="50"></textarea>
                    </td>
                 </tr>
                 <tr>
                    <td><input type="submit" name="senden" value="senden"></td>
                 </tr>
              </table>
           </form>
        </body>

        </html>
        ````

    === "Ergebnis"
        <figure markdown>
          ![Get-Formular](/assets/bier_formular.png)
          <figcaption>http://localhost:8080/index.php</figcaption>
        </figure>

    ### Auswertung


    === "Code"

        ````php linenums="1"
        <html>

        <head>
            <title>Auswertung</title>
        </head>

        <body>
            <h3>Auswertung</h3>

            <table>
                <tr>
                    <td>Anrede:</td>
                    <td>
                        <?php
                            echo $_POST["anrede"];
                        ?>
                    </td>
                </tr>
                <tr>
                    <td>Name:</td>
                    <td>
                        <?php
                            echo $_POST["name"];
                        ?>
                    </td>
                </tr>
                <tr>
                    <td>Adresse:</td>
                    <td>
                        <?php
                            echo $_POST["adresse"];
                        ?>
                    </td>
                </tr>
                <tr>
                    <td>E-Mail:</td>
                    <td>
                        <?php
                            echo $_POST["email"];
                        ?>
                    </td>
                </tr>
                <tr>
                    <td>Interesse:</td>
                    <td>
                        <?php
                            echo $_POST["interessen"];
                        ?>
                    </td>
                </tr>
                <tr>
                    <td>Bemerkungen:</td>
                    <td>
                        <?php
                            echo $_POST["bemerkungen"];
                        ?>
                    </td>
                </tr>
            </table>
        </body>

        </html>
        ````

    === "Ergebnis"
        <figure markdown>
          ![Get-Formular](/assets/bier_auswertung.png)
          <figcaption>http://localhost:8080/auswertung.php</figcaption>
        </figure>