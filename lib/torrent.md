# Torrent.prototype.createServer()
 Creates a server for the torrent.

### Syntax
    Torrent.createServer(opts)
### Parameters
   **opts {object}**
   
   
   The opts to create the server with.
   
### Description
Creates a server with the options and pushes it to the _servers array.
### Examples
# Torrent.prototype.critical()
 Marks a range of pieces as critical priority to be downloaded ASAP.

### Syntax
    Torrent.critical(start,end)
### Parameters
   **start {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to start        selecting from.
   
   
   **end {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to end          selecting from.
   
   
### Description
Adds the range on pieces to the array which hold pieces to be downloaded first.
### Examples
# Torrent.prototype.deselect()
 Deprioritizes a range of previously selected pieces.

### Syntax
    Torrent.deselect(start,end,priority)
### Parameters
   **start {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to match the 
   selection object start.
   
   
   **end {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) to match the 
   selection object end.
   
   
   **priority {number}**
   
   The priority associated with the selection.
   
### Description
Makes sure the parameters are valid, then searches the _selections array for the matching selection object, and removes it if it finds it.
### Examples
# Torrent.prototype.select()
 Select a range of pieces to prioritize.

### Syntax
    Torrent.select(start,end,priority,notify)
### Parameters
   **start {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to start        selecting from.
   
   
   **end {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to end          selecting from.
   
   
   **priority {number}**
   
   The priority that selected pieces will be given.
   **notify {function}**
   
   The callback when the selection is updated with new data.
   
### Description
Makes sure the parameters are valid, then updates selections.
### Examples
# Torrent.prototype.addWebSeed()
 Add a web seed to the swarm

### Syntax
    Torrent.addWebSeed(url)
### Parameters
   **url {string}**
   
   
   The url for the webseed. Example Soon™
### Description
Calls the [bittorrent-swarm's addWeebSeed()](https://github.com/feross/bittorrent-swarm/blob/master/index.js#L163) method with the passed url and [torrent.parsedTorrent](https://github.com/feross/parse-torrent/blob/master/index.js).
### Examples
# Torrent.prototype.addPeer()
Add a peer to the swarm

### Syntax
    Torrent.addPeer(peer)
### Parameters
   **peer {String|[simplePeer](https://github.com/feross/simple-peer/blob/master/index.js)}**
   
   
   The peer will be added to the swarm.
### Description
Returns true if the peer was added false if it was not. Checks if the peer is blocked, if it's not blocked, adds it to the swarm.
### Examples

# Torrent.prototype.destroy()
Destroys and cleans up this torrent.

### Syntax
    Torrent.destroy(cb)
### Parameters
   **cb {function}**
   
   
   The passed cb will be called with node-parallel after the torrent has finished destroying.
### Description
Sets the destroyed flag to true, removes it from client, clears reChokeInterval, cleans up blobURL's, closes the servers,
destroys the swarms,stops the discovery and closes the storage for this torrent, **this does not clean up the storage**. Then calls the callback.

### Examples


# Torrent._onMetadata()
_onMetadata is called when the metadata is received.
It does setup on Torrent, if metadata is not already set.

### Syntax
    _onMetadata(metadata)

### Parameters
  **metadata {object}** is either a parsed(decoded) .torrent file or a unparsed(encoded) .torrent file
  
   [parse-torrent module](https://github.com/feross/parse-torrent)|[torrent-file](https://en.wikipedia.org/wiki/Torrent_file)  
   
### Description
 Sets the torrent.metadata, adds the event listeneners and attempts to verify if the verify opts is set to true on torrent.
 

 
