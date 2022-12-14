<div align="center">
    <img src="https://raw.githubusercontent.com/yijensun/vid2aud/master/doc/image/logo.png" alt="logo" width="600"/>
</div>

## Installation
Before Installation, **vid2aud** require [**soundscape_IR**](https://github.com/meil-brcas-org/soundscape_IR) as dependency. Thus, install **soundscape_IR** first in a Python>=3.7.0 environment.
```bash
git clone https://github.com/meil-brcas-org/soundscape_IR.git
cd soundscape_IR
pip install -r requirements.txt
```

Run the following command to install **vid2aud** from PyPI.
```bash
pip install vid2aud
```

To install the latest version, clone the repository and install the module with dependencies from the top-level folder.
```bash
git clone https://github.com/yijensun/vid2aud.git 
cd vid2aud
pip install . --use-feature=in-tree-build
```

## Quick start

**vid2aud** allows importing video from both Google drive and local directory. 
In this guide, we import video from Google drive. Assign the folder ID of the Google drive folder that contains video in `folder_id` and the video format in `file_format` (The folder ID is a string of text after the last / in your folder's url). 

To import the video from local directory, use `path` to assign the directory instead.

```python
from vid2aud import vid2aud

# loading video from Gdrive
test = vid2aud(folder_id='1r8OF_5Vu7p8tjdZwsf1maOcKHdmZWpuo', file_format='.mp4')

# loading video from local directory
#test = vid2aud(path='data/video/', file_format='.mp4')
```
Choose the video file desired to convert by `file_no` and assign file name and file format of the converted audio in `audio_name` and `audio_format` respectively.

```python
#converting...
test.convert(file_no = 2, audio_name = 'GH020063', audio_format = '.wav')
```

By the function `audio_visualization` in **soundscape_IR**, we can plot the spectrogram of the converted audio.

```python
from soundscape_IR.soundscape_viewer import audio_visualization

#Spectrogram of part of the converted audio
camera = audio_visualization('GH020063.wav', offset_read = 74, duration_read=15, FFT_size=2048, window_overlap=0, plot_type='Spectrogram', f_range=[50,4000], prewhiten_percent=0)
```
<div align="center">
    <img src="https://raw.githubusercontent.com/yijensun/vid2aud/master/doc/image/result_1.png" alt="result_1" width="600"/>
</div>
<div>
   <a href="https://colab.research.google.com/drive/1tqT6ydi8QIs1Fd8eCGrdlNgmFexv-bca?usp=sharing"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</div>

## Currently ongoing developments
- Batch process videos

## Bugs report and suggestions 
If you encounter any bug or issue, please contact Yi-Jen Sun via elainesun442@gmail.com. Suggestions are also appreciated!
