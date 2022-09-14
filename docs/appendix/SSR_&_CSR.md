# SSR & CSR

## SSR (server side rendering)

### Diagramm

<img src="/assets/ssr_diagramm.png" alt="SSR Diagramm" width="1000"/> 
[*Moodle M133*](https://moodle.bztf.ch/course/view.php?id=2241)

## CSR (client side rendering)

### Diagramm

<img src="/assets/csr_diagramm.png" alt="SSR Diagramm" width="1000"/> 
[*Plantuml selber erstellt*]()

#### Auftrag

!!! abstract "Auftrag"
    Erweitern Sie das CSR-Projekt um die Funktion, dass die dargestellten Elemente aus einer Datei lesen kann.

??? Check "Solution"

    === "api.php"
        
        ````php
        <?php
        header("Content-Type:application/json");
        if (isset($_GET['names'])) {
            response(200, "okay");
        } else {
            responseEmpty(400, "Invalid Request");
        }

        function responseEmpty($response_code,$response_desc)
        {
            $response['response_code'] = $response_code;
        	$response['response_desc'] = $response_desc;

            $json_response = json_encode($response);
            echo $json_response;
        }

        function response($response_code,$response_desc)
        {
            $names = file("names.txt");
            for ($i=0; $i < count($names); $i++) { 
                $ganzerName = explode(" ", $names[$i]);
                $response[$ganzerName[0]] = $ganzerName[1];
            }

            $response['response_code'] = $response_code;
        	$response['response_desc'] = $response_desc;

            $json_response = json_encode($response);
            echo $json_response;
        }
        ?>
        ````

    === "names.txt"
        
        ````txt
        Peter Müller
        Pablo Escobar
        vorname nachname
        ````

## Unterschied
Der Hauptunterschied zwischen ``CSR`` und ``SSR`` besteht darin, wo die Seite gerendert wird. ``SSR`` rendert die Seite auf der Server-Seite und ``CSR`` rendert die Seite auf der Client-Seite. Die Client-Seite verwaltet das Routing dynamisch, ohne die Seite jedes Mal zu aktualisieren, wenn der Client eine andere Route anfordert.
    