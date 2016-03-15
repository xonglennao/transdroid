**NOTE: THIS REFERS TO THE OLD (TRANSDROID 1.X) PROJECT ONLY. THE LATEST CODE CAN BE FOUND AT GITHUB**

---

# Introduction #

Transdroid is open-source and of course I greatly welcome any code contributions, small and large. Besides bug fixes and (UI) improvements consider completing or adding support for different torrent clients or enhancing customization.

# Modular setup #

The full project is divided into:
  * **/android** The core (UI) project
  * **/lib** The reuseable daemon connection library, supporting many different torrent clients
  * The search library, [a separate project](http://code.google.com/p/transdroid-search/) sporting a torrent search content provider
  * **/external** Various (parts of) open-source libraries

Note that effectively two Android applications (.apk's) are produced: 1 for the search project and one for the Transdroid app.

# Code project setup #

Easiest is to use Eclipse. Create a directory (I assume ~/transdroid/ here) as root development dir. Transdroid now uses Mercurial (hg), while the search project is still on Subversion (svn). Run:

<pre>
cd ~/transdroid<br>
hg clone https://erickok@code.google.com/p/transdroid/<br>
svn checkout http://transdroid-search.googlecode.com/svn/trunk/ transdroid-search<br>
</pre>

Create a new workspace in Eclipse. Make sure you have the Android SDK tools (currently minimum version is [r14](https://code.google.com/p/transdroid/source/detail?r=14)) set up and pointing to the local Android SDK directory. You should have at least the SDK for API level 13 (Android 3.2) installed, as Transdroid is currently compiled against this (while the minimum supported version is Android 1.6).

Now add the Transdroid projects and ActionBarSherlock by using the import function and pointing to `~/transdroid/transdroid`. The import wizard should show 3 projects. Repeat this import process for `~/transdroid/transdroid-search`. Once these have been added all the projects should compile and you can debug.

If something doesn't compile/work, check:
  * Make sure the `~/transdroid` directory has the 2 directories next to each other, i.e. `transdroid` and `transdroid-search`.
  * The Transdroid project should refer to ActionBarSherlock as library project.
  * The Transdroid project should refer to the Transdroid Torrent Connect project in the build path's Projects tab.
  * The Transdroid Torrent Connect project should refer to the external android.jar file from your local SDK (API level 13) in the buld path's Libraries tab.

For more detailed help, please visit the Transdroid support forum at www.transdroid.org/support/

# Code formatting #

In principle the code is formatted according to the Eclipse IDE defaults. There are some small differences:

  * Line wrapping is set to 120 characters
  * Android XML files are formatted according to Eclipse (so check this in Android -> Editors)
  * Comments are wrapped at 120 characters too and - shortly speaking - don't use unnecessary empty lines.

Commenting is highly encouraged but in a meaningful way of course.


# Contributing code #

If you like to contribute code (or resources) back to the projet, compile a patch (`hg diff > patch.diff`) and send it to transdroid.org@gmail.com. If you plan on more regular contributions I am happy to add you as code committer at this Google Code project site.