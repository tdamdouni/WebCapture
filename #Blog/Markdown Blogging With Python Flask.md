# Markdown Blogging With Python Flask

_Captured: 2016-04-10 at 11:10 from [bfeng.github.io](http://bfeng.github.io/blog/2014/11/25/markdown-blogging-with-python-flask/)_

## Introduction

[Flask](http://flask.pocoo.org/) is a popular lightweight Python web MVC framework. Compared to `Django`, Flask based projects are usually simpler to implement and easier to maintain. Flask is BSD licensed and developed by Pocono team.

This tutorial shows how to use Flask and how to integrate a Markdown parser/render into Flask.

## Implementation

Flask based project has no file structure requirements. Python programs, view templates and static files such as javascript files, stylesheets and images can be organized freely. Here are the steps to implement it.

### Create a project folder
    
    
    mkdir pyblog
    

### Install Prerequisites
    
    
    pip install Flask
    pip install Jinja2
    pip install Flask-Misaka
    

### Initiate the blogging program

Create a python file namely `blog.py`. The code below gives an example to use Flask and view templates. `index.html` is a `Jinja2` template. The full code is shown in the appendix.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    
    
    
    from flask import Flask
    from flask import render_template
    app = Flask(__name__, template_folder="views")
    @app.route("/")
    def index():
        return render_template('index.html')
    if __name__ == "__main__":
        app.run(debug=True)
    

### Run this project

Running the project is straightforward like executing a normal python script.
    
    
    python blog.py
    

## Integrate Markdown Renderer with Blogging Platform

[Flask-Misaka](http://pythonhosted.org//Flask-Misaka/) is a project integrate Misaka with Flask. [Misaka](http://misaka.61924.nl/) is a python binding for [Sundown](https://github.com/vmg/sundown), which is a Markdown processing library in C.

The code below shows how Flask-Misaka is integrated into Flask. After `app` is initialized by Flask, wrap `app` by Misaka: `Misaka(app)`.
    
    
    1
    2
    3
    4
    
    
    
    from flask.ext.misaka import Misaka
    app = Flask(__name, template_folder="views")
    Misaka(app)
    

After `app` is initialized, `markdown` can be used in `jinja2` templates. The code below shows `text` is rendered by `markdown`.

The markdown content is written in `readme.md`, which is rendered into a web page. The code below opens the file and stores the text into `content`, which is rendered in the template.
    
    
    1
    2
    3
    4
    5
    6
    
    
    
    content = ""
    with open("readme.md", "r") as f:
      content = f.read()
    def index():
      return render_template("index.html", text = content)
    

## Conclusion

This tutorial introduces Flask and Flask-Misaka, which integrates Markdown into web framework. The code shown in the appendix is not supposed for production use. It focuses on basic examples of Flask and markdown integration.

## Appendix

blog.py
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    
    
    
    from flask import Flask, render_template
    from flask.ext.misaka import Misaka
    app = Flask(__name__, template_folder="views")
    Misaka(app)
    content = ""
    with open('readme.md', 'r') as f:
        content = f.read()
    @app.route("/")
    def index():
        return render_template('index.html', text=content)
    if __name__ == "__main__":
        app.run(debug=True)
    

views/index.html
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    
    
    
    <!doctype html>
    <html>
      <head>
        <title>My Markdown blogging site</title>
      </head>
      <body>
        {{ text|markdown }}
      </body>
    </html>

readme.md
