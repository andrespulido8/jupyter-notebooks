# Side-Scan Sonar Data Processing using Jupyter Notebooks and python-sllib

Environment to test, visualize, and process Lowrance plotter/sounder data.
All with the help of https://github.com/opensounder/python-sllib 
for interpreting the actual files.

You will need to have docker installed on your machine to follow the instructions.
Also make sure that you have the sample-data submodule cloned.

```shell
git submodule update --init --recursive
```

# Echogram (sonar image)
Using the read_echogram.ipynb file, one can visualize and process sonar images such as 

![example echogram][output1]

[output1]: images/sss.png "Example from SL2 file"

# Depthmap
Using the depthmap.ipynb file, one can interpolate and plot a bathymetry map such as 

![example echogram][output2]

[output2]: images/depthmap.png "Example from SL2 file"

# GeoJSON
Using the geojson_on_map.ipynb file, one can visualize the trajectory of the sonar in a google maps like map called GeoJSON. 

# Usage with Makefiles
```shell
make build
# now wait while the image is being built

make run
# follow the instructions that and browse to the link provided by 
# jupyter in the end
```


# Usage from PowerShell
Could be from you linux terminal as well but you will have to make some adjustments.
## Build new docker image
```powershell
docker build -t sllib-scipy-notebook -f containers/Dockerfile containers/
```
## Running
```powershell
# this works in powershell on windows, adapt to your environment
docker run --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes `
    -v "${PWD}:/home/jovyan/work" `
    sllib-scipy-notebook
```

## Dependencies
- PyKrige
install: 
```shell
pip install pykrige
```

# Data
The sl2 files and the csv files are stored in the [APRILab Google Drive](https://drive.google.com/drive/folders/1K57onShdPBO5McJBp5whlUoWPsp_cfui)
