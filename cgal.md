# cgal

### cgal cpp

```
git clone https://github.com/CGAL/cgal.git
sudo apt-get install libgmp3-dev
sudo apt-get install libmpfr-dev
make 
sudo make install
```

### cgal python

```
sudo apt-get install -y swig
```

```
git clone https://github.com/cgal/cgal-swig-bindings
cd cgal-swig-bindings
mkdir build/CGAL-5.0_release -p
cd build/CGAL-5.0_release
cmake -DCGAL_DIR=/usr/lib/CGAL -DBUILD_JAVA=OFF -DPYTHON_OUTDIR_PREFIX=../../examples/python ../..
make -j 4
cd ../../examples/python
python test.py
python setup.py install
```