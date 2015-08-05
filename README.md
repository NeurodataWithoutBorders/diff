# diff
Python script that compares two HDF5 files. 

Usage:

  python ndiff.py <file-A> <file-B>

or:

  ./ndiff.py <file-A> <file-B>


The script opens two HDF5 files and recursively compares the datasets
and groups in the files. It examines groups, datasets and attributes
and reports if some of these exist in one file and not the other, and
if their names or types differ between the two files. 

NOTE: it does not compare the values stored in datasets or attributes

When a difference is found, it will report one of the following codes:

	DIFF_UNIQUE_A	-- a dataset or group only exists in file A

	DIFF_UNIQUE_B	-- a dataset or group only exists in file B

	DIFF_OBJECTS	-- an object is a dataset in one file and a group in the other

	DIFF_DTYPE		-- the type of an object is different between files

	DIFF_UNIQ_ATTR_A -- an attribute is only present in file A

	DIFF_UNIQ_ATTR_B -- an attribute is only present in file B

	DIFF_ATTR_DTYPE	-- the type of an attribute differs between files


Example:

./ndiff.py foo.h5 bar.h5 

Comparing 'foo.h5' and 'bar.h5'
------------------------------
Examining /
	bar5
	bar3
** Attribute 'a' only in 'bar.h5' (DIFF_UNIQ_ATTR_B)**
	bar2
	bar
	bar4
**  Different element types: 'group' and 'dataset' (DIFF_OBJECTS)
------------------------------
Examining /bar5/
** Element 'bar7' only in 'foo.h5' (DIFF_UNIQUE_A)**
** Element 'bar8' only in 'bar.h5' (DIFF_UNIQUE_B)**
	bar6
** Different dtypes: '<type 'str'>' and '<type 'numpy.ndarray'>' (DIFF_DTYPE)**

