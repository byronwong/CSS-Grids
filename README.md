Project Name
============

This project is using: 2018-starter

## Global requirements
- `del-cli` - `npm install --global del-cli`


## Getting started
- `npm i`
- `npm start` - NOTE: we are using `nodemon` to reset the serve on change.


## The basics
We initiate the grid using: 
```css 
  .grid-01 {
    /* Initiate grid */
    display: grid;

    /* defines number and width of columns */
    grid-template-columns: 200px 200px 200px;

    /* defined the number and height of rows */
    /* NOTE: undefined rows are auto sized by the content inside them */
    grid-template-rows: 200px 100px;

    /* If you want to give rows an automatic height use: */
    grid-auto-rows: 50px;

    /* agjuest gutter/spacing using: */
    grid-column-gap: 20px;
    grid-row-gap: 20px;
    /* for both */
    grid-gap: 20px;

  }
```

## The Fr unit
```css
  .grid-01 {
    display: grid;

    /* fr unit treat like ratios */
    /* Notice how all other spacing is respected */
    /* Notice we can also mix in fixed size column tracks */
    grid-template-columns: 2fr 1fr 200px;

    grid-template-rows: 200px 100px;
    grid-auto-rows: 50px;
    grid-gap: 20px;
  }
```

## Repeat notation
```css 
  .grid-01 {
    display: grid;

    /* We can also repeat notation to define columns */
    /* repeat([num of times repeated], [pattern to repeat]) */
    /* Notice we can also declare additional columns as usual */
    grid-template-columns: px repeat(2, 1fr 2fr);

    grid-template-rows: 200px 100px;
    grid-auto-rows: 50px;
    grid-gap: 20px;
  }
```

## Changing flow direction and order
```css
  .grid-01 {
    display: grid;
    grid-template-columns: 200px repeat(1, 1fr) repeat(2, 30px);
    grid-template-rows: 200px 100px;
    grid-auto-rows: 50px;
    grid-column-gap: 20px;
    grid-row-gap: 20px;

    /* We can change the flow of the grid items */
    grid-auto-flow: column;
  }

  /* We can also control the order, a bit like flexbox */
  /* Think of them like priorities */
  .box:nth-child(2) {
    order: 1;
  }

  .box {
    /* second priority */
    order: 2;
    padding: 0.5rem;
    background-color: rgba(218, 78, 78, 0.55);
    border: 1px solid rgb(218, 78, 78);
  }
```

## Line based positioning 
We can position items in our grid:
- We use `grid-column-start` to say which column the item starts at.
- and we use `grid-column-end` to say where it finishes

```css
  .box:nth-child(1) {
  /* In the case of a 4 col grid */
  /* From left ot right we start at 1 to 5 */
  /* From right to left we start at -1 to -5 */
  /* we can also mix and match l-to-r with r-to-l e.g. 1 & -1 */
  grid-column-start: -1;
  grid-column-end: -5;

  /* the row we want it on */
  grid-row: 3;
}

.box:nth-child(2) {
  /* There is a sorthand */
  grid-column: 1 / -1;
}

.box:nth-child(3) {
  /* You can also you the span keyword to span n columns */
  grid-column: 1 / span 3;

  /* can be done with rows */
  grid-row: 1/3;
}
```

## Grid template areas
https://gridbyexample.com/video/grid-template-areas/

## minmax()

```css
  .grid-01 {
    display: grid;

    /* minmax allows you to set the min and max widths of column tracks */
    /* minmax([min], [max]) */
    grid-template-columns: minmax(200px, 250px) 1fr 1fr;

    /* here all new rows will have a min height of 60px, and then will auto resize to content */
    grid-auto-rows: minmax(60px, auto);
    grid-gap: 20px;
  }
```

## auto-fill and auto-fit
https://gridbyexample.com/video/series-auto-fill-auto-fit/
```css
  .grid-01 {
    display: grid;

    /* here we will fill the container with as many 150px column tracks as possible */
    /* NOTE: this may mean we lose some flexibility ^1 */
    /* auto-fill can also create empty col tracks once it runs out of cols but still has space */
    /* auto-fit on the other hand will collapse these empty tracks and allow actual cols to fill ^2 */
    grid-template-columns: repeat(auto-fill, 150px);

    /* ^1 To solve this we could do */
    /* here we would fill as many 150px col tracks, with min width of 150 and max 1fr */
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));

    /* ^2 replace auto-fill with auto-fit */
    grid-template-columns: repeat(auto-fill, minmax(50px, 1fr));

    grid-auto-rows: 50px;
    grid-gap: 20px;
  }
```

## Content sizing keywords
https://gridbyexample.com/video/content-sizing/
```css
  .box {

    /* will wrap as much as possible */
    width: min-content;

    /* will overflow content, will not wrap */
    width: max-content;

    /* a bit of both */
    /* will fit content till defined width, after that it will wrap */
    width: fit-content(50px);
  }
```

## Aligning and justifying grid items
https://gridbyexample.com/video/align-grid-items/

```css
  .grid-01 {
    display: grid;
    grid-template-columns: repeat(auto-fill, 150px);
    grid-auto-rows: 50px;
    grid-gap: 20px;

    /* two main options for all items in the container */
    justify-items: center;
    align-items: center;
  }

  .box {
    align-self: center;
    justify-self: center;
  }
```

## Aligning and Justifying the grid
This allows you to adjust the grid tracks.
```css
  .grid-01 {
    display: grid;
    grid-template-columns: repeat(auto-fill, 150px);
    grid-auto-rows: 50px;
    grid-gap: 20px;

    /* two main options adjusting the content in the grid */
    justify-content: center;
    align-content: center;
  }
```
