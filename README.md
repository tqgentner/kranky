## Kranky

Kranky is a stimulus presentation system rolled in python to control the playback of auditory stimuli in neuroscience experiments. It is easy to control and modify, and integrates with open-ephys.  

kranky is compatible with instructions for krank, a stimulus presenter and data acquisition program developed in the doupe lab. 


## usage: 
(see python kranky -h)

kranky.py [-h] [-n N_TRIALS] 
[-r REQUIRE_DATA] [-d DATA_DIR]
                 [-s STIM_DIR] [-o STIM_ORDER] [--wav WAV]
                 rc_fname



## .rc file
The .rc file describes the stimuli and trial parameteres.  Arguments can also be entered in the call to kranky, which override the .rc file specifications


```
### example rc file
stim add /tazo/jknowles/stimuli/probe_songs2/probe_songs2_song1.raw
stim add /tazo/jknowles/stimuli/probe_songs2/probe_songs2_song2.raw
stim add /tazo/jknowles/stimuli/probe_songs2/probe_songs2_song1flipped.raw

# stim list
set ao_freq 40000
set n_trials 10
set stim_order 2
set ramp_time 0
set attenuation 15
set attenuation2 0

```


## stimulus files
Kranky accepts .wav files and raw binary (.raw) are 16 bit integers. All stimuli in a presentation should have the same sampling rate, but this is enforced for .wav files.  
## .rec files
.rec files save a record of the playback and capture for future analysis. kranky.py saves .pbrec files which contain all the information about the stimulus presentation as it happens. It similtaniously looks at the data coming in to write .rec from the .pbrec files.  .rec is .pbrec plus ai clock samples when the stimuli happened.
## trigger system
## open ephys
kranky is built to run along with a special version of open ephys.  You can download my fork here:
https://github.com/Jeffknowles/GUI
## output to .wav file
Kranky can also write to a wav file:  

	python kranky.py test.rc --wav



Kranky is built to run on alsa (and soon NI) but is constructed in such a way that makes it easy build a ao thread to play out in other systems.


	


positional arguments:
  rc_fname

optional arguments:
  -h, --help            show this help message and exit
  -n N_TRIALS, --n-trials N_TRIALS
                        trials help
  -r REQUIRE_DATA, --require-data REQUIRE_DATA
                        force data help
  -d DATA_DIR, --data-dir DATA_DIR
                        data directory help
  -s STIM_DIR, --stim-dir STIM_DIR
                        stimulus directory help
  -o STIM_ORDER, --stim_order STIM_ORDER
                        stimulus directory help
  --wav WAV             wav help