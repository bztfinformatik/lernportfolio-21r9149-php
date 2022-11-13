# Regex
> Regex sind Muster, um Daten zu filtern oder zu beschreiben.
> Einfache Beispiele: [https://cs.lmu.edu/~ray/notes/regex/](https://cs.lmu.edu/~ray/notes/regex/)

## Beispiele

### Validate Email
```regex
^[a-zA-Z0-9_+&*-]+(?:\.[a-zA-Z0-9_+&*-]+)*@(?:[a-zA-Z0-
9-]+\.)+[a-zA-Z]{2,7}$
```

### Einfacher Text
```regex
^[a-zA-Z0-9 .-]+$
```

### Passwort (4-8 Z / Lower-Upper mit Zahlen)
```regex
^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{4,8}$
```

## Regex in PHP
```php
<?php
$text = "Wir haben 13 Katzen";
$muster = "/1[0123456789]/";
if(preg_match($muster, $text)) {
echo "Eingabe enthält das Muster";
} else {
echo "Eingabe enthält nicht das Muster";
}
?>
```