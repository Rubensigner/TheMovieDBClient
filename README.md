TheMovieDBClient
=======
[![NPM](https://nodei.co/npm/themoviedbclient.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/themoviedbclient/)

A simple node module to make calls to TheMovieDB API, based on [EtienneWan's tmdb-js](https://github.com/EtienneWan/tmdb-js), re-written with promises. 

Usage
-----------

Get your api key by signing up at [www.themoviedb.org](https://www.themoviedb.org/documentation/api)

```javascript
var tmdbclient = require('themoviedbclient');
var tmdb = new tmdbclient(your_api_key);

tmdb.call("/movie/293660", {})
    .then(function (data) {
        console.log(data);
    });
    

tmdb.call("/find/tt1431045", {external_source:"imdb_id"})
    .then(function (data) {
        console.log(data);
    }); 

```

Various Urls defined inside the module are configurable

```javascript
tmdb.configure(
    {
        "host": "api.themoviedb.org",
        "path": "/3",
        "images_url": "http://image.tmdb.org/t/p",
        "timeout": 5000,
        "update_images_url": true
    }
);

```

To get Image Urls of TMDb posters and backdrops, use the following method

```javascript
// poster_path: poster/backdrop filename returned by TMDb api,
// 'W500' : pre-defined size constant. See API documentation for details 
var url = tmdb.getImageUrl(poster_path, 'w500');
```

LICENCE
-----------
The MIT License (MIT)

Copyright (c) 2014 EtienneWan

Copyright (c) 2016 Sarath KCM

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
