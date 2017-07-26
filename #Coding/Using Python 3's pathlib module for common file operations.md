# Using Python 3's pathlib module for common file operations

_Captured: 2016-11-13 at 22:01 from [blog.danwin.com](http://blog.danwin.com/using-python-3-pathlib-for-managing-filenames-and-directories/)_

## tl;dr

Check out the [pathlib](https://docs.python.org/3/library/pathlib.html) module - [made standard in Python 3.4](https://www.python.org/dev/peps/pep-0428/) - for an object-oriented approach to common file tasks:

Traditional way of downloading (well, with [Requests](http://docs.python-requests.org/en/master/)), unzipping, and globbing through a file folder:
    
    
    from glob import glob
    from os import makedirs
    from os.path import basename, join
    from shutil import unpack_archive
    import requests
    # pretend DATA_URL could point to an archive file URL only known at runtime
    # i.e. we don't know if it's a zip, gz, etc., which is why we use 
    # unpack_archive instead of ZipFile
    DATA_URL = 'http://stash.compciv.org/ssa_baby_names/names.zip' 
    DATA_DIR = join('/', 'tmp', 'pathto', 'stuff')
    ZIP_FNAME = join(DATA_DIR, basename(DATA_URL))
    makedirs(DATA_DIR, exist_ok=True)
    print('Downloading', DATA_URL)
    resp = requests.get(DATA_URL)
    with open(ZIP_FNAME, 'wb') as wf:
        print("Saving to", ZIP_FNAME)
        wf.write(resp.content)
    
    unpack_archive(ZIP_FNAME, extract_dir=DATA_DIR)
    for fname in glob(join(DATA_DIR,  '*.txt')):
        with open(fname, 'r') as rf:
            print(fname, rf.read())
    

Using [pathlib](https://docs.python.org/3/library/pathlib.html), which provides a `Path` object that has `basename`, `joinpath`, `glob`, and `read_text`, and `write_bytes` methods.
    
    
    from pathlib import Path
    from shutil import unpack_archive
    import requests
    
    DATA_URL = 'http://stash.compciv.org/ssa_baby_names/names.zip' 
    DATA_DIR = Path('/', 'tmp', 'pathto', 'stuff')
    DATA_DIR.mkdir(exist_ok=True, parents=True)
    ZIP_FNAME = DATA_DIR.joinpath(Path(DATA_URL).name)
    
    print('Downloading', DATA_URL)
    resp = requests.get(DATA_URL)
    print("Saving to", ZIP_FNAME)
    ZIP_FNAME.write_bytes(resp.content)
    
    unpack_archive(str(ZIP_FNAME), extract_dir=str(DATA_DIR))
    for fpath in DATA_DIR.glob('*.txt'):
        print(fpath, fpath.read_text())
    

## The importance of learning file operations

For my [computational journalism courses at Stanford](http://www.compciv.org/), I've made students work through the code needed to handle not just analyzing data files, but downloading and organizing them. This is based on my own experience of how widescale data collection can quickly go to shit if you can't jigger together an automated, reproducible way of fetching and saving files. But I'm also motivated to show students that nothing magical happens when we enter Programming-Land: the file you download goes exactly where you tell your program to download it, whether your program is a web browser or a Python script you've written yourself.

(From my anecdotal observation, students seem to be increasingly ignorant of how file downloads in the browser even work - and who can blame them, with the way iOS has made the file system a magic black box? But that's a whole other topic…)

Regardless of the value of being able to programmatically manage files, knowing how to do it is still good general practice for programming, as it involves all the fundamentals, including conditionals and control flow, as well as importing libraries.

I even wrote an 8-part lesson just on how to download, unzip, and read through a nested file list: [Extracting and Reading Shakespeare](http://2016.compciv.org/practicum/shakefiles/shakefiles-landing-page/) \- Practicing the ins-and-outs of managing files and reading through them, featuring the works of Shakespeare.

The first lesson is: [How to create a directory idempotently with makedirs()](http://2016.compciv.org/practicum/shakefiles/a-creating-a-directory-idempotently/) - which simply asks the student to write a program that creates a directory.

In Python 3's os module, there's the [makedirs method](https://docs.python.org/3/library/os.html#os.makedirs):
    
    
    import os
    os.makedirs("mynewdirectory")
    

To make this call not throw an error if the directory already exists, we specify `True` for the optional `exists_ok` argument:
    
    
    import os
    os.makedirs("mynewdirectory", exists_ok=True)
    

By the final lesson, [Counting the non-blank-lines in Shakespeare's tragedies](http://2016.compciv.org/practicum/shakefiles/h-count-non-blank-lines-in-shakespeare-tragedies/), the student is expected to glob a list of filenames and iterate through them to open each file (as well as use [PEP8-approved import syntax)](https://www.python.org/dev/peps/pep-0008/#imports):

(…though at this early stage in the curriculum, I've avoided the introduction of [file handling via context managers and its extra `with` syntax](https://www.python.org/dev/peps/pep-0343/))
    
    
    from os.path import join
    from glob import glob
    filepattern = join('tempdata', '**', '*')
    filenames = glob(filepattern)
    
    for fname in filenames:
        txtfile = open(fname, 'r')
        for line in txtfile:
            # ...etc
        txtfile.close()
    

Later on in the curriculum, this file management code can become quite verbose. The following code comes from an exercise titled, [Download all of the baby names data from the Social Security Administration](http://2016.compciv.org/assignments/exercise-sets/0020-gender-detector-set/#exercise-a):
    
    
    import requests
    from os import makedirs
    from os.path import join
    from shutil import unpack_archive
    from glob import glob
    SOURCE_URL = 'https://www.ssa.gov/oact/babynames/names.zip'
    DATA_DIR = 'tempdata'
    DATA_ZIP_PATH = join(DATA_DIR, 'names.zip')
    # make the directory
    makedirs(DATA_DIR, exist_ok=True)
    
    print("Downloading", SOURCE_URL)
    resp = requests.get(SOURCE_URL)
    
    with open(DATA_ZIP_PATH, 'wb') as f:
        f.write(resp.content)
    
    unpack_archive(DATA_ZIP_PATH, extract_dir=DATA_DIR)
    babynamefilenames = glob(join(DATA_DIR, '*.txt'))
    print("There are", len(babyfilenames), 'txt files')
    

I don't mind making students write lots of code, because that's what they need the most practice with early on. But there's a case to be made that that such code is so lengthy that it hinders cognitive understanding. Coming from Ruby-land, I have always longed for the elegance of its [Pathname module](http://ruby-doc.org/stdlib-2.1.0/libdoc/pathname/rdoc/Pathname.html).

But just recently, I discovered [PEP 428: The pathlib module - object-oriented filesystem paths](https://www.python.org/dev/peps/pep-0428/), which reduces the number of modules (particularly `os` and `os.path`) needed to do OS-agnostic file handling.

Here's the traditional way of creating a new file (including its parent directory):
    
    
    from os import makedirs
    from os.path import join
    mydir = join('myfiles', 'docs')
    myfname = join(mydir, 'readme.txt')
    makedirs(mydir, exist_ok=True)
    with open(myfname, 'w') as wf:
        wf.write("Hello world")
    

Here's the same process using the `pathlib.Path` type:
    
    
    from pathlib import Path
    mydir = Path('myfiles', 'docs')
    mydir.mkdir(exist_ok=True, parents=True)
    myfname = mydir.joinpath('readme.txt')
    with myfname.open('w') as wf:
        wf.write("Hello world")
    

The Path type also has [convenience methods for reading and writing](https://docs.python.org/3/library/pathlib.html#pathlib.Path.read_text) for those _many_ situations in which you don't need to handle files via streaming I/O:
    
    
    from pathlib import Path
    myfname = Path('myfile.txt')
    myfname.write_text("Hi there")
    print(myfname.read_text())
    

And there are additional conveniences for path segment handling:
    
    
    from pathlib import Path
    URL = 'http://www.example.com/hello/world/stuff.html'
    # save to /tmp/stuff.bak
    fname = Path("/tmp").joinpath(Path(URL).stem + '.bak')
    

Compared to:
    
    
    from os.path import basename, join, splitext
    URL = 'http://www.example.com/hello/world/stuff.html'
    fname =  join("/tmp", splitext(basename(URL))[0] + '.bak')
    

It's not a huge change in number of lines of code, but you only have to look in the [pathlib documentation](https://docs.python.org/3/library/pathlib.html) to figure out what you need, rather than both [os](https://docs.python.org/3/library/os.html) and [os.path](https://docs.python.org/3/library/os.path.html).

I'll be using pathlib for all of my personal Python programming. That said, I'm not sure if I'll use pathlib for teaching beginners. For example, what I like about `os.path.join` is that its arguments are strings and its return value is a string. Novice programmers struggle with realizing how straightforward a file path is - it's just a string, and if you pass in a typo, your program isn't going to magically know where you intended a file to be.

The `Path` type is a thin layer over filepath strings…but until you actually understand what object-oriented programming is, `Path('hey', 'there').write_text('yo')` is going to feel very magical. Having to define filenames as strings, then _open_ them, and then _read_ them - all as discrete operations - is perhaps verbose in comparison, but it helps to connect beginners to the realities of computing, i.e. a file isn't just magically read into memory, instantaneously.

And there's also the issue that high-level methods that expect a file path to be a string won't know how to deal with `Path`-type objects - while delivering a cryptic error message to boot:
    
    
    from shutil import unpack_archive
    unpack_archive(Path('example.zip'))
    
    
    
        930     for name, info in _UNPACK_FORMATS.items():
        931         for extension in info[0]:
    --> 932             if filename.endswith(extension):
        933                 return name
        934     return None
    
    AttributeError: 'PosixPath' object has no attribute 'endswith'
    

**Teaching tip:** My use of `os.path.join` might seem like unnecessary overhead, as in, why write all of this:
    
    
    from os.path import join
    from glob import glob
    my_datadir = join('mydata', 'cleaned')
    my_filenames = glob(join('mydata', 'cleaned', '*.csv'))
    

- when we can write this:
    
    
    from glob import glob
    my_datadir = 'mydata/cleaned/'
    my_filenames = glob(my_datadir + '*.csv'))
    

Well, the main reason is that being a OS X person, I'm not sure how those examples behave on Windows's file system - and even if they do work, it's still incredibly confusing to beginners who don't understand the basics of OS filesystems (not everyone knows what a "directory " is) and are wondering why my examples have `'my/path/to/file'` when their OS has paths that look like `'my\\\path\\\to\\\file'`.

Also, creating paths via string concatenation is somewhat restricting when you're dynamically generating paths in an automated loop.

And of course, when manually typing out paths, there's the huge risk of human error. Spot the typo below:
    
    
    from glob import glob
    my_datadir = 'mydata/cleaned'
    my_filenames = glob(my_datadir + '*.csv'))
    
