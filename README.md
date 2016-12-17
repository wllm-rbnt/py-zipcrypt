# Support for traditional PKWARE encryption for Zip files in Python 2.7 & 3.4

## Description

- Modified versions of /usr/lib64/python2.7/zipfile.py and /usr/lib64/python3.4/zipfile.py
- Python Software Foundation License applies
- Implemented for ZipFile.write() -- file operations
- Implemented for ZipFile.writestr() -- in-memory operations
- Encryption is active if password is set with ZipFile.setpassword()
- Default password is set to 'infected' for cli commands
- This implementation is probably not very good at handling large files
- *WARNING* (you already know this) This encryption scheme should not be
	used to protect sensitive information, it is known to be broken (see [this paper][1]).

## Example usage

- Python 2.7 - in-memory operations

	```python
	...
	# Initialize a new password protected zip file from an empty buffer
	zipfile_as_buffer = ''
	zipfile_as_stream = io.BytesIO(zipfile_as_buffer)
	zipfile_object = ZipFile(zipfile_as_stream, 'w', allowZip64=True)
	zipfile_object.setpassword("infected")

	# Define data to be archived
	data1 = "blabla"
	data1_as_stream = io.BytesIO(data1)
	data2 = "blibli"
	data2_as_stream = io.BytesIO(data2)

	# Deflate & add two file entries to the encrypted archive
	zipfile_object.writestr('bla', data1, compress_type=ZIP_DEFLATED)
	zipfile_object.writestr('bli', data2, compress_type=ZIP_DEFLATED)
	zipfile_object.close()

	# Do whatever you want with the resulting zip file
	zipfile_as_stream.seek(0)
	sys.stdout.write(zipfile_as_stream.read())
	...
	```

- Python 3.4 - in-memory operations

	```python
	...
	# Initialize a new password protected zip file from an empty buffer
	zipfile_as_buffer = ''
	zipfile_as_stream = io.BytesIO(bytes(zipfile_as_buffer, "utf-8"))
	zipfile_object = ZipFile(zipfile_as_stream, 'w', allowZip64=True)
	zipfile_object.setpassword(bytes("infected", "utf-8"))

	# Define data to be archived
	data1 = "blabla"
	data1_as_stream = io.BytesIO(bytes(data1, "utf-8"))
	data2 = "blibli"
	data2_as_stream = io.BytesIO(bytes(data2, "utf-8"))

	# Deflate & add two file entries to the encrypted archive
	zipfile_object.writestr('bla', data1, compress_type=ZIP_DEFLATED)
	zipfile_object.writestr('bli', data2, compress_type=ZIP_DEFLATED)
	zipfile_object.close()

	# Do whatever you want with the resulting zip file
	zipfile_as_stream.seek(0)
	sys.stdout.buffer.write(zipfile_as_stream.read())
	...
	```

[1]: http://math.ucr.edu/~mike/zipattacks.pdf
