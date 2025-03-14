# Widgets

_Widgets_ are dashboard elements that display information as a chart or text.

There are three types of widgets available in {{ monitoring-full-name }}:

- [Chart](#chart)
- [Text](#text)
- [Title](#heading)

## Chart {#chart}
The visual representation of one or more metrics over a specific period of time. Each metric has a different color on the chart.

{{ monitoring-full-name }} lets you display {{ yandex-cloud }} service metrics on charts and custom metrics uploaded via the API.

#### Chart types {#chart-types}
The following chart types are available:

- ![image](../../../_assets/monitoring/chart-lines.svg) Line charts.
- ![image](../../../_assets/monitoring/chart-area.svg) Stacked area charts.
- ![image](../../../_assets/monitoring/chart-columns.svg) Bar charts.

You can also normalize data and display it as a stacked bar chart.

#### Time period on charts {#time-period-on-charts}

Metrics on charts are displayed for a specific interval of time, which can be set using preset ranges (`1h 3h 1d 1w 1mo`). You can also set the start and the end of the interval.

To set the interval more precisely, use the timeline located above the chart.

## Text {#text}
Text in [markdown](https://en.wikipedia.org/wiki/Markdown) format, which lets you include additional information in the dashboard. For example, you can post links to other dashboards.

## Title {#heading}
Text that lets you label a dashboard or group of charts.

