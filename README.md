
# SVLM 

Speech Integrated Visual Language Model. Using PG-Video-LLaVA as a start. 




## Installation

After creating a virtual enviroment you can copy this repository with: (make sure you include PYTHONPATH="./:$PYTHONPATH") this will use the modules inside the repository.


```bash
conda create --name=pg_video_llava python=3.10
conda activate pg_video_llava
git clone https://github.com/daniel01mc/SVLM-PG-Video-LLaVA.git
cd Video-LLaVA
PYTHONPATH="./:$PYTHONPATH"
```
or go to the original https://github.com/mbzuai-oryx/Video-LLaVA --> docs 1-CLIP_DEMO.md

Due to dependencies problem 

```bash
  pip install -r requirements.txt (lines 1-18) and (lines 22-23)
```
Download the weights of the model just like in docs --> 1-CLIP_DEMO.md some of the weights are large so make sure you install https://git-lfs.com before downloading the weights.
```bash
  mkdir weights 
  cd weights 
  mkdir llava (download weights)
  mkdir projections (download weights)

  git lfs install or conda-forge::git-lfs


  git clone https://huggingface.co/liuhaotian/llava-v1.5-7b

```
Follow the instructions of Whisper-at: https://github.com/YuanGongND/whisper-at and make sure you run:

```bash
  pip install --no-deps whisper-at
```
That would help with some dependencies conflict.

If you did not copy the whole repository make sure you download: Grounded-Segment-Anything https://github.com/hkchengrex/Grounded-Segment-Anything and follow the instructions.
```bash
export AM_I_DOCKER=False
export BUILD_WITH_CUDA=True
export CUDA_HOME=/path/to/cuda-11.3/

python -m pip install -e segment_anything

python -m pip install -e GroundingDINO

pip install --upgrade diffusers[torch]

git submodule update --init --recursive
cd grounded-sam-osx && bash install.sh

git submodule update --init --recursive
cd Tag2Text && pip install -r requirements.txt
```
If you did not copy the whole repository make sure you download: Tracking-Anything-with-DEVA-- https://github.com/hkchengrex/Tracking-Anything-with-DEVA and follow the instructions.

```bash
git clone https://github.com/hkchengrex/Tracking-Anything-with-DEVA.git

cd Tracking-Anything-with-DEVA
pip install -e .
```


If you did not copy the whole repository make sure you download: recognize-anything-- https://github.com/xinyu1205/recognize-anything and follow the instructions.


```bash
git clone https://github.com/xinyu1205/recognize-anything.git
cd recognize-anything
pip install -e .
```

If you get to this error --> cannot import name 'LLaMAConfig' from 'transformers' run the following line 

```bash
pip install git+https://github.com/zphang/transformers.git@llama_push
```
If you have not donwloaded any transformers yet do:
```bash
transformers@git+https://github.com/huggingface/transformers.git@cae78c46

The version I'm using is tokenizers-0.13.3 transformers-4.27.0.dev0

check with: pip show transformers

or pip install --force-reinstall transformers==x.x.x
```


Run 
```bash
export PYTHONPATH="./:$PYTHONPATH"

python video_chatgpt/chat.py \
    --model-name  <path_to_LLaVA-7B-1.5_weights> \
    --projection_path <path_to_projector_wights_for_LLaVA-7B-1.5> \
    --use_asr \
    --conv_mode pg-video-llava
```


## Appendix

The repository should look like:

- Grounded-Segment-Anything
- Tracking-Anything-with-DEVA
- flash-attention (in case you want train)
- grounding_evaluation
- quantitative_evaluation
- recognize-anything
- scripts
- video_chatgpt
- weights (just like the demo in docs directory)

