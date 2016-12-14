# Support for Zip files traditional encryption in Python 2.7 & 3.4

- Modified versions of /usr/lib64/python2.7/zipfile.py and /usr/lib64/python3.4/zipfile.py
- Python Software Foundation License applies
- Implemented for ZipFile.write() -- file operations
- Implemented for ZipFile.writestr() -- in-memory operations
- Encryption is active if password is set with ZipFile.setpassword()
- Default password is set to 'infected' for cli commands
- This implementation is probably not very good at handling large files
