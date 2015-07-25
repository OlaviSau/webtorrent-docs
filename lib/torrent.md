# Torrent.prototype.deselect()
 Deprioritizes a range of previously selected pieces.

### Syntax
    Torrent.deselect(start,end,priority)
### Parameters
   **start {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to start        selecting from.
   
   
   **end {number}**
   
   
   The index at the storage [pieces](https://github.com/feross/webtorrent/blob/master/lib/storage.js#L36) array to end          selecting from.
   
   
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
 Sets the torrent.metadata 
   *   If the passed metadata is a decoded .torrent file encodes
   *   the passed metadata into a torrent file
   *   otherwise uses the passed metadata
   *    https://github.com/feross/parse-torrent
   *  Torrent.parsedTorrent
*  (note: parsedTorrent is synonym for decoded .torrent file)
*  If the passed metadata is already a decoded .torrent file
*  sets it as the parsedTorrent
*  otherwise attempts to parse it
*   https://en.wikipedia.org/wiki/Torrent_file
 * Torrent.name
 *  Preliminary update to the name
 *  uses the torrent file's name property
 * Torrent.discovery 
 *  calls setTorrent
 *    Updates discovery module with full torrent metadata
 * Torrent.rarityMap
 *  Creates a new RarityMap using the current swarm and parsedTorrent
 * Torrent.storage
 *  If _storageImpl is default
 *  Creates a new Storage using parsedTorrent and self.opts
 *  otherwise
 *  uses the provided _storageImpl
 * Torrent.storage.on
 *  Does setup on storage, setting event handlers for
 *  'piece','file', 'done', 'select', 'deselect', 'critical'
 * Torrent.files
 *  Gets all files from Torrent.storage and pushes them to Torrent.files
 * Torrent.swarm.wires.metadata
 *  If metadata was unavailable at the time ut_metadata was initialized for this
 *  wire, makes it available to the peer in case they request it.
 *
 */

 
