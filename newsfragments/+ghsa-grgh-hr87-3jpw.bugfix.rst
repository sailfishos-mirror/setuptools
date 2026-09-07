``setuptools.archive_util`` no longer extracts archive members outside of the
requested extraction directory. Both the tar and zip formats specify ``/`` as
the only path separator, but the guard against ``..`` components split member
names on ``/`` alone, so a name such as ``..\escaped.txt`` was treated as a
single component and then resolved as a traversal by the filesystem on
Windows. Member names containing a backslash, a drive letter, or a UNC prefix
are now rejected, as are members whose resolved destination falls outside the
extraction directory -- see GHSA-grgh-hr87-3jpw.
