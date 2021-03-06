# <img src="https://cloud.githubusercontent.com/assets/7833470/10423298/ea833a68-7079-11e5-84f8-0a925ab96893.png" width="60"> React GeoQuakes

## Introduction

> ***Note:*** *This is a pair programming activity! You must work with a partner on this project! There are many pieces that could trip you up, so having two pairs of eyes and two brains on one set of code will be an important tactic to minimize errors and generate ideas.*

In this training, we attempt to put together much of the work from this week as well as the last. We'll be using axios functions to make calls to a third party API.  We will be using live data from the USGS (United States Geological Survey), specifically a data set showing significant earthquakes (M4.0 or greater) from the past week.

![](https://media.giphy.com/media/3o7bubiK9vDtxXCOgU/giphy.gif)

## Objectives

Developers will be able to:
- Use Axios to grab data from the USGS earthquakes API
- Use the Google Maps API to embed a map

## GeoQuakes

#### Starter code

Get started with the code provided in the `src` folder.

#### Deliverable

Our goal is to:
- List information about each quake.
- Display a Google Map with a pin at the epicenter of each quake.

Here's a screenshot of what the final product could look like:

![geoquakes](https://cloud.githubusercontent.com/assets/4304660/25784846/9905f872-3339-11e7-92c5-30775b6bb8f4.png)

If your partner forked the repository originally, you should fork their repository **after you finish working together** so that you'll have your own copy of your work to edit in the future. Link your own repo to your personal website.


## Instructions

#### Part 1. Rendering Data
Take a moment to familiarize yourself with the dataset by opening it in your browser: [https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_week.geojson](https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_week.geojson).

+ What is the structure of the data?
    + How many earthquakes does it list?
    + How would you grab the first earthquake?
        * How would you grab its title?
        * How would you grab its geological coordinates:
            - *latitude*?
            - *longitude*?
        * When did it happen?
            - How many hours ago is that?

Write out the AJAX call that will grab the data and `console.log` the list of earthquakes.

#### Part 2. Add the title data to the page

**Add each *title* to the page**: Loop over your JSON response object, and each `title` to the page using React. Aim to put each title inside the `<div id="info">` section of the page. For example:

```html
<div id="info">
  <p>M 4.2 - 1km ESE of Fontana, California / 123 hours ago </p>
  <p>M 3.1 - 6km SSW of Columbus, Ohio / 77 hours ago </p>
</div>
```

> **Pro-tip**: When in doubt, work in your Chrome Javascript Console! You can manipulate JSON, test your ideas, and even render elements to the page without ever touching your `app.js` file!

#### Part 3. Add Google Maps
- Your next goal is to integrate Google Maps:
    - Follow the tutorial at [Google Maps Javascript API](https://developers.google.com/maps/documentation/javascript/tutorial)
        + Note that you would normally need to sign up for an API key, but we've provided one (See `index.html` line 16)
    - Please center your map on your city:
        - Austin:  `{lat: 30.2682, lng: -97.74295}`
        - San Francisco: `{lat: 37.78, lng: -122.44}`
    - We recommend the `google-maps-react` npm package to get started
    

#### Part 4. Add pins to your map
Once you've got the map to show up, your next goal is to drop a single pin on your city. This is a sanity check.  
- Next, can you add only the first earthquake to the map?
- Can you add pins for *all* the earthquakes to the map?
- Finally, can you replace the pin with the `earthquake.png` icon?

#### Bonus:
Extend your template:  
- Calculate how long ago the quake occurred and add it to the page. E.g. "28 hours ago". Currently, the time that the API returns is in Unix time (seconds since 1/1/1970). That's a nice format for computers, but not a nice format for humans.
- Parse the title to only include the location, E.g. Instead of "M 4.2 - 1km ESE of Fontana, California", it should just say "Fontana, California."
- Create a visual indicator of the magnitude of a quake. For instance, maybe a 4.0 is indicated by a "yellow" dot, a 5.0 by an "orange" dot, and anything larger is "red".
- Create a button that allows us to switch the map from having a 'weekly' view to a 'monthly' view of all quakes. Hint: look through the USGS website to see available endpoints.
