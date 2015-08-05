# diff
Python script that compares two HDF5 files. 

Usage:

  python ndiff.py <file-A> <file-B>

The script opens two HDF5 files and recursively compares the datasets
and groups in the files. It examines groups, datasets and attributes
and reports if some of these exist in one file and not the other, and
if their names or types differ between the two files. 

NOTE: it does not compare the values stored in datasets or attributes

When a difference is found, it will report one of the following codes:

	DIFF_UNIQUE_A	-- a dataset or group only exists in file A

	DIFF_UNIQUE_B	-- a dataset or group only exists in file B

	DIFF_OBJECTS	-- an object is a dataset in one file and a group in
	the other

	DIFF_DTYPE		-- the type of an object is different between files

	DIFF_UNIQ_ATTR_A -- an attribute is only present in file A

	DIFF_UNIQ_ATTR_B -- an attribute is only present in file B

`	DIFF_ATTR_DTYPE	-- the type of an attribute differs between files

