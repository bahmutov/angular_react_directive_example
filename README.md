This is just a little sandbox for me to play with React + Angular together.

To run the demo:

```
cd angular_react_directive_example
npm install
npm run dev
Browse to http://localhost:8090
```

## Performance improvement tags

* `step-0` - the original example
* `step-1` - set random timeout to 0 for every cell

Seems like the digest cycle runs many times (after each `$timeout` call). Confirmed using
[ng-monitor-digest-cycle-simple.js](https://github.com/bahmutov/code-snippets/blob/master/ng-count-digest-cycle-simple.js) - while loading the table, the digest runs 1493 times!

* `step-2` - removed full digest run after each `$timeout` in each cell by using

    $timeout(..., ms, false);

This drops the time from 12 seconds to 0.5 seconds.
