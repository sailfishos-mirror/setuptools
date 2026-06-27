``MANIFEST.in`` matching (via ``FileList``) is now insensitive to Unicode
normalization form. A pattern authored in one form (e.g. NFC, as typically
saved by editors) now matches a file whose name is stored on disk in another
(e.g. NFD, as produced by macOS APFS/HFS+). Previously an ``exclude``,
``global-exclude``, ``recursive-exclude``, or ``prune`` rule could silently
fail to drop a non-ASCII-named file from the source distribution, publishing
it despite the exclusion -- see GHSA-h35f-9h28-mq5c.
