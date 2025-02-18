# accelerator2025

Misc things for eScience accelerator 2025 

https://escience.washington.edu/global-high-resolution-modeling-a-new-lens-on-the-southern-ocean/

## Custom Python environment on NCAR JupyterHub

Default 'NPL' Conda environments have a ton of great packages and are updated twice a year. Currently, `NPL2025a` is the latest environment and has very recent packages (e.g. `xarray=2025.1.1`). *But you can't update existing packages or add new ones to this environment*. 

For a shared custom Python environment on the NCAR JupyterHub we can use `pixi` (https://pixi.sh/). It creates "lock" files to guarantee two collaborators use the same packages and versions. 

### Install pixi
```
curl -fsSL https://pixi.sh/install.sh | bash
```

### Install a pixi environment 

Environments are defined by `pixi.toml` and `pixi.lock` files which live in a "project" folder/repository. The actual packages are downloaded and installed in a hiddent `.pixi` subfolder.
```
git clone https://github.com/scottyhq/accelerator2025.git
cd accelerator2025
pixi shell # when done type "exit" instead of "conda deactivate"
```

### Use in ipython notebook 

You might have to logout of the JupyterHub before using the new kernel:
```
pixi shell
python -m ipykernel install --user --name=accelerator2025
```