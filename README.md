## You will find everything you need in the /Project folder

.

## Use python 3.9 while you have > python 3.9 in the host

To **pip install autogluon** you might need python 3.9 also in the running jupyter notebook.

One way is to have a virtualenv running jupyter notebook with the pythin 3.9 used also in the notebook.

For MacOS, install python 3.9 via the official installer and check the binary path.

Should be `/usr/local/Frameworks/Python.framework/Versions/3.9/bin/python3.9`.

Install virtualenv:

`pip install virtualenv`

Then create a virtualenv project, passing python 3.9:

`python -m virtualenv --python="/usr/local/Frameworks/Python.framework/Versions/3.9/bin/python3.9" project_folder`

Activate the project:

`source project_folder/bin/activate`

Make sure jupyter is installed in the new virtualenv:

`pip install jupyter`

Then clone the project:

`git clone git@github.com:manhluong/cd0385-project-starter.git`

And continue as usual starting the jupyter notebook from the cloned repo:

`jupyter notebook`

In Jupyter check that the python in your path:

`!type python`

Is the same as the one used in the notebook:

```
import sys
sys.executable
```

If not, then check the kernel path with a cell:

`!jupyter kernelspec list`

Edit the kernel in a shell:

`subl /usr/local/share/jupyter/kernels/python3/kernel.json`

Make sure that `argv` has python path the output of `!type python` above. So should be something like: `VIRTUALENV_PROJECT_FOLDER_PATH/bin/python`

Check again that the the python in the path is the same python of the notebook using the cells above.

They should be the same.

Now you should be able to **pip install autogluon** and import it.

## LightGBM might crash in MacOS

Ref.: <https://github.com/microsoft/LightGBM/issues/4229>

As stated at the bottom of the issue, try to downgrade libomp 11:

```
wget https://raw.githubusercontent.com/Homebrew/homebrew-core/fb8323f2b170bd4ae97e1bac9bf3e2983af3fdb0/Formula/libomp.rb
brew unlink libomp
brew install libomp.rb
```
