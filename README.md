# react-calendar-month-view [![npm version](https://badge.fury.io/js/react-calendar-month-view.svg)](https://badge.fury.io/js/react-calendar-month-view)

A simple and customizable monthly calendar component view.

## Demo & Examples

[Live Demo](https://alwyntan.github.io/react-calendar-month-view/)

To build the examples locally, clone this repo and run:

```js
npm install
npm start
```

or

```js
yarn install
yarn start
```

Then open [`localhost:8080`](http://localhost:8080) in a browser.

## Installation

Install directly from NPM:

```js
npm install react-calendar-month-view --save
```

or

```js
yarn add react-calendar-month-view
```

## Usage

Use this component to display a month view of a calendar with supplied event duration indicators.

```jsx
import CalendarMonthView from 'react-calendar-month-view';

class App extends Component {
  // date is given as an ISO-8601 string
  _renderDay = (date) => {
    // return a component to render for the given date
  };

  render() {
    return <CalendarMonthView renderDay={this._renderDay} />;
  }
}
```

### Functions accessible with a ref

#### isSmallCalendar()

Returns if the calendar is a small calendar.

Example:

```jsx
_renderDay = date => {
  if (this.calendar && this.calendar.isSmallCalendar()) {
    // renderDay for small calendar
  } else {
    // renderDay for normal calendar
  }
};

render() {
  return (
    <CalendarMonthView
      ref={ref => (this.calendar = ref)}
      renderDay={this._renderDay}
    />
  );
}
```

### Props

| prop             | type     | default | description                                                                                                                                                |
| ---------------- | -------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| width            | string   | "90%"   | Specifies the width of the calendar (height is dynamically set and therefore cannot be customized). Examples. "500px", "90vw", "90%"                       |
| renderDay        | function | null    | Callback used to render a given day                                                                                                                        |
| onMonthChange    | function | null    | Callback that is fired when the month is changed (Fires once on component mount)                                                                           |
| titleTextStyle   | object   | null    | Custom styles for the title text                                                                                                                           |
| dayNameTextStyle | object   | null    | Custom styles for the day names (header row of the calendar)                                                                                               |
| dayTextStyle     | object   | null    | Custom styles for the numbers that correspond to the days on the calendar                                                                                  |
| activeDayStyle   | object   | null    | Custom styles for the calendar tile corresponding to the current day                                                                                       |
| inactiveDayStyle | object   | null    | Custom styles for the calendar tile corresponding days that are not the current day                                                                        |
| currentMonth     | number   | null    | Specify the current month to be displayed in the calendar on component mount. Value should be based on moment's set method i.e 0 => Jan, 1 = Feb and so on |
| currentYear      | number   | null    | Specify the current year to be displayed in the calendar on component mount.                                                                               |

### Prop Functions:

#### renderDay(isoDate: string)

**isoDate** is a ISO-8601 string that represents the current day being rendered.

Example:

```jsx
const renderDay = (isoDate) => {
  return <div> ... </div>;
};
```

#### onMonthChange(startDate)

**startDate** is a ISO-8601 string representing the start date of the current month, after the month is changed (Fires once when component is mounted)

Example:

```jsx
const onMonthChange = (startDate) => {
  // eg. retrieve data from gcal
};
```

### Notes

Use the width to control the size of the calendar component.
