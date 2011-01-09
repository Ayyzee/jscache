JavaScript LRU Cache
====================

Just a simple LRU cache written in javascript. It is loosely based on ASP.NET's Cache, and includes many caching options such as absolute expiration, sliding expiration, cache priority, and a callback function. It can be used to cache data locally in the user's browser, saving a server roundtrip in AJAX heavy applications.

How It Works
------------

		// Create a new cache item
		// The constructor accepts an optional integer 
		// parameter which places a limit on how many 
		// items the cache holds
		var cache = new Cache();
		
		// add an item to the cache
		// parameters: key - the key to refer to the object
		//             value - the object to cache
		//             options - an optional parameter described below
		// the last parameter accepts an object which controls various caching options:
		//      expirationAbsolute: the datetime when the item should expire
		//      expirationSliding: an integer representing the seconds since
		//                         the last cache access after which the item
		//                         should expire
		//      priority: How important it is to leave this item in the cache.
		//                You can use the values CachePriority.Low, .Normal, or 
		//                .High, or you can just use an integer.  Note that 
		//                placing a priority on an item does not guarantee 
		//                it will remain in cache.  It can still be purged if 
		//                an expiration is hit, or if the cache is full.
		//      callback: A function that gets called when the item is purged
		//                from cache.  The key and value of the removed item
		//                are passed as parameters to the callback function.
		cache.setItem("A", "1", {expirationAbsolute: null, 
		                         expirationSliding: 60, 
		                         priority: CachePriority.HIGH,
		                         callback: function(k, v) { alert('removed ' + k); }
		                        });
		                        
		// retrieve an item from the cache
		// takes one parameter, the key to retreive
		// returns the cached item
		cache.getItem("A");
		
		// clears all items from the cache
		cache.clear();

History
-------

1/8/2011: Migrated project to GitHub.
1/20/2010: Thanks to Andrej Arn for some syntax updates.
5/30/2008: First version.
