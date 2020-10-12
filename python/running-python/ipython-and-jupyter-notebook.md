# Ipython

### Features

* Tab completion &lt;Tab&gt;
  * tab after command
  * object.&lt;tab&gt;
* introspection \(?\) operator after a variable \(object\)
  * ?? show more if possible
* Terminal Shortcuts
  * follow **Emacs** keys and Linux shell keys
  * Ctrl + Shift + V paste from clipboard
* Command Line history
  * Ctrl + P \(Up\), Ctrl + N \(Down\) : previous or next history \(by %run\) 
  * \__ \_and \_\_ stored previous two commands,
    * \_&lt;n&gt; stores previous nth output
    * \_i&lt;n&gt; previous nth input
      * eval\(\_i27\)

#### [Magic Commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html)

* %run, %load
  * -d use debugger
    * c\(continue\), s\(step\)
    * !&lt;var&gt; to view variables
    * [debugger commands](https://docs.python.org/2.0/lib/debugger-commands.html)
  * -p 
* %prun - Execute with c profile statement
  * %paste, %cpaste
  * %%prun - profile code block
* %lprun - line profiler
  * uses line\_profiler
  * %lprun -f func1 -f func2 &lt;statement to profile&gt;
* %quickref, %magic - documentation
* %who, who\_ls whos
  * display variable
* %xdel &lt;variable&gt;
  * %reset - delete all variables
* % pdb - use **pdb **to debug
  * %debug : drops you to the stack frame after error is thrown
    * u and d to shift levels
* %page Object
  * pretty print object
* %time, %timeit &lt;statement&gt;
  * time time once, timeit takes multiple runs and average
* command line ones
  * !&lt;cmd&gt;
    * cmd in system shell
    * can combine with current python variables with $
      * ```py
        foo = 'test*' # wildcard
        !ls $foo
        ```
  * %alias &lt;alias\_name&gt; &lt;cmd&gt;
    * give command alias
  * %pwd
  * %bookmark &lt;name&gt; &lt;dir&gt;
    * -b: override and use bookmark location
    * -l: list all bookmarks
  * %cd
    * %pushd, %popd
  * %dirs
  * %ddhist
    * history of visited directories
  * %env
    * environmental variables
* Matplotlib
  * %matplotlib: configure matplotlib options
    * %matplotlib inline

### Advanced Features

* Ipython-Friendly Class
  * \_\__repr\_\_ _methods
* Profiles and [Configuration](https://www.google.com/search?q=create+ipython+config&oq=create+ipython+config&aqs=chrome..69i57j0l2.6031j0j4&sourceid=chrome&ie=UTF-8)
  * _.ipython/profile\_default/ipython\_config.py_
  * .jupyter/
  * ipython --profile=&lt;profile&gt;

# Jupyter Notebook

* Running on cloud now
  * [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb#recent=true)
  * [Binder](https://gke.mybinder.org/)
* Local Run
  * [Install](https://jupyter.org/install.html)
  * [Run](https://jupyter.readthedocs.io/en/latest/running.html#running)
* [Config Jupyter](https://jupyter-notebook.readthedocs.io/en/stable/config_overview.html)
  * jupyter notebook --config=...



