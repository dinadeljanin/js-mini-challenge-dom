# JS Mini Challenge: DOM Manipulation

Today, we'll be building a prototype of a small application about Ian's favorite soccer team, Liverpool FC. If you don't like Liverpool, 1. sorry, and 2. feel free to change the data and personalize your app!

There's a section in this Readme file for your notes on each deliverable. As you go through the deliverables, write down some notes in this file on how you solved each problem. It'll help reinforce what you learned and give you a head start next time you see a similar problem.

A note on notation: when you see an element like `h1#header` in the Readme, that refers to the element's tag name and the CSS selector. For example, `h1#header` looks like this in the HTML:

```html
<h1 id="header">Some text here</h1>
```

And `div.players-container` looks like this (note the CSS class selector syntax):

```html
<div class="player-container">
  <!-- child elements here -->
</div>
```

## Deliverable 1

Open the `index.html` file in your browser and check the console in Chrome Dev Tools. You'll notice the console.log from line 2 of the `index.js` file is returning `null` instead of showing the `h1#header` element.

Figure out what you need to change to give Javascript access to the `h1#header` element.

**YOUR NOTES**
```
The code in the JS file is fine. It's just **where** the script tag referencing the file is place. Because it's on top, the JavaScript is loading before the HTML renders. I placed it at the bottom.
```

## Deliverable 2

Now that you have access to the `h1#header` element, use Javascript to change the element's font color to red (of course).

**YOUR NOTES**
```
header.style.color = "red"; // changes the text color to red
```

## Deliverable 3

Now that we've got a beautiful red header, we can show some players on the page. The player data is stored in a variable called `PLAYERS` in the `data.js` file - you can still access that variable in your `index.js` file (see if you can figure out why!).

First, uncomment the `console.log` under Deliverable 3 in the `index.js` file to see the data in the console. *For each* player in our application, we want to render their information on the DOM inside the `div#player-container` element.

Create a DOM element that looks like this for each player and append it to the `div.player-container`:

```html
<div class="player" data-number="(Player Number)">
  <h3>
    {player name} (<em>{player nickname}</em>)
  </h3>
  <img src="{player image}" alt="{player name}">
</div>
```

**YOUR NOTES**
```
- You want to grab the element with the id of "player-container". Whatever elements you create as you iterate through the array of players will need to be appended to it.
- On each iteration of the players array, you'll need to create a div. But separately, and I don't know if this is dry, but to set attributes, twice. To give it the class of player, and to give it a data-number of the players number.
  - I could have a function in there to take an argument of attributes and assign them whenever, but I guess since it's just two attributes, this is just fine.
- Then you want to create a multi-line string of what the contents of that container will be. Use template literal to plug in keys from each player object. Assign that to a variable.
- Take that variable and assign it to the innerHTML of the div you created.
- Then use appendChild to add each div you created to the original player-container in the html.
```

## Deliverable 4

Uh-oh! A Manchester City player, Raheem Sterling, snuck into our list. Use Javascript to find the element with the `[data-number='7']` attribute, and remove that element from the page.

Hint: You can use `querySelector` with [CSS Attribute Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) to find an element with a specific data-number.

**YOUR NOTES**
```
.removeChild() takes an argument, but will be applied to the container. Grab the element with the data-number of 7, and just plug that in as the argument.
```
