# Html5ㆍCanvasElement

## Listing 1-1. A Basic HTML Template
```html
<html>
  <head>
      <title>This is an HTML canvas</title>
  </head>
  <body>
      <h1>This is an HTML canvas</h1>
      <canvas id="asteroids" width="400" height="400"></canvas>
  </body>
</html>
```


## Listing 1-2. A Simple Script
```html
  <script>
      var canvas = document.getElementById("asteroids");
      var context = canvas.getContext("2d");
      context.strokeStyle = 'dimgrey';
      context.lineWidth = 5;
      context.rect(75, 75, 250, 250);
      context.stroke();
  </script>
```


## Listing 1-3. Styling the Canvas
```html
<style media="screen">
    body {
        text-align: center;
        font-family: sans-serif;
    }

    canvas {
        background-color: black;
    }
</style>
```


## Listing 1-4. Changing the Rectangle Color, Shape, and Position
```html
<script>
    var canvas = document.getElementById("asteroids");
    var context = canvas.getContext("2d");
    context.strokeStyle = 'lightgrey';
    context.fillStyle = 'dimgrey';
    context.lineWidth = 5;
    context.rect(75, 50, canvas.width - 150, canvas.height - 100);
    context.stroke();
    context.fill();
</script>
```


## Listing 1-5. Write Some Text
```js
context.font = "34px Arial";
context.fillText("2D Drawing", 110, 100);
```


## Listing 1-6. Some Fancy Text
```html
<script>
    var canvas = document.getElementById("asteroids");
    var context = canvas.getContext("2d");
    context.strokeStyle = 'lightgrey';
    context.fillStyle = 'dimgrey';
    context.lineWidth = 5;
    context.rect(75, 50, canvas.width - 150, canvas.height - 100);
    context.stroke();
    context.fill();
    context.font = "34px Arial";
    context.strokeStyle = '#FF2222';
    context.fillStyle = '#FFAAAA';
    context.lineWidth = 0.75;
    context.textAlign = "center";
    let msg = "2D Drawing"
    context.fillText(msg, canvas.width / 2, 100);
    context.strokeText(msg, canvas.width / 2, 100);
</script>
```


##  Listing 1-7. A Stick Figure
```html
<script>
    context.strokeStyle = '#FFFFFF';
    context.lineWidth = 2;
    context.beginPath();
    context.arc(200, 140, 20, 0, Math.PI * 2);
    context.moveTo(200, 160);
    context.lineTo(200, 220);
    context.moveTo(180, 300);
    context.lineTo(185, 260);
    context.lineTo(200, 220);
    context.lineTo(215, 260);
    context.lineTo(220, 300);
    context.moveTo(240, 130);
    context.lineTo(225, 170);
    context.lineTo(200, 170);
    context.lineTo(175, 180);
    context.lineTo(170, 220);
    context.stroke();
</script>
```


## Listing 1-8. A Motivational Message
```html
<script>
    // context.strokeText(msg, canvas.width / 2, 100);

    let msg2 = "its quite easy";
    context.font = "24px Arial";
    context.fillText(msg2, canvas.width / 2, 330);
    context.strokeText(msg2, canvas.width / 2, 330);

    // context.strokeStyle = '#FFFFFF';
</script>
```