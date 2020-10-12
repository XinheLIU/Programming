### Python Interpreters

* Cpython
  * default python intepreter
* Ipython
  * interactive
* Pypy
  * [difference between PyPy and Cpython](https://pypy.readthedocs.io/en/latest/cpython_differences.html)
* JPython
  * on Java platform and translate to java bytecode
* IronPython
  * .Net platform, translate to bytecodes

### IDEs

* VS Code
* PyCharm

### Editors

* [Vim](https://realpython.com/vim-and-python-a-match-made-in-heaven/)
  * [Full stack python with Vim](https://www.fullstackpython.com/vim.html)
* [Emacs](https://realpython.com/emacs-the-best-python-editor/)

### Python Tools

* virtualenv
* pip
  * install [third-party packages](https://pypi.org/)
  * pip3 on Mac and Linux
* conda
* Anaconda
* kernel

python3 -m ipykernel install --user --name=py3

## Virtual Environment

Create independent and clean running environment

```bash
$ pip3 install virtualenv
Mac:~ michael$ mkdir myproject
Mac:~ michael$ cd myproject/
Mac:myproject michael$
Mac:myproject michael$ virtualenv --no-site-packages venv
Using base prefix '/usr/local/.../Python.framework/Versions/3.4'
New python executable in venv/bin/python3.4
Also creating executable in venv/bin/python
Installing setuptools, pip, wheel...done.
Mac:myproject michael$ source venv/bin/activate
(venv)Mac:myproject michael$
(venv)Mac:myproject michael$ pip install jinja2
...
Successfully installed jinja2-2.7.3 markupsafe-0.23
(venv)Mac:myproject michael$ python myapp.py
...
(venv)Mac:myproject michael$ deactivate 
Mac:myproject michael$ 
```



