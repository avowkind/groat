---
title: NiwaWeather
date: 2013-06-31 08:44:18
tags:
---

## Designed for embedding.
In 2013 over a 6 week period the NIWA Systems Development Team rapidly built a weather website to demonstrate how NIWA&#8217;s EcoConnect web services can be made available as visual components.  The result of this is the rather stylish <a href="http://weather.niwa.co.nz">http://weather.niwa.co.nz </a>

The page provides an 'at a glance' summary of the weather for the day. You can tell the mood of the day, and you can easily spot those windows of opportunity &#8211; a dry spell or rain showers. The design is intentionally impressionistic rather than detailed.

The application uses a PHP microservice to aggregate several EcoConnect API calls for different data products into a smaller JSON response giving the forecast for the requested location. The front end is written in Javascript with [D3](https://d3js.org/) generating the SVG graphics. The experience of writing a fairly complex javascript application here led us to investigate Javascript frameworks and eventually adopt Angular for future projects.

The interactive website is great and I&#8217;ll hope that you will bookmark your local page.  But the code is also designed to support embedding of the forecasts in other websites.

Like this for Auckland:

<iframe src="http://weather.niwa.co.nz/Auckland/kiosk/day/temperatureChart,minMaxTemperature" width="100%" height="340" scrolling="yes" class="iframe-class" frameborder="0"></iframe>

And this for Dunedin:

<iframe src="http://weather.niwa.co.nz/Dunedin/kiosk/day/temperatureChart,minMaxTemperature" width="100%" height="340" scrolling="yes" class="iframe-class" frameborder="0"></iframe>

The key is to add <em>/kiosk</em> after the location in the URL.  This gives you just the interactive graphical elements and leaves off the rest of the website content and chrome.

If you do use this in your website be sure to give credit to NIWA and provide a link to the main weather site: http://weather.niwa.co.nz. Also be sure to read the <a href="http://weather.niwa.co.nz/content/disclaimer">DISCLAIMER</a>

If you are running a commercial site then you will need to get an agreement from NIWA and they might want to charge you if traffic is high.

We can also do special locations &#8211; NIWA installed a local weather station at Mystery Creek for fieldays 2013 where the site was launched. The NiwaWeather kiosk appeared on the Giant display screens, on stand display and on the <a href="fieldays.co.nz/weather">fieldays website </a>.

# API
## The Server
The service url is http://weather.niwa.co.nz
The full path is: http://weather.niwa.co.nz/{locationList}/{displayMode}/{trackingMode}/{extras}

## Location list
The first parameter is one or more location names.  The forecast is repeated for each location given in a comma separated list.
1. single location  e..g  Auckland
2. Names with spaces use underscores  e.g.  Mystery_Creek
3. Multiple locations e.g   Auckland,Wellington   &#8211; shows a list of panels.
The stations list is available at <a href="http://weather.niwa.co.nz/stationsAvailable">/stationsAvailable</a> this returns a javascript variable containing the stations list.
<caption>Example of http://weather.niwa.co.nz/Auckland,Christchurch,Timaru/kiosk </caption>
<iframe src="http://weather.niwa.co.nz/Auckland,Christchurch,Timaru/kiosk" width="600" height="1150" scrolling="yes" class="iframe-class" frameborder="0"></iframe>

## Mode
The mode parameter controls what is on the page and the number of hours showing:

* _weather_ (default)   &#8211; shows the title bar with the previous locations, the hours, days, main page body text and footer
* _kiosk_ – shows hours and days only
* _ribbon_ – shows hours only with 144 hours showing – for testing purposes only.
<iframe src="http://weather.niwa.co.nz/Auckland,Christchurch,Timaru/ribbon" width="600" height="160" scrolling="yes" class="iframe-class" frameborder="0"></iframe>

## Track
The track parameter controls how the page is presented and updates over time.
* _hour_ – keep the infoText in the left hand column and move the day left once each hour.  Default for weather mode
* _day_ – centre the day in the window and track the infoText across the page. Default for kiosk mode

## Extra features
Controls the appearance of extra features. You can add multiple extras with a comma separated list.

* _textOnly_ – replace the hours and days SVG graphics with a pure HTML table.
* _temperatureChart_ &#8211;  display a temperature chart on the hours graphic.
* _minMaxTemperature_ – display min and max daily temperatures on the hours graphic.  (can be combined with temperatureChart).

If we detect that your browser does not support SVG we will switch to textOnly automatically.

### Other URLS
/about – Shows the about page.
/weathermap/rain – Shows the rainfall map

This is a reprint from an older blog posting as I wanted to keep the API documentation available.
