### css,html revision

1)tell importance of **_autocomplete_** attribute of input tag?

ans: Autocomplete allows the browser to predict and automatically complete the input as the user types, based on previous entries they have made in similar fields.

**_ default behaviour of autocomplete : on _**

Use Cases:

- **_Enabled Autocomplete:_**
  Forms where convenience is a priority, such as login forms, search boxes, or checkout forms where users frequently enter the same information.

- **_Disabled Autocomplete:_**
  Sensitive fields where security is important, such as credit card numbers, passwords, or other confidential information.

```javascript
    <input type="text" id="username" name="username" autocomplete="on">

    <input type="password" id="password" name="password" autocomplete="off">
```

---

---

2)explain all options of **_target attribute_** of anchor tag?

ans:
**_ default target attribute value : \_self _**

- \_self:
  - Opens the linked document in the same frame as it was clicked
- \_blank:
  - Opens the linked document in a new window or tab.
- \_parent
- namediframe
- \_top

When working with web pages, sometimes the content is displayed within frames. A frame is like a window within a web page that can display another web page. When a web page is divided into multiple frames, each frame can load and display different content independently of the others.

Imagine you are on a website that has a navigation menu in one frame on the left side and the main content in another frame on the right side. If you click a link in the navigation menu, you typically want the new content to appear in the main content frame which can be achieved by **_giving framename to target attribute_**

```html
//index.html
<html>
<frameset rows="30%,*">
    <frame src="topframe.html" name="topframe">
    <frameset cols="20%,*">
        <frame src="menu.html" name="menu"> // occupies 20% of container
        <frame src="content.html" name="content"> // occupies remaining 80% of container
    </frameset>
</frameset>
</html>

//menu.html

<html>
<body>
    <ul>
      // opens page1 in content frame
        <li><a href="page1.html" target="content">Page 1</a></li>

      //If you click below link, the document will replace the immediate parent frame, which is the nested frameset that contains both the menu and content frames. As a result, newpage.html will replace the entire right side of the window, but the top frame (topframe.html) will remain
        <li><a href="newpage.html" target="_parent">New Page</a></li>

      // If you click below link, the document will replace the entire frameset, including the topframe and the nested frameset. Essentially, anotherpage.html will take over the entire browser window, breaking out of all frames.
        <li><a href="anotherpage.html" target="_top">Another Page (Top)</a></li>
    </ul>
</body>
</html>
```

---

---

3)audio,video tags explain?

```html
<!-- audio-->
<audio src="./assets/sample-3s.mp3" controls></audio>

<!-- audio with type check -->
<audio controls>
  <source src="./assets/sample-3s.mp3" type="audio/mp4" />
</audio>

<!-- video-->
<div class="embed-video-container">
  <video src="./assets/2278095-hd_1920_1080_30fps.mp4" controls></video>
</div>

<!-- video with type check -->
<div class="embed-video-container">
  <video controls>
    <source src="./assets/2278095-hd_1920_1080_30fps.mp4" type="video/mp4" />
    <!-- Fallback message for browsers that do not support the video tag -->
    Your browser does not support the video tag.
  </video>
</div>
```

```css
.embed-video-container {
  width: 40vw;
  height: calc((9 / 16) * 40vw); /* to
maintain 16:9 aspect ratio of video,height should be (9/16) of current container
width */
}
.embed-video-container video {
  width: 100%;
  height: 100%;
}

/* <!-- style.scss for responsive video -- > */
```

---

---

4. semantic tags?
   semantic HTML5 elements improvea the readability of the webpage with meaningful tags.

- header
- nav
- main
- article
- section
- footer

---

---

5. html entities for >, <, & ?

<p>Use &amp;lt; to display less than: &lt;</p>
<p>Use &amp;gt; to display greater than: &gt;</p>
<p>Use &amp;amp; to display ampersand: &amp;</p>

---

---

6. explain image map and its uses

```html
<img
  src="https://via.placeholder.com/150"
  usemap="#image-map"
  alt="Placeholder Image"
/>
<map name="image-map">
  <area
    shape="rect"
    coords="34,44,270,350"
    href="./assets/2278095-hd_1920_1080_30fps.mp4"
    alt="video"
  />
  <area
    shape="circle"
    coords="500,500,100"
    href="./assets/css-streetstyle-mockup.png"
    alt="image"
  />
  <area
    shape="poly"
    coords="160,60,290,150,230,270,60,200"
    href="./assets/sample-3s.mp3"
    alt="audio"
  />
</map>
```

Common Uses of Image Maps:

- **_Geographical Maps_**: Online maps can use image maps to link specific regions or landmarks to more detailed information or related web pages.
- **_Product Showcases_**: E-commerce sites may use image maps to showcase products, where clicking on different parts of an image (like different products in a group photo) leads to their respective pages.
- **_Museum Websites_**: An image of a museum floor plan can use image maps to let users click on different rooms to get information about exhibits.
- **Event Sites**: Seating charts for concerts or events can use image maps to let users select and book specific seats.

---

---

7. embeding a pdf?

```html
<!-- type check is also there -->
<embed
  src="./assets/website.pdf"
  type="application/pdf"
  height="500"
  width="700"
/>
```

---

---

8. HTML Canvas?
   ans: it allows drawing of graphics on a web page. It provides an area within which you can use JavaScript to create and manipulate various shapes, images, text, and animations.
   - Popular online games like "Cut the Rope" or "Angry Birds" use canvas for rendering graphics.
   - Libraries like Chart.js use canvas to create interactive charts and graphs.
   - Canvas allows for the editing of images, such as applying filters, cropping, and resizing.
   - Applications like Sketchpad or online whiteboards use canvas to provide drawing functionalities

```html
<canvas
  id="myCanvas"
  width="500"
  height="400"
  style="border:1px solid #000000;"
>
  Your browser does not support the HTML canvas tag.
</canvas>
```

```javascript
var canvas = document.getElementById("myCanvas");
var context = canvas.getContext("2d");

// Drawing a rectangle
context.fillStyle = "#FF0000";
context.fillRect(50, 50, 150, 100); //fillRect(x, y, width, height) draws a filled rectangle.
```

---

---

9. CSS transitions?

- **_CSS transitions_** allow you to change property values smoothly (over a given duration), instead of instantly, thereby creating a smooth transition effect
- Transitions are only applied for specified properties that change.

```css
transition: [property] [duration] [timing-function] [delay];
transition: all 1s linear 2s;
```

- **_transition-property_** : which css property requires transition [color,height,width,opacity ....]
- **_transition-duration_** : Defines how long the transition should take to complete.
- **_transition-timing-function_**:
  - **_linear_**: constant speed
  - **_ease_**: slow start, fast, then slow end (default)
  - **_ease-in_**: slow start
  - **_ease-out_**: slow end
  - **_ease-in-out_**: slow start and end
  - **_cubic-bezier_**: custom timing function using cubic-bezier curve
- **_transition-delay_**: Specifies when the transition effect will start.

```css
.box {
  width: 100px;
  height: 100px;
  background-color: red;
  transition: width 2s ease-in-out, background-color 1s linear,
    transform 1s ease;
}

.box:hover {
  width: 200px;
  background-color: blue;
  transform: rotate(45deg);
}
```

---

---

10. css transform?

- **_functionalities_**:

  - **_Translate_**

    - **_translate(x, y)_**: Moves an element by x (horizontal) and y (vertical).
      - **_transform: translate(50px, 100px)_**
    - **_translate3d(x, y, z)_**: Moves an element in 3D space.

  - **_Rotation_**:

    - **_rotate(angle)_**: Rotates an element clockwise by given degrees.
      - **_transform: rotate(45deg)_**
    - **_rotateZ(angle)_**: Rotates an element around the z-axis (same as rotate).

  - **_Scaling_**

    - **_scale(x, y)_**: Scales an element by x horizontally and y vertically.
      - **_transform: scale(2, 3); (doubles the width and triples the height of the element)._**

  - **_Skewing_**

    - creates slanting affect.
    - give the appearance that the element is being "pushed" or "pulled" along the axes.
      - **_skew(x-angle, y-angle)_**

  - **_perspective_**
    - Defines a perspective from the z-axis to give a 3d affect
    - It defines how far the object is from the viewer
    - just like how we use a camera lens
      - **_transform: perspective(500px)_**

```css
transform: translate(50px, 100px) rotate(45deg) scale(1.5);
```

---

---

10.css animations?

- CSS animations allow you to animate the transition of an element's style properties over a specified duration

- **_@keyframes Rule_**

```css
@keyframes animation-name {
  0% {
    /* starting styles */
  }
  50% {
    /* intermediate styles */
  }
  100% {
    /* ending styles */
  }
}

@keyframes animation-name {
  from {
    /* starting styles */
  }
  to {
    /* ending styles */
  }
}
```

- **_Animation Properties_**

  - **_animation-name_**: Specifies the name of the @keyframes animation.
  - **_animation-duration_**: Defines how long the animation lasts (e.g., 2s for 2 seconds).
  - **_animation-timing-function_**: Specifies the speed curve of the animation
    - linear
    - ease
    - ease-in
    - ease-out
    - ease-in-out
    - steps(n):: The animation progresses in n discrete steps
    - cubic-bezier(x1,y1,x2,y2)
  - **_animation-delay_**: Delays the start of the animation (e.g., 1s for 1 second).
  - **_animation-iteration-count_**: Specifies the number of times the animation should repeat (e.g., infinite, 2).
  - **_animation-direction_**: Defines whether the animation should play in reverse on alternate cycles

    - normal
    - reverse
    - alternate

  - **_animation-fill-mode_**: Specifies how the animation applies styles before and after execution

    - **_none_**: No styles are applied before or after the animation.
    - **_forwards_**: The element retains the final state of the animation after it ends.
    - **_backwards_**: The element uses the initial state of the animation before it starts.
    - **_both_**: The element uses both the initial and final states, applying styles in both cases.

  - **_animation-play-state_**: Allows pausing and resuming the animation
    - running
    - paused.

```css
.box {
  animation: move 2s ease-in-out infinite alternate, rotate 3s linear infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

```css
animation: [animation-name] [animation-duration] [animation-timing-function]
  [animation-delay] [animation-iteration-count] [animation-direction]
  [animation-fill-mode] [animation-play-state];
```

---

---

11. css box-sizing options?

ans:

- **_content-box_**: Width and height include only the content. Padding and border are added outside.
- **_border-box_**: Width and height include content, padding, and border. This is easier to manage for overall element sizing.
- **_inherit_**: Inherits the box-sizing value from the parent element.

```css
* {
  box-sizing: border-box;
}
```

---

---
