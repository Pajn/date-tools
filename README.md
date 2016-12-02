# date-tools
[![Build Status](https://travis-ci.org/Pajn/date-tools.svg?branch=master)](https://travis-ci.org/Pajn/date-tools)
[![Coverage Status](https://coveralls.io/repos/github/Pajn/date-tools/badge.svg?branch=master)](https://coveralls.io/github/Pajn/date-tools?branch=master)
[![npm version](https://badge.fury.io/js/date-tools.svg)](https://badge.fury.io/js/date-tools)
[![Dependency Status](https://david-dm.org/Pajn/date-tools.svg)](https://david-dm.org/Pajn/date-tools)
[![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org)

Functions for comparing and counting with dates. Includes Typescript tyipings.


### Install
```
yarn add date-tools
npm install --save date-tools
```

### Usage

#### add/subtract
```javascript
import {Duration, add, subtract} from 'date-tools';

add(Date(2000, 1, 1), Duration.Days(5)) === Date(2000, 1, 6)
subtract(Date(2000, 1, 6), Duration.Days(5)) === Date(2000, 1, 1)

add(Date(2000, 1, 1), Duration.Months(2)) === Date(2000, 3, 1)
subtract(Date(2000, 3, 1), Duration.Months(2)) === Date(2000, 1, 1)

// You can also use them as methods on the date
Date(2000, 1, 1).add(Duration.Days(5)) === Date(2000, 1, 6)
Date(2000, 1, 6).subtract(Duration.Days(5)) === Date(2000, 1, 1)
Date(2000, 1, 1).add(Duration.Months(2)) === Date(2000, 3, 1)
Date(2000, 3, 1).subtract(Duration.Months(2)) === Date(2000, 1, 1)
```

#### isEqual
```javascript
import {Precision, isEqual} from 'date-tools';

isEqual(Date(2000, 1, 1), Date(2000, 1, 2), {precision: Precision.Days}) === false
isEqual(Date(2000, 1, 1), Date(2000, 1, 2), {precision: Precision.Months}) === true
```

#### timeBetween
```javascript

import {Duration, timeBetween} from 'date-tools';
import {match} from 'rusted'

const compare = (start, end) => match(timeBetween(start, end), {
  Days: days => `There are ${days} days between the dates`,
  Months: months => `There are ${months} months between the dates`,
})

compare(Date(2000, 1, 1), Date(2000, 1, 3)) === 'There are 2 days between the dates'
compare(Date(2000, 1, 1), Date(2000, 3, 1)) === 'There are 2 months between the dates'
```

### More Usage
Take a look at the [test file](https://github.com/Pajn/date-tools/blob/master/src/index.test.ts).