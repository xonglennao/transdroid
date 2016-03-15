# Introduction #

Transdroid supports a limited amount of intents that perform actions on a torrent server. These intents can be used by other applications to perform server-wide operations such as starting all torrents and changing transfer rates.

# Available intents #

The following intents are available:

  * org.transdroid.control.PAUSE\_ALL
  * org.transdroid.control.RESUME\_ALL
  * org.transdroid.control.START\_ALL
  * org.transdroid.control.STOP\_ALL
  * org.transdroid.control.SET\_TRANSFER\_RATES
    * Needs extras UPLOAD\_RATE and DOWNLOAD\_RATE which are both integers in KB/s
  * org.transdroid.service.FORCE\_CHECK

All org.transdroid.control intents optionally take a DAEMON extra, which is the ID string for the server to execute the action against. To find the ID string for a server: the first server (as listed in the settings) is "" (an empty string) and any subsequent servers have "1", "2", "3", etc. If the DAEMON is omitted, the last-used server is used instead.

The org.transdroid.service.FORCE\_CHECK intent starts the alarm service and does the usual checks. Hence, it only checks new/finished torrents if enabled in the server configuration and only checks RSS feeds if enabled in the alarm settings. On the other hand, it will forcefully run even if the regular alarm service is disabled or background data was disabled on the Android device.

# Examples #

The following code pauses all torrents running on your third server:
```
Intent i = new Intent("org.transdroid.control.PAUSE_ALL");
i.putExtra("DAEMON", "3");
startService(i);
```

To set the transfer rates of the default server:
```
Intent i = new Intent("org.transdroid.control.SET_TRANSFER_RATES");
i.putExtra("UPLOAD_RATE", "250");
i.putExtra("DOWNLOAD_RATE", "500");
startService(i);
```