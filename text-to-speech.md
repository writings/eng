Text To Speech
==============

Notes on TTS technology.

Misc
----

Fast CPU inference:

https://github.com/yoyololicon/wavenet-like-vocoder

http://on-demand.gputechconf.com/gtc/2017/presentation/s7544-andrew-gibiansky-efficient-inference-for-wavenet.pdf


model             training    inference
. . . . . . . . . . . . . . . . . . . . .
WaveNet           faster      slowest
FFTNet            fastest     slower
WaveRNN           slower      faster
Parallel WaveNet  fast        fastest


WaveRNN
-------
Sounds really good. This might be the one to use.

"wavernn" has fast CPU inference time:

https://github.com/keithito/tacotron/issues/152

https://arxiv.org/abs/1802.08435

https://github.com/fatchord/WaveRNN

https://github.com/kdhingra307/wavernn

"I wouldn't recommend this particular model unless you want to achieve real-time inference on a mobile app or something like that."

https://github.com/fatchord/WaveRNN/issues/6

"@hdmjdp I'm still working on the simplified model and the results are pretty good so far (more params than your 0.95M though) ... also experimenting with batched inference on GPU." - Dec 4 2018

Waveglow
--------
"Faster than real time".

Generates from mel-spectrograms.

From Glow and WaveNet, but no need for autoregression. Only a single network.
Single cost function.

Ready to test with pre-trained model on LJS.

### Quotes

"I have 2x1080ti, and the training process takes at least 5 days to get a decent result."

"We have 6 1080ti, the results are still noisy even after a week."

"Faster and higher quality than 'griffinlim(meslpectrogram(audio))'."

- https://github.com/NVIDIA/waveglow/issues/75

"The community has been sharing decent sounding samples at ~160k iterations on a model 
trained with a single GPU. The discussion is here: #12"

"I'm sure you can get away with less than 24 hours. My hunch is 2 hours would be fine."

"I'm at 140k on ljspeech. It doesn't sound great, but it continues to improve. A smaller dataset I'm using at 165k the speech is noisy, but definitely better than the ljspeech. According to the paper https://arxiv.org/pdf/1811.00002.pdf their model was 24 batch size and 580k iterations. So by extremely rough math you are looking at well over 1mil iterations for results equivalent to the paper."

"Wow, the amount of training this thing requires is insane, compared to the wavenet."

"Using a single 1080ti that 9 second clip took about 2 seconds to generate."

"CPU inference is actually pretty slow"

- https://github.com/NVIDIA/waveglow/issues/53

### Links

- [NVIDA impl](https://github.com/NVIDIA/WaveGlow)

Tacotron 2 (Dec 2017)
---------------------
End-to-end.

### Problems:

- Cannot generate audio in realtime
- Difficulty with pronouncing hard words

### Links

- [Original Paper](https://arxiv.org/abs/1712.05884), Natural TTS Synthesis 
  by Conditioning WaveNet on Mel Spectrogram Predictions

- [NVIDIA impl](https://github.com/NVIDIA/tacotron2), without Wavenet.


Tacotron (2017)
---------------
By Google. End-to-end. Generates speech directly from characters (instead of having multiple stages, 
eg. analysis, synthesis).

Trained on (text,audio) pairs.

```
Input: text => Output: raw spectrogram 
                  |
                  +-> Griffin-Lim reconstuction => Speech
```

Griffin-Lim
-----------


nv-wavenet
----------
"Faster than real time".

https://devblogs.nvidia.com/nv-wavenet-gpu-speech-synthesis/

“Medium” is the largest model for which the Deep Voice authors were able to achieve 16 kHz inference on a CPU. It uses 64 residual channels, 128 skip channels, and 20 layers.


Char2Wav (2017)
---------------
Independent. End-to-end.  


WaveNet (2016)
--------------
By Google. Slow. Not end-to-end. Requires linguistic features. Only replaces the vocoder and 
acoustic model.


### Links

- https://google.github.io/tacotron/
