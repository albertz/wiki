I followed <http://www.scipy.org/Installing_SciPy/Mac_OS_X> with a few modifications.

First:
* Of course install Apple Dev Tools / Git.
* Get and install GFortran. E.g. from [here](http://r.research.att.com/gfortran-4.2.3.dmg).
* Install umfpack via Homebrew (`brew install umfpack`).

Get the source:

    git clone https://github.com/numpy/numpy.git
    git clone https://github.com/scipy/scipy.git

For both (first numpy, then scipy):

    python setup.py install

If any other numpy installed (via easy_install or so), delete the directory in /Library/Python/2.6/site-packages/.
I got an error about a missing npymath.ini while building scipy. This was because it searched in an old site-packages/numpy.
