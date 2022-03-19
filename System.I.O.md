# System.I.O
---

is a namespace. It will contain standard IO (input/output) types such as classes, structures, enumerations, and delegates to perform read/write operations on different sources like file, memory, network, etc.

---

Here are some commonly used file and directory classes:

File - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

FileInfo - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

Directory - provides static methods for creating, moving, and enumerating through directories and subdirectories.

DirectoryInfo - provides instance methods for creating, moving, and enumerating through directories and subdirectories.

Path - provides methods and properties for processing directory strings in a cross-platform manner.

---

## Readers and writers

BinaryReader and BinaryWriter – for reading and writing primitive data types as binary values.

StreamReader and StreamWriter – for reading and writing characters by using an encoding value to convert the characters to and from bytes.

StringReader and StringWriter – for reading and writing characters to and from strings.

TextReader and TextWriter – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.

---

## Compression

ZipArchive – for creating and retrieving entries in the zip archive.

ZipArchiveEntry – for representing a compressed file.

ZipFile – for creating, extracting, and opening a compressed package.

ZipFileExtensions – for creating and extracting entries in a compressed package.

DeflateStream – for compressing and decompressing streams using the Deflate algorithm.

GZipStream – for compressing and decompressing streams in gzip data format.

---

## Isolated storage


Isolated storage is a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data. The storage provides a virtual file system that is isolated by user, assembly, and (optionally) domain. Isolated storage is particularly useful when your application does not have permission to access user files.

---

The following classes are frequently used when implementing isolated storage:

IsolatedStorage – provides the base class for isolated storage implementations.

IsolatedStorageFile – provides an isolated storage area that contains files and directories.

IsolatedStorageFileStream - exposes a file within isolated storage.

## Write to a file

Some classes and methods are typically used to write text to a file:

StreamWriter contains methods to write to a file synchronously (Write and WriteLine) or asynchronously (WriteAsync and WriteLineAsync).

File provides static methods to write text to a file, such as WriteAllLines and WriteAllText, or to append text to a file, such as AppendAllLines, AppendAllText, and AppendText.

Path is for strings that have file or directory path information. It contains the Combine method and, in .NET Core 2.1 and later, the Join and TryJoin methods, which allow concatenation of strings to build a file or directory path.
