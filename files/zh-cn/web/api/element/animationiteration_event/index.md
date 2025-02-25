---
title: GlobalEventHandlers.onanimationiteration
slug: Web/API/Element/animationiteration_event
---

{{APIRef("CSS3 Animations")}}

{{event("animationiteration")}}事件的处理器 . 当 [CSS Animation](/zh-CN/docs/Web/CSS/CSS_Animations) 运动到最后一帧时触发。 An iteration ends when a single pass through the sequence of animation instructions is completed by executing the last animation step.

## 语法

```
var animIterationHandler = target.onanimationiteration;

target.onanimationiteration = {{jsxref("Function")}}
```

### Value

A {{jsxref("Function")}} to be called when an {{event("animationiteration")}} event occurs indicating that a CSS animation has reached the end of an iteration while running on the _`target`_, where the target object is an HTML element ({{domxref("HTMLElement")}}), document ({{domxref("Document")}}), or window ({{domxref("Window")}}). The function receives as input a single parameter: an {{domxref("AnimationEvent")}} object describing the event which occurred.

## 实例

Let's create an animation which automatically pauses at the end of each iteration, allowing the user to choose whether or not to start the next iteration. Much of this code is the same as in other examples of animation events, so it may look familiar.

```html hidden
<div class="main">
  <div id="box">
    <div id="text">Box</div>
  </div>
</div>

<div class="button" id="play">
  Begin Demonstration
</div>
```

### CSS content

```css hidden
:root {
  --boxwidth:50px;
}

.main {
  width: 300px;
  height:300px;
  border: 1px solid black;
}

.button {
  cursor: pointer;
  width: 300px;
  border: 1px solid black;
  font-size: 16px;
  text-align: center;
  margin-top: 0;
  padding-top: 2px;
  padding-bottom: 4px;
  color: white;
  background-color: darkgreen;
  font: 14px "Open Sans", "Arial", sans-serif;
}

#text {
  width: 46px;
  padding: 10px;
  position: relative;
  text-align: center;
  align-self: center;
  color: white;
  font: bold 1.4em "Lucida Grande", "Open Sans", sans-serif;
}


```

Leaving out some bits of the CSS that don't matter for the discussion here, let's take a look at the styles for the box that we're animating. First is the box itself. We set its size, position, color, and layout. Note that there's nothing there about animation. That's because we don't want the box to start animating right away. We'll add the {{cssxref("animation")}} style later to start animating the box.

```css
#box {
  width: var(--boxwidth);
  height: var(--boxwidth);
  left: 0;
  top: 0;
  border: 1px solid #7788FF;
  margin: 0;
  position: relative;
  background-color: #2233FF;
  display: flex;
  justify-content: center;
  animation: 2s ease-in-out 0s infinite alternate both paused slideBox;
}
```

The animation's keyframes are defined next; they describe an animation which causes the box to migrate from the top-left corner of the container to the bottom-right corner.

```css
@keyframes slideBox {
  from {
    left:0;
    top:0;
  }
  to {
    left:calc(100% - var(--boxwidth));
    top:calc(100% - var(--boxwidth))
  }
}
```

### JavaScript content

Some JavaScript code will need to be written to handle the click on the button to start the next iteration. Let's have a look.

```js
var box = document.getElementById("box");
var iterationCounter = 0;

box.onanimationiteration = function(event) {
  box.style.animationPlayState = "paused";
  document.getElementById("play").innerHTML = "Start Iteration #" + (iterationCounter+1);
};
```

This sets up two global variables: `box`, which references the `"box"` element that we're animating, and `iterationCounter`, which is initially zero, which indicates how many iterations of the animation have occurred.

The onanimationiteration event handler is then set up. It simply sets the box's {{cssxref("animation-play-state")}} to "paused", then updates the text displayed in the button to indicate that clicking the button will start playing the next iteration of theanimation.

Finally, we set up a handler for a click on the button that runs the animation:

```js
document.getElementById("play").addEventListener("click", function(event) {
  box.style.animationPlayState = "running";
  iterationCounter++;
}, false);
```

This sets the box element's {{cssxref("animation-play-state")}} to "running" and increments the iteration counter. That's all there is to it!

### Result

Assembled together, you get this:

{{ EmbedLiveSample('Example', 500, 400) }}

Each time the box reaches the opposing corner, it stops, with the button reflecting which iteration number is up next, until you click the button to run the next iteration.

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- The {{event("animationiteration")}} event this event handler is triggered by.
- {{domxref("AnimationEvent")}}
