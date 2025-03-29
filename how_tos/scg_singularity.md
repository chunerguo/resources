# How to install CellOracle using Singularity on SCG

### Author: Chuner Guo

### Date: 2025-03-28

How to install and run [CellOracle](https://morris-lab.github.io/CellOracle.documentation/installation/index.html) using [Singularity](https://www.sherlock.stanford.edu/docs/software/containers/singularity/) on Stanford's [SCG Cluster](https://login.scg.stanford.edu). This should also apply to any other container-based distributions of python packages that you want to use.

## Step 1: download Docker image

I tried installation using conda and pip but kept running into conflicts. Using Singularity to pull the pre-built docker iamge worked best for me.

Go to a directory where you want to the container to be downloaded, then run:

```bash
singularity pull --tmpdir /tmp ./celloracle.sif docker://kenjikamimoto126/celloracle_ubuntu:0.18.0
```

## Step 2: register a Jupyter kernel

In order to use the container interactively (in Jupyter Notebook), you have to register it as a Jupyter kernel:

```bash
singularity run celloracle.sif
python -m ipykernel install --user --name=celloracle_env
```

## Step 3: modify kernel file

Now navigate to `~/.local/share/jupyter/kernels/celloracle_env/` and open the `kernal.json` file, which should look like:

```js
{
 "argv": [
  "/opt/miniconda/envs/celloracle_env/bin/python",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "celloracle_env",
 "language": "python",
 "metadata": {
  "debugger": true
 }
}
```

In order for Jupyter to construct the kernel from the container when a notebook is started, you have to edit the `argv` key by inserting the first 5 lines:

```js
{
 "argv": [
  "/usr/bin/singularity",    // path to singularity executable
  "exec",                    // singularity command to execute
  "--bind",                  // bind mount to ensure files can be access smoothly
  "/absolute/path/to/data_folder:/root/data_folder", // bind your data directory to the container 
  "/path/to/celloracle.sif", // path to your container image
  "/opt/miniconda/envs/celloracle_env/bin/python",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "celloracle_env",
 "language": "python",
 "metadata": {
  "debugger": true
 }
}
```

The `celloracle_env` kernel should now be available when you start a Jupyter Notebook Server session on [SCG OnDemand](https://ondemand.scg.stanford.edu/).