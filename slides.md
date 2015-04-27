# Saving Data

## Saving Files
- Android uses a file system that's similar to disk-based file systems on other platforms.
- Read and write files using the [File](http://developer.android.com/reference/java/io/File.html) APIs.
	- A `File` object is good for large data that is read *serially*.
		- Image files.
		- Large files exchanged over a network.

### Choose Internal or External Storage
- All Android devices have two file storage areas: "internal" and "external" storage.
- Older devices have two physical mediums, e.g., internal HD and external card.
- Even without removable storage, the APIs are the same (two partitions).

#### Internal storage
- It's always available.
- Files saved here are accessible by only your app by default.
- When the user uninstalls your app, the system removes all your app's files from internal storage.
>**Internal storage is best when you want to be sure that neither the user nor other apps can access your files.**

#### External storage
- It's not always available, because the user can mount the external storage as USB storage and in some cases remove it from the device.
- It's world-readable, so files saved here may be read outside of your control.
- When the user uninstalls your app, the system removes your app's files from here only if you save them in the directory from [`getExternalFilesDir()`](http://developer.android.com/reference/android/content/Context.html#getExternalFilesDir(java.lang.String)).
> **External storage is the best place for files that don't require access restrictions and for files that you want to share with other apps or allow the user to access with a computer.**

### Obtain Permissions for External Storage
To write to the external storage, you must request the [`WRITE_EXTERNAL_STORAGE`](http://developer.android.com/reference/android/Manifest.permission.html#WRITE_EXTERNAL_STORAGE) permission in your manifest file:
```xml
<manifest ...>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    ...
</manifest>
```