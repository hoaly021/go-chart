go-chart
========

Package `chart` is a very simple golang native charting library that supports timeseries and continuous
line charts. 

# Installation

To install `chart` run the following:

```bash
> go get -u github.com/wcharczuk/go-chart
```

Most of the components are interchangeable so feel free to crib whatever you want. 

# Usage 

 ![](https://raw.githubusercontent.com/wcharczuk/go-chart/master/images/goog_ltm.png)


The chart code to produce the above is as follows:

```go
// note this assumes that xvalues and yvalues
// have been pulled from a pricing service.
graph := chart.Chart{
    Width:  1024,
    Height: 400,
    Axes: chart.Style{
        Show:        true,
    },
    FinalValueLabel: chart.Style{
        Show: true,
    },
    Series: []chart.Series{
        chart.TimeSeries{
            XValues: xvalues,
            YValues: yvalues,
        },
    },
}
graph.Render(chart.PNG, buffer) //thats it!
```

The Key areas to note are that we have to explicitly turn on two features, the axes and the last value label.

# Design Philosophy

I wanted to make a charting library that used only native golang, that could be stood up on a server (i.e. it had built in fonts).

The goal with the API itself is to have the "zero value be useful", and to require the user to not code more than they absolutely needed.

# Contributions

This library is super early but contributions are welcome.