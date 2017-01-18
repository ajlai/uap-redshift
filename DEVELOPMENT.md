# Development
1. Update the submodule
```
git submodule update
```
2. Rebuild the updated uap-python
```
cd uap-python && python setup.py install && cd ..
```
3. Copy over updated build files into base dir
```
cp uap-python/build/lib/ua_parser/* release/ua_parser
```
4. Create release zip
```
cd release && zip ../uap-redshift.zip * */* && cd ..
```
