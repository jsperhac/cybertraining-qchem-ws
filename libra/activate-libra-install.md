# activating the libra-4.4.0 install

This is a cleaner way of activating the environment (than using the python
environment explicitly) since it sets all paths for the user, thanks to the
special Hubzero use script in /apps/share64/debian7/environ.d. It can also
be used inside python itself with the hublib library (see "From Jupyter Tool").

The libra install was performed using anaconda-6 environment. User can activate
the libra-4.4.0 environment, then set the paths manually, if desired.

## From Workspace tool
```
which python
python --version
```

If no anaconda-6 paths, specify:
```
source /etc/environ.sh
use anaconda-6
conda info --envs
conda activate base
```

If conda env activation error message then do the following:
`conda init bash`
(log out of Workspace shell, then restart shell)
`conda activate base`
(should show base env)

```
conda info --envs
(should show libra-4.4.0)
conda activate libra-4.4.0
```

`which python` 
(should show path to the libra-4.4.0 python since we use conflict ANACONDA_CHOICE set to that installation)

## From Jupyter tool

Inside the Jupyter notebook, running with anaconda-6 (python3), take advantage
of the hublib library. Then call the "use" script with a special ipython
magic command "%" (https://ipython.readthedocs.io/en/stable/interactive/magics.html)
```
import hublib.use
%use libra-4.4.0
```

then, to verify paths (good for single notebook cell only):
```
%%bash
echo $PATH
```
