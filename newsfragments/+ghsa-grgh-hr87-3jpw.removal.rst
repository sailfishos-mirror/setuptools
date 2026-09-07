``setuptools.archive_util`` now raises the new ``UnsafeMember`` exception when
an archive member would be extracted outside of the extraction directory,
where previously such a member was silently skipped. Aborting makes a
malicious or malformed archive visible to the caller instead of yielding a
quietly incomplete extraction, and matches the behavior of the standard
library's ``tarfile`` extraction filters. Note that this also rejects archives
whose members use a backslash as a path separator, as produced by some
non-conforming Windows archivers; such an archive must now be repaired rather
than partially extracted.
