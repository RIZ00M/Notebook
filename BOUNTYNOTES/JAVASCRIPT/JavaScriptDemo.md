# JavaScript Demo – Basic DOM Manipulation

A minimal example showing how JavaScript can change page content via the DOM.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>TryHackMe Editor</title>
    </head>
    <body>
        <div id="demo">Hi there!</div>
        <script type="text/javascript">
            document.getElementById("demo").innerHTML = "Hack the Planet";
        </script>
    </body>
</html>
```

**What it does:** the script finds the element with `id="demo"` and overwrites its inner HTML, changing the displayed text from *"Hi there!"* to *"Hack the Planet"*.
