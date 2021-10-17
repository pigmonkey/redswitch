# Redswitch

Redswitch allows the use of [Redshift][1] with automatic position updating, without the complexity of [GeoClue][2].

Redswitch fetches the current location via the [Mozilla Location Service][3] (using GeoClue's API key, which [may go away][4]). The result is stored and compared against the previous location to determine if the device has moved. If a change in location is detected, Redshift is killed and relaunched with the new location (this will result in a noticeable flash, but there seems to be no alternative since [Redshift cannot reload its settings while running][5]). If Redshift is not running, it is launched. If no change in location is detected and Redshift is already running, nothing happens. Because the location information is stored, this can safely be used to launch Redshift when the machine is offline (or when the Mozilla Location Service API is down or rate-limited).

My laptop does not experience frequent, drastic changes in location. I find that having the script automatically execute once upon login is adequate for my needs. If you're jetting around the world, you could periodically execute the script via cron or a systemd timer.

[1]: http://jonls.dk/redshift/
[2]: https://gitlab.freedesktop.org/geoclue/geoclue/-/wikis/home
[3]: https://location.services.mozilla.com/
[4]: https://gitlab.freedesktop.org/geoclue/geoclue/-/issues/136
[5]: https://github.com/jonls/redshift/pull/96
