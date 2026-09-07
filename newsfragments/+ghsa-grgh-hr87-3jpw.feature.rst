``setuptools.archive_util`` now raises the new ``UnsafeMember`` exception when
an archive member would be extracted outside of the extraction directory,
where previously such a member was silently skipped. Aborting makes a
malicious or malformed archive visible to the caller instead of yielding a
quietly incomplete extraction, and matches the behavior of the standard
library's ``tarfile`` extraction filters.
