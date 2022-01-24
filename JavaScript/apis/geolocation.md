# [Geolocation API](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)

-   Accessed via _navigator.geolocation_ object and it returns `Geolocation` Object.

-   There are following properties associated with `Gelocation` Obj :-
    1. getCurrentPosition()
    2. clearWatch()
    3. watchPosition()

## getCurrentPosition()

-   The method takes two callbacks, one for `success` & one for `error/failure`and an optional `options` object.

-   `success` returns **GeolocationPosition** object instance which contains `coords` (It contains **GeolocationCoordinates** object instance) & `timestamp`(the time when location data was retrieved - **DOMTimeStamp**) properties.

*   `failure` returns a **GeolocationPositionError** object instance which contains two properties `code` & `message`.

*   `options` object contains properties like `enableHighAccuracy`, `maximumAge` & `timeout`.

## watchPosition()

-   Similar to **getCurrentPosition**, it also takes three arguments `success callback`, `failure callback` & `options` (optional).

*   Used to watch the position of user device and if it changes then call the callback functions.

*   It returns an positionId which can be furthur used to clear the `watchPosition` by `clearWatch`.

## clearWatch()

-   Used to clear the watching of Position by `watchPosition`.
