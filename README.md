ServerModsAPI-Example
=====================

A basic example of how to use the BukkitDev ServerMods API to query &amp; obtain Bukkit plugin updates.

What this code IS
-------
* A barebones system to query the BukkitDev ServerMods API for information about the latest file of any given plugin.

* Specifically unlicensed, and free for anyone to use, modify, or redistribute without attribution.

* Compliant with the [BukkitDev Submission Guidelines concerning Auto-Updaters](http://wiki.bukkit.org/BukkitDev:Project_Submission_Guidelines#Auto-updaters).

What this code is NOT
-------
* A fully-fledged updating class.

* Able to download new files.

* Able to compare the current version with remote versions and determine whether it is up-to-date.

* A realistic implementation of API key usage (API keys should be provided by server admins, per-server, not ever shared or provided by the plugin developer).

* Recommended to be implemented in your plugin without modification.


If you are looking for code that is capable of these things, see [Updater](https://github.com/h31ix/Updater), a drop-in, fully-featured updating class for your plugin that uses the API outlined in this code.

Usage
-------

To use the Update class for testing, you may include it in your code and construct it with one of the following:

* Project ID only

Example:
```Update updateCheck = new Update(38723)```

* Project ID  + API key

Example:
```Update updateCheck = new Update(38723, "1af12d93b7722923d2da7a417f37b190cabdd36d")```

**To obtain your Project's ID:**

1. Point your web browser to the desired project's page on BukkitDev.
2. Locate the "Facts" pane, located on the right side of the page.
3. Copy the Project ID, the first value listed in the pane.

**To obtain your API key:**

1. Point your web browser to [https://dev.bukkit.org/home/servermods-apikey/](https://dev.bukkit.org/home/servermods-apikey/). Note that this page can be accessed from your BukkitDev profile by expanding the "User management" pane and clicking the "Server Mods API Key" link under "Scripting" -- this is NOT your regular API key. You must be logged in to access these pages.
2. If you do not already have a key set, hit "Regenerate" to create one.
3. Copy the API key listed.

**Why use an API key?**

The use of an API key is not required to access the ServerMods API. However, should any anonymous throttling of the API ever be introduced, you may wish to do so in order to identify yourself and remove such restrictions.

In a real implementation, the API key would **NOT** be provided by the developer, it would be provided by the server administrator for their server. You should not share your API key with others.

**Result of use:**

* Provided that the project ID you submit is valid, the program will print out the details of the latest file approved by BukkitDev staff.

Example:

Output of: ```Update updateCheck = new Update(38723)```:

```[INFO] The latest version of AntiCheat.jar is AntiCheat v1.5.9, a RELEASE available at: http://addons.curse.cursecdn.com/files/726/899/AntiCheat.jar```

* If no files have been approved for the project, a message will be printed reflecting this.

* Retaining the initialized Update object, you may call ```object.query()``` at any time to re-query the API for the latest file.

* If the API key submitted is invalid, the query will return a 403 Forbidden response, and an error will result. Note that although API access is available without an API key, submitting one that is invalid is not allowed.