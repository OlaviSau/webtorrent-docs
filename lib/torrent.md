# Torrent.prototype.destroy()
Destroys and cleans up this torrent.

### Syntax
    Torrent.destroy(cb)
### Parameters
   **cb {Function}**
   
   
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
  **metadata {Object}** is either a parsed(decoded) .torrent file or a unparsed(encoded) .torrent file
  
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

 
