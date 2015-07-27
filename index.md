# WebTorrent.prototype.add()

 Start downloading a new torrent. Aliased as `WebTorrent.download`.

### Syntax
    WebTorrent.add(torrentId,opts,onTorrent) WebTorrent.download(torrentId,opts,onTorrent)
### Parameters
 **torrentId  {string|[buffer](https://github.com/feross/buffer/blob/master/index.js)|[torrent](https://github.com/OlaviSau/webtorrent-docs/edit/master/lib/torrent.md)}**
 
 The torrent to add.
 
 
 **opts {object}**
 
 The options to create the torrent with.
 
 
  <b>onTorrent {function }</b>
   
   
   The cb to be called after the function finishes.
   
### Description
Adds a new torrent to the client.
### Examples
# WebTorrent.prototype.get()

 Returns the torrent with the given `torrentId`.Convenience method.

### Syntax
    WebTorrent.get(torrentId)
### Parameters
 **torrentId  {string|[buffer](https://github.com/feross/buffer/blob/master/index.js)|[torrent](https://github.com/OlaviSau/webtorrent-docs/edit/master/lib/torrent.md)}**
 
 The torrent to get.
 

### Description
Returns the torrent with the given `torrentId`.Convenience method. Easier than
 searching through the `client.torrents` array. Returns `null` if no matching torrent
 found.
### Examples
# WebTorrent.prototype.seed()

 Start seeding a new file/folder.

### Syntax
    WebTorrent.seed(input, opts, onseed)
### Parameters
 **input  {string|[file](https://developer.mozilla.org/en/docs/Web/API/File)|[fileList](https://developer.mozilla.org/en-US/docs/Web/API/FileList)|[buffer](https://github.com/feross/buffer/blob/master/index.js)|Array.&#60;string|[file](https://developer.mozilla.org/en/docs/Web/API/File)|[buffer](https://github.com/feross/buffer/blob/master/index.js)&#62;}**
 
 The file is used to create a Torrent.
 
 
 **opts {object}**
 
 The options to create the torrent with.String takes the file from filesystem
 
 
   <b>onTorrent {function }</b>
   
   
   The cb to be called after the method.
   
### Description
Adds a new Torrent to the client(WebTorrent). Pushes it to the DHT. Emits 'seed'. TODO:Write better docs ^^
### Examples
 Soon.
