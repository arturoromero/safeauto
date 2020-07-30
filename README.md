
Install
-------
```sh
$ yarn # Or alternatively: `npm install`
```


I created the `Driver` and `Trip` classes that parse the input file lines passed into their constructors and assign the
data to the respective instance properties. Factory methods were added to each class to assist in a functional
implementation via `Array.prototype.map` as well as `Trip.prototype.isReported` for usage via chained
`Array.prototype.filter` invocations.

As each `Trip` belongs to a respective `Driver` instance I decided to add a `Driver.prototype.trips` property which is
populated via `Driver.prototype.addTrip` _(or the `Driver.prototype.addTrips` convenience method)_. Adding trips via
this method automatically updates the driver's miles driven and average speed. Lastly I added the
`Driver.prototype.toString` method to convert each driver instance into the textual representation that will be
aggregated into the final report. I felt using the `toString` nomenclature was the most semantic approach being that the
textual report generated is literally the data that the instance contains in the desired human readable format.

The final class implemented was `Report`. It effectively is a container for various `Driver` instances with the
respective `Report.prototype.toString` method to generate the driver report which is the primary objective of this
exercise.

I then added the primary `app` function in `lib/index.js` since it is the main library file. This function takes in
a single string input argument which is then split out into an array of lines which are put through a "functional
pipeline" to aggregate and filter the data into a `Report` instance at which point the value of
`Report.prototype.toString` is returned.
