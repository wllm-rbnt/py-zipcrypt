# Support for zip files traditional encryption

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
