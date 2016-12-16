# Support for PKWARE traditional encryption for Zip files in Python 2.7 & 3.4

## Description

- Modified versions of /usr/lib64/python2.7/zipfile.py and /usr/lib64/python3.4/zipfile.py
- Python Software Foundation License applies
- Implemented for ZipFile.write() -- file operations
- Implemented for ZipFile.writestr() -- in-memory operations
- Encryption is active if password is set with ZipFile.setpassword()
- Default password is set to 'infected' for cli commands
- This implementation is probably not very good at handling large files

## Example usage:

- Python 2.7 - in-memory operations

	```python
	...
	# Initialize a new password protected zip file from an empty buffer
	zipfile_as_buffer = ''
	zipfile_as_filehandler = io.BytesIO(zipfile_as_buffer)
	zipfile_object = ZipFile(zipfile_as_filehandler, 'w', allowZip64=True)
	zipfile_object.setpassword("infected")

	# Define data to be archived
	data1 = "blabla"
	data1_as_filehandler = io.BytesIO(data1)
	data2 = "blibli"
	data2_as_filehandler = io.BytesIO(data2)

	# Deflate & add two file entries to the encrypted archive
	zipfile_object.writestr('bla', data1, compress_type=ZIP_DEFLATED)
	zipfile_object.writestr('bli', data2, compress_type=ZIP_DEFLATED)
	zipfile_object.close()

	# Do whatever you want with the resulting zip file
	zipfile_as_filehandler.seek(0)
	sys.stdout.write(zipfile_as_filehandler.read())
	...
	```
