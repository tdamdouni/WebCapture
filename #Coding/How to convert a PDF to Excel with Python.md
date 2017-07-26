# How to convert a PDF to Excel with Python Sep 16, 2016 • Tristan Bacon

_Captured: 2016-11-07 at 09:54 from [pdftables.com](https://pdftables.com/blog/pdf-to-excel-with-python)_

![PDF to Excel with Python header](https://pdftables.com/images/blog/pdf-to-excel-with-python-head.png)

If you're a Python user, and want to be able to convert PDFs without uploading it manually to [PDFTables.com](https://pdftables.com), you can make use of our brand-new Python PDFTables API.

In this tutorial, I'll be showing you how to get the library set up on your local machine, and how to use it to convert a PDF in a folder to Excel.

![An example of a PDF conversion with Python](https://pdftables.com/images/blog/pdf-excel-python-preview.png)

> _Here's an example of a PDF that I've converted with the library. In order to properly test the library, make sure you have a PDF handy!_

### Before we start

If you haven't already, install Python on your machine from the [Python website](https://www.python.org/downloads/). You can use either Python 3.5.x or 2.7.x, as the PDFTables API works with both.

For this tutorial, I'll be using the Windows Python IDLE Shell, but the instructions are almost identical for Linux and Mac. Depending on the version of Python you have, you will also need to install the **[pip** package management system](https://pip.pypa.io/en/stable/installing/) for Python.

You'll also need to [create an account on PDFTables.com](https://pdftables.com/join) in order to get your free PDFTables API key.

### Step 1

In your terminal/command line, install the PDFTables Python library with:
    
    
    pip install git+https://github.com/pdftables/python-pdftables-api.git

Or if you'd prefer to install it manually, you can download it from [python-pdftables-api](https://github.com/pdftables/python-pdftables-api), and install it with:
    
    
    python setup.py install

### Step 2

Create a new Python script, and add the following code:
    
    
    import pdftables_api
    
    c = pdftables_api.Client('my-api-key')
    c.xlsx('input.pdf', 'output.xlsx')

Now, you'll need to make the following changes to the script:

  * Replace `my-api-key` with your PDFTables API key, which you can get [here](https://pdftables.com/pdf-to-excel-api).
  * Replace `input.pdf` with the PDF you want to convert.
  * Replace `output.xlsx` with the name of the converted spreadsheet.

Now, save your finished script as `convert-pdf.py` in the same directory as the PDF document you want to convert.

![PDF and Python script in the conversion directory](https://pdftables.com/images/blog/pdf-excel-python-directory.png)

### Step 4

Open your command line/terminal, and change your directory (e.g. `cd C:/Users/Bob`) to the folder you saved your `convert-pdf.py` script and PDF in, then run the following command:
    
    
    python convert-pdf.py

To find your converted spreadsheet, navigate to the folder in your file explorer and hey presto, you've converted a PDF to Excel with Python!

![Converted Excel spreadsheet in its directory](https://pdftables.com/images/blog/pdf-excel-python-result.png)
