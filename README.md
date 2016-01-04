phonegap-icloudkv-plugin
========================

iOS iCloud KeyValue Store plugin for Cordova

Allows storing small amounts of configuration data in iCloud from Cordova/PhoneGap. Wraps NSUbiquitousKeyValueStore class.

## Compatibility

Cordova/PhoneGap >= 3.0

## Adding the plugin to your project

```
cordova plugin add cordova-plugin-icloudkv
```

## Using the plugin

The plugin becomes available when DeviceReady event is fired, it creates the object `iCloudKV` with the following methods:

    sync(successCallback/*(dictionary_with_all_sync_keys)*/ , failCallback)
       In addition to calling NSUbiquitousKeyValueStore sync method the plugin's sync returns the dictionary holding all iCloud data for the app.
       Normally you only need to call the sync once - on application load.
       Reminder: Calling sync does not guarantee (or matter for) syncrhonization with iCloud but only between the in-memory and the flash storage that will be eventually synced with iCloud by an independent agent.

    save(key, value, successCallback)
       Saves string value for the key.

    load(key, successCallback/*(value)*/, failCallback)
       Loads string value for the key.

    remove(key, successCallback)
        Removes the key.

    monitor(notificationCallback/*(value)*/, successCallback)
        Monitor changes of the app's iCloud.

For the simplest (but probably sufficient for most apps) implementation you will only need two methods: sync (on page load) and save (each time a value is changed).

## Thanks

Special thanks to Pierrick Rouxel and Alexander Portnoy, for upgrading the plugin for Cordova 3.0.

## Bugs and contributions

If you have a patch, fork my repo and send me a pull request. Submit bug reports on GitHub, please.

## Changelog

v0.4.0:
- Fixed monitor API.
- Name changed to match new guidelines.

v0.3.0:
First version of forked plugin:
- Added proper wrapper code for including plugin into application using clobbers
- Added plugin meta-data for cordova registry
