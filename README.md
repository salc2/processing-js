# &lt;processing-js&gt;

> Web Component wrapper to the [Processingjs Project](http://processingjs.org/), that allows you to do draws using [Polymer](http://www.polymer-project.org/).

## Documentation

[Check JSDoc !](http://salc2.github.io/processing-js/components/processing-js/)

## Demo

[Check it live!](http://salc2.github.io/processing-js/components/processing-js/demo.html)

## Install

Install the component using [Bower](http://bower.io/):

```sh
$ bower install processing-js --save
```

## Usage

1. Import Web Components' polyfill:

    ```html
    <script src="bower_components/platform/platform.js"></script>
    ```

2. Import Custom Element:

    ```html
    <link rel="import" href="bower_components/processing-js/processing-js.html">
    ```
#### With external pde file

 ```html
    <processing-js pdeUrl="sketch.pde"></processing-js
    ```

#### With pde (java) code

 ```html
  <processing-js>
<script type="pde">

float max_distance;
void setup() {
  size(200, 200);
  smooth();
  noStroke();
  max_distance = dist(0, 0, width, height);
}

void draw() 
{
  background(51);
  for(int i = 0; i <= width; i += 20) {
    for(int j = 0; j <= width; j += 20) {
      float size = dist(mouseX, mouseY, i, j);
      size = size/max_distance * 66;
      ellipse(i, j, size, size);
    }
  }
}
</script>
</processing-js>
    ```

#### With js (javascript) code

 ```html
<processing-js>
  <script type="js">
  processing.draw = function() {
      var centerX = processing.width / 2, centerY = processing.height / 2;
      var maxArmLength = Math.min(centerX, centerY);

      function drawArm(position, lengthScale, weight) {      
        processing.strokeWeight(weight);
        processing.line(centerX, centerY, 
          centerX + Math.sin(position * 2 * Math.PI) * lengthScale * maxArmLength,
          centerY - Math.cos(position * 2 * Math.PI) * lengthScale * maxArmLength);
      }
  processing.background(224);

      var now = new Date();
      var hoursPosition = (now.getHours() % 12 + now.getMinutes() / 60) / 12;
      drawArm(hoursPosition, 0.5, 5);
      var minutesPosition = (now.getMinutes() + now.getSeconds() / 60) / 60;
      drawArm(minutesPosition, 0.80, 3);
      var secondsPosition = now.getSeconds() / 60;
      drawArm(secondsPosition, 0.90, 1);
    };

  </script>
</processing-js>
    ```

