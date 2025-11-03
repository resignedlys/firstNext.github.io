ComfyUI
The most powerful and modular visual AI engine and application.

Website Dynamic JSON Badge Twitter Matrix
   

ComfyUI Screenshot

ComfyUI lets you design and execute advanced stable diffusion pipelines using a graph/nodes/flowchart based interface. Available on Windows, Linux, and macOS.

Get Started
Desktop Application
The easiest way to get started.
Available on Windows & macOS.
Windows Portable Package
Get the latest commits and completely portable.
Available on Windows.
Manual Install
Supports all operating systems and GPU types (NVIDIA, AMD, Intel, Apple Silicon, Ascend).

Examples
See what ComfyUI can do with the example workflows.

Features
Nodes/graph/flowchart interface to experiment and create complex Stable Diffusion workflows without needing to code anything.
Image Models
SD1.x, SD2.x (unCLIP)
SDXL, SDXL Turbo
Stable Cascade
SD3 and SD3.5
Pixart Alpha and Sigma
AuraFlow
HunyuanDiT
Flux
Lumina Image 2.0
HiDream
Qwen Image
Hunyuan Image 2.1
Image Editing Models
Omnigen 2
Flux Kontext
HiDream E1.1
Qwen Image Edit
Video Models
Stable Video Diffusion
Mochi
LTX-Video
Hunyuan Video
Wan 2.1
Wan 2.2
Audio Models
Stable Audio
ACE Step
3D Models
Hunyuan3D 2.0
Asynchronous Queue system
Many optimizations: Only re-executes the parts of the workflow that changes between executions.
Smart memory management: can automatically run large models on GPUs with as low as 1GB vram with smart offloading.
Works even if you don't have a GPU with: --cpu (slow)
Can load ckpt and safetensors: All in one checkpoints or standalone diffusion models, VAEs and CLIP models.
Safe loading of ckpt, pt, pth, etc.. files.
Embeddings/Textual inversion
Loras (regular, locon and loha)
Hypernetworks
Loading full workflows (with seeds) from generated PNG, WebP and FLAC files.
Saving/Loading workflows as Json files.
Nodes interface can be used to create complex workflows like one for Hires fix or much more advanced ones.
Area Composition
Inpainting with both regular and inpainting models.
ControlNet and T2I-Adapter
Upscale Models (ESRGAN, ESRGAN variants, SwinIR, Swin2SR, etc...)
GLIGEN
Model Merging
LCM models and Loras
Latent previews with TAESD
Works fully offline: core will never download anything unless you want to.
Optional API nodes to use paid models from external providers through the online Comfy API.
Config file to set the search paths for models.
Workflow examples can be found on the Examples page

Release Process
ComfyUI follows a weekly release cycle targeting Friday but this regularly changes because of model releases or large changes to the codebase. There are three interconnected repositories:

ComfyUI Core

Releases a new stable version (e.g., v0.7.0)
Serves as the foundation for the desktop release
ComfyUI Desktop

Builds a new release using the latest stable core version
ComfyUI Frontend

Weekly frontend updates are merged into the core repository
Features are frozen for the upcoming core release
Development continues for the next release cycle
Shortcuts
Keybind	Explanation
Ctrl + Enter	Queue up current graph for generation
Ctrl + Shift + Enter	Queue up current graph as first for generation
Ctrl + Alt + Enter	Cancel current generation
Ctrl + Z/Ctrl + Y	Undo/Redo
Ctrl + S	Save workflow
Ctrl + O	Load workflow
Ctrl + A	Select all nodes
Alt + C	Collapse/uncollapse selected nodes
Ctrl + M	Mute/unmute selected nodes
Ctrl + B	Bypass selected nodes (acts like the node was removed from the graph and the wires reconnected through)
Delete/Backspace	Delete selected nodes
Ctrl + Backspace	Delete the current graph
Space	Move the canvas around when held and moving the cursor
Ctrl/Shift + Click	Add clicked node to selection
Ctrl + C/Ctrl + V	Copy and paste selected nodes (without maintaining connections to outputs of unselected nodes)
Ctrl + C/Ctrl + Shift + V	Copy and paste selected nodes (maintaining connections from outputs of unselected nodes to inputs of pasted nodes)
Shift + Drag	Move multiple selected nodes at the same time
Ctrl + D	Load default graph
Alt + +	Canvas Zoom in
Alt + -	Canvas Zoom out
Ctrl + Shift + LMB + Vertical drag	Canvas Zoom in/out
P	Pin/Unpin selected nodes
Ctrl + G	Group selected nodes
Q	Toggle visibility of the queue
H	Toggle visibility of history
R	Refresh graph
F	Show/Hide menu
.	Fit view to selection (Whole graph when nothing is selected)
Double-Click LMB	Open node quick search palette
Shift + Drag	Move multiple wires at once
Ctrl + Alt + LMB	Disconnect all wires from clicked slot
Ctrl can also be replaced with Cmd instead for macOS users

Installing
Windows Portable
There is a portable standalone build for Windows that should work for running on Nvidia GPUs or for running on your CPU only on the releases page.

Direct link to download
Simply download, extract with 7-Zip and run. Make sure you put your Stable Diffusion checkpoints/models (the huge ckpt/safetensors files) in: ComfyUI\models\checkpoints

If you have trouble extracting it, right click the file -> properties -> unblock

Update your Nvidia drivers if it doesn't start.

Alternative Downloads:
Experimental portable for AMD GPUs

Portable with pytorch cuda 12.8 and python 3.12 (Supports Nvidia 10 series and older GPUs).

How do I share models between another UI and ComfyUI?
See the Config file to set the search paths for models. In the standalone windows build you can find this file in the ComfyUI directory. Rename this file to extra_model_paths.yaml and edit it with your favorite text editor.

comfy-cli
You can install and start ComfyUI using comfy-cli:

pip install comfy-cli
comfy install
Manual Install (Windows, Linux)
Python 3.14 will work if you comment out the kornia dependency in the requirements.txt file (breaks the canny node) but it is not recommended.

Python 3.13 is very well supported. If you have trouble with some custom node dependencies on 3.13 you can try 3.12

Instructions:
Git clone this repo.

Put your SD checkpoints (the huge ckpt/safetensors files) in: models/checkpoints

Put your VAE in: models/vae

AMD GPUs (Linux)
AMD users can install rocm and pytorch with pip if you don't have it already installed, this is the command to install the stable version:

pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm6.4

This is the command to install the nightly with ROCm 7.0 which might have some performance improvements:

pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/rocm7.0

AMD GPUs (Experimental: Windows and Linux), RDNA 3, 3.5 and 4 only.
These have less hardware support than the builds above but they work on windows. You also need to install the pytorch version specific to your hardware.

RDNA 3 (RX 7000 series):

pip install --pre torch torchvision torchaudio --index-url https://rocm.nightlies.amd.com/v2/gfx110X-dgpu/

RDNA 3.5 (Strix halo/Ryzen AI Max+ 365):

pip install --pre torch torchvision torchaudio --index-url https://rocm.nightlies.amd.com/v2/gfx1151/

RDNA 4 (RX 9000 series):

pip install --pre torch torchvision torchaudio --index-url https://rocm.nightlies.amd.com/v2/gfx120X-all/

Intel GPUs (Windows and Linux)
(Option 1) Intel Arc GPU users can install native PyTorch with torch.xpu support using pip. More information can be found here

To install PyTorch xpu, use the following command:
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/xpu

This is the command to install the Pytorch xpu nightly which might have some performance improvements:

pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/xpu

(Option 2) Alternatively, Intel GPUs supported by Intel Extension for PyTorch (IPEX) can leverage IPEX for improved performance.

visit Installation for more information.
NVIDIA
Nvidia users should install stable pytorch using this command:

pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu130

This is the command to install pytorch nightly instead which might have performance improvements.

pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu130

Troubleshooting
If you get the "Torch not compiled with CUDA enabled" error, uninstall torch with:

pip uninstall torch

And install it again with the command above.

Dependencies
Install the dependencies by opening your terminal inside the ComfyUI folder and:

pip install -r requirements.txt

After this you should have everything installed and can proceed to running ComfyUI.

Others:
Apple Mac silicon
You can install ComfyUI in Apple Mac silicon (M1 or M2) with any recent macOS version.

Install pytorch nightly. For instructions, read the Accelerated PyTorch training on Mac Apple Developer guide (make sure to install the latest pytorch nightly).
Follow the ComfyUI manual installation instructions for Windows and Linux.
Install the ComfyUI dependencies. If you have another Stable Diffusion UI you might be able to reuse the dependencies.
Launch ComfyUI by running python main.py
Note: Remember to add your models, VAE, LoRAs etc. to the corresponding Comfy folders, as discussed in ComfyUI manual installation.

Ascend NPUs
For models compatible with Ascend Extension for PyTorch (torch_npu). To get started, ensure your environment meets the prerequisites outlined on the installation page. Here's a step-by-step guide tailored to your platform and installation method:

Begin by installing the recommended or newer kernel version for Linux as specified in the Installation page of torch-npu, if necessary.
Proceed with the installation of Ascend Basekit, which includes the driver, firmware, and CANN, following the instructions provided for your specific platform.
Next, install the necessary packages for torch-npu by adhering to the platform-specific instructions on the Installation page.
Finally, adhere to the ComfyUI manual installation guide for Linux. Once all components are installed, you can run ComfyUI as described earlier.
Cambricon MLUs
For models compatible with Cambricon Extension for PyTorch (torch_mlu). Here's a step-by-step guide tailored to your platform and installation method:

Install the Cambricon CNToolkit by adhering to the platform-specific instructions on the Installation
Next, install the PyTorch(torch_mlu) following the instructions on the Installation
Launch ComfyUI by running python main.py
Iluvatar Corex
For models compatible with Iluvatar Extension for PyTorch. Here's a step-by-step guide tailored to your platform and installation method:

Install the Iluvatar Corex Toolkit by adhering to the platform-specific instructions on the Installation
Launch ComfyUI by running python main.py
Running
python main.py

For AMD cards not officially supported by ROCm
Try running it with this command if you have issues:

For 6700, 6600 and maybe other RDNA2 or older: HSA_OVERRIDE_GFX_VERSION=10.3.0 python main.py

For AMD 7600 and maybe other RDNA3 cards: HSA_OVERRIDE_GFX_VERSION=11.0.0 python main.py

AMD ROCm Tips
You can enable experimental memory efficient attention on recent pytorch in ComfyUI on some AMD GPUs using this command, it should already be enabled by default on RDNA3. If this improves speed for you on latest pytorch on your GPU please report it so that I can enable it by default.

TORCH_ROCM_AOTRITON_ENABLE_EXPERIMENTAL=1 python main.py --use-pytorch-cross-attention

You can also try setting this env variable PYTORCH_TUNABLEOP_ENABLED=1 which might speed things up at the cost of a very slow initial run.

Notes
Only parts of the graph that have an output with all the correct inputs will be executed.

Only parts of the graph that change from each execution to the next will be executed, if you submit the same graph twice only the first will be executed. If you change the last part of the graph only the part you changed and the part that depends on it will be executed.

Dragging a generated png on the webpage or loading one will give you the full workflow including seeds that were used to create it.

You can use () to change emphasis of a word or phrase like: (good code:1.2) or (bad code:0.8). The default emphasis for () is 1.1. To use () characters in your actual prompt escape them like \( or \).

You can use {day|night}, for wildcard/dynamic prompts. With this syntax "{wild|card|test}" will be randomly replaced by either "wild", "card" or "test" by the frontend every time you queue the prompt. To use {} characters in your actual prompt escape them like: \{ or \}.

Dynamic prompts also support C-style comments, like // comment or /* comment */.

To use a textual inversion concepts/embeddings in a text prompt put them in the models/embeddings directory and use them in the CLIPTextEncode node like this (you can omit the .pt extension):

embedding:embedding_filename.pt

How to show high-quality previews?
Use --preview-method auto to enable previews.

The default installation includes a fast latent preview method that's low-resolution. To enable higher-quality previews with TAESD, download the taesd_decoder.pth, taesdxl_decoder.pth, taesd3_decoder.pth and taef1_decoder.pth and place them in the models/vae_approx folder. Once they're installed, restart ComfyUI and launch it with --preview-method taesd to enable high-quality previews.

How to use TLS/SSL?
Generate a self-signed certificate (not appropriate for shared/production use) and key by running the command: openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 3650 -nodes -subj "/C=XX/ST=StateName/L=CityName/O=CompanyName/OU=CompanySectionName/CN=CommonNameOrHostname"

Use --tls-keyfile key.pem --tls-certfile cert.pem to enable TLS/SSL, the app will now be accessible with https://... instead of http://....

Note: Windows users can use alexisrolland/docker-openssl or one of the 3rd party binary distributions to run the command example above.

If you use a container, note that the volume mount -v can be a relative path so ... -v ".\:/openssl-certs" ... would create the key & cert files in the current directory of your command prompt or powershell terminal.

Support and dev channel
Discord: Try the #help or #feedback channels.

Matrix space: #comfyui_space:matrix.org (it's like discord but open source).

See also: https://www.comfy.org/

Frontend Development
As of August 15, 2024, we have transitioned to a new frontend, which is now hosted in a separate repository: ComfyUI Frontend. This repository now hosts the compiled JS (from TS/Vue) under the web/ directory.

Reporting Issues and Requesting Features
For any bugs, issues, or feature requests related to the frontend, please use the ComfyUI Frontend repository. This will help us manage and address frontend-specific concerns more efficiently.

Using the Latest Frontend
The new frontend is now the default for ComfyUI. However, please note:

The frontend in the main ComfyUI repository is updated fortnightly.
Daily releases are available in the separate frontend repository.
To use the most up-to-date frontend version:

For the latest daily release, launch ComfyUI with this command line argument:

--front-end-version Comfy-Org/ComfyUI_frontend@latest
For a specific version, replace latest with the desired version number:

--front-end-version Comfy-Org/ComfyUI_frontend@1.2.2
This approach allows you to easily switch between the stable fortnightly release and the cutting-edge daily updates, or even specific versions for testing purposes.

Accessing the Legacy Frontend
If you need to use the legacy frontend for any reason, you can access it using the following command line argument:

--front-end-version Comfy-Org/ComfyUI_legacy_frontend@latest
This will use a snapshot of the legacy frontend preserved in the ComfyUI Legacy Frontend repository.
