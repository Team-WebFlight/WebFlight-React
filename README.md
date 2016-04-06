[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://www.standardjs.com)

# WebFlight for React
WebFlight enables the users visiting a site to serve the content of that site. P2P content sharing technology powered with :heart: by [WebTorrent](https://webtorrent.io)!

### Install
```bash
npm install webflight-react
npm install electron-spawn        // initial peer
```

### Usage

It's easy to incorporate WebFlight into your existing site! Just provide us with a few details on where to find the assets you want to seed, and we'll take care of the rest.

#### Initialize WebFlight

```javascript
const WebFlight = require('webflight-react')

const wf = new WebFlight(options, serverRoot)

wf.init()

app.use(wf.redirect.bind(wf))
```

##### Options

```siteUrl``` - Your website url
<br>```assetsPath``` - The absolute path(s) to the folder(s) containing your assets
<br>`serverRoot` - The root path on your server
<br>```wfPath``` - (optional) The folder WebFlight files will appear in
<br>```wfRoute``` - (optional) The route that retrieves WebFlight files
<br>```seedScript``` - (optional) The script that will initialize seeding your assets so they're ready to be downloaded by users after the **userCount** threshold is passed
<br>`statusBar` - (optional) Dropdown element that will appear on your website that shows users what is being seeded

```
{
  siteURL: String             // Required
  assetsPath: String|Array    // Required
  serverRoot: String          // Required
  wfPath: String              // Optional - defaults to '/wfPath'
  seedScript: String          // Optional - defaults to 'wf-seed.js'
  statusBar: Boolean          // Optional - defaults to true
}
```

## `webflight.redirect(req, res, next)`
Once seeding threshold is met, redirect requests to webflight routes.

## `webflight.start()`
Call starts the seeding process.

## `webflight.watch(req, res, next)`
Watches for http requests to server. Based on a threshold specified in opts, `.watch()` will call `.start()` to begin seeding. When peers are connected, initial seeds are no longer necessary and are killed

---

### License
MIT License (MIT)

Copyright (c) Team WebFlight

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
