# Support for zip files traditional encryption in Python 2.7 & 3.4

- Modified versions of /usr/lib64/python2.7/zipfile.py and /usr/lib64/python3.4/zipfile.py
- Python Software Foundation License applies
- Implemented for ZipFile.write(), NOT (yet) for ZipFile.writestr()
- Encryption is active if password is set with ZipFile.setpassword()
- Default password is 'infected'
- This implementation is probably not very good at handling large files

Example usage:
	
	$ python2.7 ./zipfile_python2.7.py -c test.zip blabla
	$ unzip test.zip
	Archive:  ../test.zip
	[test.zip] blabla password:
  	inflating: blabla
	$

	$ python3 ./zipfile_python3.4.py -c test.zip blabla
	$ unzip test.zip
	Archive:  ../test.zip
	[test.zip] blabla password:
  	inflating: blabla
	$
