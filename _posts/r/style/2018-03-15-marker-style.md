---
title: Marker Styling in R | Examples | Plotly
name: Marker Styling
permalink: r/marker-style/
description: How to style markers in R.
layout: base
thumbnail: thumbnail/marker-style.gif
language: r
page_type: example_index
has_thumbnail: false
display_as: style_opt
order: 8
output:
  html_document:
    keep_md: true
---


### New to Plotly?

Plotly's R library is free and open source!<br>
[Get started](https://plot.ly/r/getting-started/) by downloading the client and [reading the primer](https://plot.ly/r/getting-started/).<br>
You can set up Plotly to work in [online](https://plot.ly/r/getting-started/#hosting-graphs-in-your-online-plotly-account) or [offline](https://plot.ly/r/offline/) mode.<br>
We also have a quick-reference [cheatsheet](https://images.plot.ly/plotly-documentation/images/r_cheat_sheet.pdf) (new!) to help you get started!

### Version Check

Version 4 of Plotly's R package is now [available](https://plot.ly/r/getting-started/#installation)!<br>
Check out [this post](http://moderndata.plot.ly/upgrading-to-plotly-4-0-and-above/) for more information on breaking changes and new features available in this version.

```r
library(plotly)
packageVersion('plotly')
```

```
## [1] '4.7.1.9000'
```

#### Add Marker Border
In order to make markers distinct, you can add a border to the markers. This can be achieved by adding the line dict to the marker dict. For example, `marker:{..., line: {...}}`.


```r
library(plotly)

x <- runif(500, min=3, max=6)
y <- runif(500, min=3, max=6)

p <- plot_ly(type = 'scatter', mode = 'markers') %>%
  add_trace(
    x = x,
    y = y,
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 20,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 2
      )
    ),
    showlegend = F
  ) %>%
  add_trace(
    x = c(2),
    y = c(4.5),
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 120,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 12
      )
    ),
    showlegend = F
  )

# Create a shareable link to your chart
# Set up API credentials: https://plot.ly/r/getting-started
chart_link = api_create(p, filename="style-add-border")
chart_link
```

<iframe src="https://plot.ly/~RPlotBot/5282.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>

#### Fully Opaque
Fully opaque, the default setting, is useful for non-overlapping markers. When many points overlap it can be hard to observe density.  


```r
library(plotly)

x <- runif(500, min=3, max=6)
y <- runif(500, min=3, max=6)

p <- plot_ly(type = 'scatter', mode = 'markers') %>%
  add_trace(
    x = x,
    y = y,
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 20,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 2
      )
    ),
    showlegend = F
  ) %>%
  add_trace(
    x = c(2,2),
    y = c(4.25,4.75),
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 120,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 12
      )
    ),
    showlegend = F
  )

# Create a shareable link to your chart
# Set up API credentials: https://plot.ly/r/getting-started
chart_link = api_create(p, filename="style-full-opacity")
chart_link
```

<iframe src="https://plot.ly/~RPlotBot/5284.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>

#### Opacity
Setting opacity outside the marker will set the opacity of the trace. Thus, it will allow greater visbility of additional traces but like fully opaque it is hard to distinguish density.


```r
library(plotly)

x <- runif(500, min=3, max=6)
y <- runif(500, min=3, max=4.5)
x2 <- runif(500, min=3, max=6)
y2 <- runif(500, min=4.5, max=6)

p <- plot_ly(type = 'scatter', mode = 'markers') %>%
  add_trace(
    x = x,
    y = y,
    opacity = 0.5,
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 20,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 2
      )
    ),
    name = 'Opacity 0.5'
  ) %>%
  add_trace(
    x = x2,
    y = y2,
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 20,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 2
      )
    ),
    name = 'Opacity 1.0'
  ) %>%
  add_trace(
    x = c(2,2),
    y = c(4.25,4.75),
    opacity = 0.5,
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 120,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 12
      )
    ),
    showlegend = F
  )

# Create a shareable link to your chart
# Set up API credentials: https://plot.ly/r/getting-started
chart_link = api_create(p, filename="style-opacity")
chart_link
```

<iframe src="https://plot.ly/~RPlotBot/5286.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>

#### Marker Opacity
To maximise visibility of density, it is recommended to set the opacity inside the marker `marker:{opacity:0.5}`. If mulitple traces exist with high density, consider using marker opacity in conjunction with trace opacity.


```r
library(plotly)

x <- runif(500, min=3, max=6)
y <- runif(500, min=3, max=6)

p <- plot_ly(type = 'scatter', mode = 'markers') %>%
  add_trace(
    x = x,
    y = y,
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 20,
      opacity = 0.5,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 2
      )
    ),
    showlegend = F
  ) %>%
  add_trace(
    x = c(2,2),
    y = c(4.25,4.75),
    marker = list(
      color = 'rgb(17, 157, 255)',
      size = 120,
      opacity = 0.5,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 12
      )
    ),
    showlegend = F
  )

# Create a shareable link to your chart
# Set up API credentials: https://plot.ly/r/getting-started
chart_link = api_create(p, filename="style-marker-opacity")
chart_link
```

<iframe src="https://plot.ly/~RPlotBot/5288.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>

#### Color Opacity
To maximise visibility of each point, set the color opacity by using alpha: `marker:{color: 'rgba(0,0,0,0.5)'}`. Here, the marker line will remain opaque.


```r
library(plotly)

x <- runif(500, min=3, max=6)
y <- runif(500, min=3, max=6)

p <- plot_ly(type = 'scatter', mode = 'markers') %>%
  add_trace(
    x = x,
    y = y,
    marker = list(
      color = 'rgba(17, 157, 255,0.5)',
      size = 20,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 2
      )
    ),
    showlegend = F
  ) %>%
  add_trace(
    x = c(2,2),
    y = c(4.25,4.75),
    marker = list(
      color = 'rgba(17, 157, 255,0.5)',
      size = 120,
      line = list(
        color = 'rgb(231, 99, 250)',
        width = 12
      )
    ),
    showlegend = F
  )

# Create a shareable link to your chart
# Set up API credentials: https://plot.ly/r/getting-started
chart_link = api_create(p, filename="style-color-opacity")
chart_link
```

<iframe src="https://plot.ly/~RPlotBot/5290.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>

### Reference

See [https://plot.ly/r/reference/](https://plot.ly/r/reference/) for more information and chart attribute options!
