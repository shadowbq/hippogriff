# Hippogriff

Fly across time and space to find the rightful owners.

![About](http://upload.wikimedia.org/wikipedia/commons/d/da/Hippogriff2.jpg) [1]

## GeoIP Server Revisted

[Erik Michaels-Ober]

This simple Rack server is useful as a self-hosted service for making lookups to the GeoIP database from [MaxMind][].

[maxmind]: http://www.maxmind.com/app/geolite


## Instant installation and deploy

* Clone this: `git clone git://github.com/shadowbq/hippogriff.git`
* Update the free GeoIP data files: `rake geoip:update_city_lite`
* Commit that data file to your clone: `git add vendor && git commit -m "adding data file"`

## How To

Once the server is running you can make a GET request to the server and receive lookup results in JSON format.

```ruby
require 'json'
require 'open-uri'
ip = "207.97.227.239"
data = JSON.load(open("http://localhost/#{ip}").read)
"You're in: #{data['city']}"
```

Or, straight from a terminal:

    curl http://localhost/207.97.227.239

## License & Copyrights

MIT - See [LICENSE](./LICENSE)

Contributing authors: [Shadowbq, Erik Michaels-Ober]

Copyright (c) 2010-2014, 

Maxmind - [Data LICENSE](./LICENSE.maxmind)

GeoLite Databases (c) 2005 - 2014 MaxMind.

This product includes GeoLite data created by MaxMind, available from
http://maxmind.com/ 
