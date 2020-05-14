# Activating the libra-4.4.0 install

This is a cleaner way of activating the environment (than using the python
environment explicitly) since it sets all paths for the user, thanks to the
special Hubzero use script in /apps/share64/debian7/environ.d. It can also
be used inside python itself with the hublib library (see "From Jupyter Tool").

The libra install was performed using anaconda-6 environment. User can activate
the libra-4.4.0 environment, then set the paths manually, if desired.

Substitute 4.8.1 for 4.4.0 to get that version of Libra!

## From Workspace tool

### tl;dr
```
source /etc/environ.sh
use libra-4.4.0
```
Now you should have the libra env's packages in your path.

### The long story
First check which python version you are pointing to:
```
which python
python --version
```

If the path is not to an anaconda-6 directory, specify:
```
source /etc/environ.sh
use anaconda-6
conda info --envs
conda activate base
```

If conda env activation error message displays, then do the following:
`conda init bash`
then log out of Workspace shell, and restart shell. Run 
`conda activate base`. Now the terminal should show the base env. 

Let's verify and activate the desired env:

```
conda info --envs
conda activate libra-4.4.0
```
Now, 
`which python` 
should show the path to the libra-4.4.0 python, since we specify `conflict ANACONDA_CHOICE` in the libra use script.
This procedure should set up the same paths as the `use` script!

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
## Assumptions

Vidia with hubzero; debian7 containers; anaconda-6 install. 
