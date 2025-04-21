# I/O

## File Handling

`stream` is used for handling `cout` and `cin` functions of `<iostream>` 

Input and output files is `<fstream>`

`in_stream` is the stream name and tell compiler to create a input-file-stream object, `<ifstream>`

`out_stream` is the stream name and tell compiler to create 

## Member Functions and Precision

Member function - a function associated with a certain type of object. 

Fixed point rather than scientific notation

```cpp
cout.setf(ios::fixed);
```

Show the decimal point

```cpp
cout.setf(ios::showpoint);
```

Precision of 2 digits

```cpp
cout.precision(2);
```

## File Operations

to open a file called “myFile.txt”

```cpp
in_stream.open("myFile.txt");
```

Open the output file

```cpp
out_stream.open("anotherFile.txt");
```

so create the file if it does not exist. overwrite of it does.

To disclose the stream

```cpp
in_stream.close(); // for in_stream
out_stream.close(); //for out_stream
```

## Dealing with I/O Failures

```cpp
in_stream.fail();
```

return `true` only if the previous stream operation for `in_stream` was not successful. 

I/O stream work in similar way to `cin` and `cout`

## End-of-File (EOF) for systems that implement `eof()`

you think you know how much data to read from a file…well you usually don’t. 

So the eof flag will be useful to indicate that you have reach the end of the file. 

Two ways to use this function

```cpp
while(!in_stream.eof()){
		// execution commands
}
```

or you can use the `>>` operator

```cpp
while(in_stream >> inputn){
		// execution commands
}
```

What are good use cases for EOFs in C++ programming?

- to keep a program from writing into other files
- to make sure you do not overflow into temporary buffer
- to stop an input files stream.

## Passing streams as parameters

pass by reference
