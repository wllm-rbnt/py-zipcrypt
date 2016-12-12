# Support for zip files traditional encryption in Python 2.7

- It's just a modified version of /usr/lib64/python2.7/zipfile.py
- Python Software Foundation License applies
- Not tested on Python 3
- Implemented for ZipFile.write(), NOT (yet) for ZipFile.writestr()
- Encryption is active if password is set with ZipFile.setpassword()
- Default password is 'infected'
- This implementation is probably not very good at handling large files

Example usage:
	
	$ python2.7 ./zipfile.py -c test.zip blabla
	$ unzip test.zip
	Archive:  ../test.zip
	[test.zip] blabla password:
  	inflating: blabla
	$
