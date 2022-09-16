# Code Talk Exercise

In this exercise, we're going to rebuild a page from the [Dave.com website][1] using [Bootstrap][2].

Rebuilding websites you like on the internet is a good way practice web development.

## Setup

1. Install homebrew https://brew.sh/

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Install node via homebrew

```
brew install node
```

3. Download exercise project

```
git clone https://github.com/akrawchyk/code-talk-exercise
```

or download at https://github.com/akrawchyk/code-talk-exercise

4. Run a local web server to start up the project

```
cd code-talk-exercise
npm install
npx @11ty/eleventy --serve
```

5. Go to http://localhost:8080/

---

## Design

We want our design to look good on different sized screens, so here are example screenshots of what
we're trying to create.

Small:

![small](./design/small.png)

Medium:

![medium](./design/medium.png)

Large:

![large](./design/large.png)


---

## Build - Small layout

When building a page layout, I like to start with small screens and work up to larger sizes.

This is because content on small screen usually stacks in one column, so it's often the most straightforward.

We're going to use Bootstrap to build the layout of the page, starting with the small design.

### Get started

Open the `index.html` file and follow the steps below.

### Steps

1. First, insite of the `<div class="wrapper"></div>` add a container for your content. 

    [Bootstrap container docs][3]

```
<div class="container">
  <!-- STEP 2 -->
</div>
```

2. Then, inside of that container, add a grid to give us some structure. We're going to start with one column for now, but we'll add more later.

    [Bootstrap grid docs][4]

```
<div class="row align-items-center">
  <div class="col">
    <!-- STEP 3 --->
  </div>
</div>
```

3. And now add the content to our grid column.

    [Bootstrap typography docs][5]

    [Bootstrap image docs][5]

  ```
  <img class="img-fluid" src="./img/parachuting-bear.svg" alt="Parachuting Bear">

  <h1>Get up to $500 with ExtraCash instantly</h1>

  <p>
    With ExtraCash from Dave, you can get and spend up to $500 instantly.
    There's no interest, credit checks, or late fees-because it's your own money.
    Think of it as a helping hand from Future You!
  </p>

  <!-- STEP 4 --->
  <a href="#learn-more" class="btn btn-primary">Learn more</a>
  ```

4. That's pretty close, let's adjust the button link to make it match the design better.

    Find the `<a class="btn btn-primary">` tag from the previous step and wrap it with the `<div class="d-grid"></div> tag to make it spann the full width of the page.

    Also, add the "btn-lg" class to the button to make it larger.

    [Bootstrap button docs][7]

```
<div class="d-grid">
  <a href="#learn-more" class="btn btn-primary btn-lg">Learn more</a>
</div>
```

---

## Build - Decorating

When building pages, I like to focus on layout and decoration separately.

So, now that we have the small layout, let's add some styles to spruce up the page.

### Getting started

Open the `css/main.css` file and follow the steps below.

You'll also need to make changes to the `index.html` file to add the styling classes to th e content.

### Steps

5. Let's start by adding a `background-color` to the component, first make a CSS class, and then add the class to the markup.

    In `css/main.css`:

    ```
    .bg-light-blue {
      background-color: rgb(230, 245, 250);
    }
    ```

    In `index.html`, find the `<div class="wrapper"></div>` tag, and add the class we just created:

```
<div class="wrapper bg-light-blue">
```

6. Now let's add some vertical padding to show off some more of that background color.

    [Bootstrap spacing docs][8]

    On the same wrapper tag, add the `py-5` class to give it a little padding:

```
<div class="wrapper bg-light-blue py-5">
```

7. And last but not least, let's override the `background-color` of the button link to match the design:

    In `css/main.css`:

    ```
    .btn,
    .btn:hover {
      background-color: #16b04f;
      border-color: #16b04f;
    }

    .btn:active {
      background-color: #16b04f;
    }
    ```

## Build - Medium layout

Now working out way up to medium screen sizes, we'll need to make some layout adjustments to accomodate the content to the design.

### Steps

8. Start by increasing the size of your browser viewport, you should notice that the image doesn't stay centered after a certain point.

9. Let's fix this by adjusting the `img` tag. Add the `d-block` and `mx-auto` tags:

    [Bootstrap spacing utilities][8]

    [Bootstrap display utilities][9]

```
<img class="img-fluid d-block mx-auto" src="img/parachuting-bear.svg" alt="Parachuting Bear">
```

## Build - Large layout

And continuing up to the largest screen sizes, the layout is a lot different since the content is in two columns now, with the text to the left of the image.

### Steps

10. First, break up the content into two columns by wrapping the text content in a new `<div class="col"></div>` tag.

```
<div class="col">
  <img class="img-fluid d-block mx-auto" src="img/parachuting-bear.svg" alt="Parachuting Bear">
</div>

<div class="col">
  <h1>Get up to $500 with ExtraCash instantly</h1>

  <p>
  With ExtraCash from Dave, you can get and spend up to $500 instantly.
  There's no interest, credit checks, or late fees-because it's your own money.
  Think of it as a helping hand from Future You!
  </p>

  <div class="d-grid">
    <a href="#learn-more" class="btn btn-primary btn-lg">Learn more</a>
  </div>
</div>
```

11. This is close to what we want for the large screens! But, it broke our medium and small screen layouts since those were only meant for one column. To fix that, we need to change the `class="col"` class to `col-12` so they always take up the full space:

```
<div class="col-12">
</div>

<div class="col-12">
</div>
```

12. And then we can apply column classes for a two column layout for the large screen only with `col-lg-6`:

```
<div class="col-12 col-lg-6">
</div>

<div class="col-12 col-lg-6">
</div>
```

13. Now, we need to change the order of the content so we can display the image to the right of the text with `order-lg-*:

```
<div class="col-12 col-lg-6 order-lg-2">
</div>

<div class="col-12 col-lg-6 order-lg-1">
</div>
```

[1]: https://dave.com/extra-cash-advances
[2]: https://getbootstrap.com/
[3]: https://getbootstrap.com/docs/5.2/layout/containers/
[4]: https://getbootstrap.com/docs/5.2/layout/grid/
[5]: https://getbootstrap.com/docs/5.2/content/typography/
[6]: https://getbootstrap.com/docs/5.2/content/images/
[7]: https://getbootstrap.com/docs/5.2/components/buttons/
[8]: https://getbootstrap.com/docs/5.2/utilities/spacing/
[9]: https://getbootstrap.com/docs/5.2/utilities/display/