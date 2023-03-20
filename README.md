# Install-stable-diffusion
Repository with instructions to install stable diffusion

## Stable diffusion

#### Create new conda environment
Clone latent diffusion repository and create new conda environmetn by it
```commandline
git clone https://github.com/CompVis/latent-diffusion.git
cd latent-diffusion
conda env create -f environment.yaml
conda activate ldm
cd ..
```

#### Install stable diffusion
Clone stable diffusion repository and install dependencies
```commandline
git clone https://github.com/Stability-AI/stablediffusion.git
cd stablediffusion
conda install -y pytorch==1.12.1 torchvision==0.13.1 cudatoolkit=11.6 -c pytorch -c conda-forge
pip install transformers==4.19.2 diffusers invisible-watermark
pip install -e .
```

#### Install recent version of nvcc and gcc/g++
```commandline
export CUDA_HOME=/usr/local/cuda-X.Y
conda install -y -c "nvidia/label/cuda-X.Y.0" cuda-nvcc
conda install -y -c conda-forge gcc
conda install -y -c conda-forge gxx_linux-64==9.5.0
```

#### Install xformers library
```commandline
cd ..
git clone https://github.com/facebookresearch/xformers.git
cd xformers
git submodule update --init --recursive
pip install -r requirements.txt
pip install -e .
cd ../stablediffusion
```

#### Install open-clip
```
pip install open_clip_torch
```

#### Dependencies
```commandline
pip install chardet
pip uninstall torchmetrics
pip install torchmetrics==0.7.3
```

#### Exports
Before txt2img.py execute
```commandline
<!-- export KMP_DUPLICATE_LIB_OK=TRUE -->
export PYTHONPATH=$PYTHONPATH:<path to latent-diffusion>
```

#### txt2img
Try with
```commandline
python scripts/txt2img.py --prompt "a professional photograph of an astronaut riding a horse" --ckpt models/v2-1_768-ema-pruned.ckpt --config configs/stable-diffusion/v2-inference-v.yaml --H 768 --W 768
```