# FUEL MIX ERCOT GRAPH

## Application Overview

The fuel mix ERCOT graph provides a visual representation of various sources of electricity generation broken down by fuel source based on data from ERCOT. The app renders a stacked area graph to show the data of various fuel sources for a particular date and time. The app allows the user to:

- View the ERCOT fuel mix graph.
- Use crosshairs to point out the exact location on the graph.
- View information for that date and time as a tooltip.
- Dynamically sort itself in descending order of the value of fuel sources.
- Calculate the percentages for each source.
- Adjust for maximum viewability.
- Show a legend that defines the color scheme of the graph.
- Act as a toggle to show or hide a particular fuel source (graph and tooltip update accordingly).
- Use a calendar to select a range of dates to view the data for the specified period.
- Use arrow buttons to move the graph one day forward or backward.

## Tech Stack Used

- HTML, CSS, and Javascript for rendering the frontend.
- Bootstrap for additional CSS.
- Icons for the legend and tooltip.
- D3.js library and its Plot framework to render the graph.
- Flatpickr to render the calendar.

## Functional Overview

The functions used in the application are as follows:

### `Processdata()`
Processes CSV data and transforms it. Takes 2 parameters, `startDate` and `endDate` to filter the data. If the date range is out of scope, it renders the whole graph as default.

### `Createlegend()`
Creates a legend for the energy sources. Takes 2 parameters: `sources` (list of unique energy sources) and `customcolors` (dictionary of each source and its color hexcode for custom color scheme).

### `Plotvisualise()`
Renders the main graph using the D3.js library's Plot framework. Takes 3 parameters: `raw data` (untransformed data from the CSV file), `transformed data` (data after transformations), and `visible sources list` (sources that are not hidden).

### `Showtooltip()`
Renders the dynamic tooltip and handles positioning for viewability. Takes 5 parameters: `event` (to get mouse position), `data` (information for the tooltip), `tooltip element`, `custom colors dictionary` (to render icons), and `visible sources list` (to block hidden sources).

### `Sortsources()`
Utility function used to sort sources in the tooltip. Takes 1 parameter: `values` (data for the specific date and time for all sources).

### `Hidetooltip()`
Hides the tooltip when out of bounds of the graph. Takes no parameters.

### `UpdateCrosshairs()`
Updates the crosshair’s position. Takes 3 parameters: `mouse pointer` (current location), `horizontal line` (line object for horizontal crosshair), and `vertical line` (line object for vertical crosshair).

### `HideCrosshairs()`
Hides the crosshair lines when out of bounds of the graph. Takes 2 parameters: `horizontal line object` and `vertical line object`.

### `UpdateGraph()`
Re-renders the graph when any source is hidden or shown, and deletes the previous graph. Takes no parameters.
