# UnderstandingPaths


## Listing 2-1. A Basic Template
```html
<!doctype html>
<html>

<head>
    <title>More drawing to canvas</title>
    <link rel="stylesheet" href="styles.css">
</head>

<body>
    <h1>More drawing to canvas</h1>
    <canvas id="asteroids" width="400" height="400"></canvas>
    <script>
        var canvas = document.getElementById("asteroids");
        var context = canvas.getContext("2d");
        // Grid drawing code goes here
    </script>
</body>

</html>
```


## Listing 2-2. A Standard Stylesheet
```html
<style>
    body {
        text-align: center;
        font-family: sans-serif;
    }

    canvas {
        background-color: black;
    }
</style>
```


## Listing 2-3. Altering Line Thickness
```js
context.strokeStyle = "#00FF00";
for (var x = 0; x < canvas.width; x += 10) {
    context.beginPath();
    context.moveTo(x, 0);
    context.lineTo(x, canvas.height);
    context.lineWidth = (x % 50 == 0) ? 0.5 : 0.25;
    context.stroke();
}
for (var y = 0; y < canvas.height; y += 10) {
    context.beginPath();
    context.moveTo(0, y);
    context.lineTo(canvas.width, y);
    context.lineWidth = (y % 50 == 0) ? 0.5 : 0.25;
    context.stroke();
}
```


## Listing 2-4. draw_grid function
```js
function draw_grid(ctx, minor, major, stroke, fill) {
    minor = minor || 10;
    major = major || minor * 5;
    stroke = stroke || "#00FF00";
    f
    ill = fill || "#009900";
    ctx.save();
    ctx.strokeStyle = stroke;
    ctx.fillStyle = fill;
    let width = ctx.canvas.width, height = ctx.canvas.height
    for (var x = 0; x < width; x += minor) {
        ctx.beginPath();
        ctx.moveTo(x, 0);
        ctx.lineTo(x, height);
        ctx.lineWidth = (x % major == 0) ? 0.5 : 0.25;
        ctx.stroke();
        if (x % major == 0) { ctx.fillText(x, x, 10); }
    }
    for (var y = 0; y < height; y += minor) {
        ctx.beginPath();
        ctx.moveTo(0, y);
        ctx.lineTo(width, y);
        ctx.lineWidth = (y % major == 0) ? 0.5 : 0.25;
        ctx.stroke();
        if (y % major == 0) { ctx.fillText(y, 0, y + 10); }
    }
    ctx.restore();
}


draw_grid(context);
draw_grid(context, 15, 45, 'red', 'yellow');
draw_grid(context, 5, 30, 'white', 'red');


// ctx.save()
// - 현재 상태를 스택(stack)에 저장
// - 나중에 restore 하면 이 상태로 돌아올 수 있음

// ctx.restore()
// - 스택에서 마지막 저장 상태를 꺼내서 복원
// - strokeStyle, fillStyle, lineWidth 등이 이전 값으로 돌아감
```


## Listing 2-5. Some Lines
```js
context.beginPath();
context.strokeStyle = "#FFFFFF";
context.fillStyle = "#00FF00";
context.lineWidth = 2;
context.moveTo(50, 50);
context.lineTo(150, 250);
context.lineTo(250, 170);

context.lineTo(320, 280);

// context.fill();
context.closePath();

context.stroke();
context.fillText("(50, 50)", 30, 40);
context.fillText("(150, 250)", 130, 260);
context.fillText("(250, 170)", 255, 175);
```


## Listing 2-6. Closed Shapes
```js
context.beginPath()
context.moveTo(50, 250);
context.quadraticCurveTo(25, 300, 50, 350);
context.quadraticCurveTo(100, 375, 150, 350);
context.closePath();
context.moveTo(230, 360);
context.quadraticCurveTo(255, 340, 270, 360);
context.quadraticCurveTo(255, 340, 270, 310);
context.closePath();
context.moveTo(250, 50);
context.quadraticCurveTo(310, 60, 370, 50);
context.quadraticCurveTo(400, 75, 370, 100);
context.closePath();
context.strokeStyle = "#FFFF00";
context.fillStyle = "#000000";
context.fill();
context.stroke();
```


## Listing 2-7. Adding Curves
```js
context.beginPath()
context.moveTo(50, 250);
context.quadraticCurveTo(25, 300, 50, 350);
context.quadraticCurveTo(100, 375, 150, 350);
context.closePath();
context.moveTo(230, 360);
context.quadraticCurveTo(255, 340, 270, 360);
context.quadraticCurveTo(255, 340, 270, 310);
context.closePath();
context.moveTo(250, 50);
context.quadraticCurveTo(310, 60, 370, 50);
context.quadraticCurveTo(400, 75, 370, 100);
context.closePath();
context.strokeStyle = "#FFFF00";
context.fillStyle = "#000000";
context.fill();
context.stroke();
```


## Listing 2-8. Bezier Curves
```html
<script>
    var canvas = document.getElementById("asteroids");
    var context = canvas.getContext("2d");
    draw_grid(context)
    context.beginPath();
    context.strokeStyle = "#FFFFFF";
    context.fillStyle = "#00FF00";
    context.lineWidth = 2;
    context.moveTo(50, 50);
    context.bezierCurveTo(0, 0, 80, 250, 150, 250);
    context.bezierCurveTo(250, 250, 250, 250, 250, 170);
    context.bezierCurveTo(250, 50, 400, 350, 320, 280);

    context.closePath();
    // context.fill();
    context.stroke();
    context.fillText("(50, 50)", 30, 40);
    context.fillText("(150, 250)", 130, 260);
    context.fillText("(250, 170)", 255, 175);
    
    context.beginPath()
    context.moveTo(50, 250);
    context.quadraticCurveTo(25, 300, 50, 350);
    context.quadraticCurveTo(100, 375, 150, 350);
    context.closePath();
    context.moveTo(230, 360);
    context.quadraticCurveTo(255, 340, 270, 360);
    context.quadraticCurveTo(255, 340, 270, 310);
    context.closePath();
    context.moveTo(250, 50);
    context.quadraticCurveTo(310, 160, 370, 50);
    context.quadraticCurveTo(400, 75, 370, 100);
    context.closePath();
    context.strokeStyle = "#FFFF00";
    context.fillStyle = "#000000";
    context.fill();
    context.stroke();
</script>
```


