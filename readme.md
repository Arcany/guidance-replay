# guidance-replay

An event source loop for visual guidance simulator. It turns timestamped GeoJSON into mock location events.


## API

### Emitter

Generate location events for timestamped GeoJSON along a given update interval.

**Parameters**

-   `geojson` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Timestamped geojson of route.
-   `updateInterval` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** Interval (milliseconds) at which to generate location events.

#### Emitter.all

Return all location events for a route. Useful for debugging.

Returns **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)>** Location events with coordinates, bearing, and, if in speedmode, speed and speedchange.

#### Emitter.next

Return the next location event for a route. Useful for long and/or complex routes.

Returns **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Location events with coordinates, bearing, and, if in speedmode, speed and speedchange.


### Route

Turn a Mapbox Directions API response into timestamped GeoJSON in the format of [GeoJSON Coordinate Properties](https://github.com/mapbox/geojson-coordinate-properties).

**Parameters**

-   `directions` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Response from Mapbox Directions API.
-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Optional spacing parameter, which can be `constant` or `acceldecel`. Default is `constant`.

Returns **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** GeoJSON LineString with coordinateProperties.times timestamps in milliseconds for each coordinate in the input geometry, starting at 0 ms.


## Development

### test

```sh
npm test
```

### run simulator

```sh
npm start
# --> http://localhost:9966/
```
