# How to prepare data
## Generate mixed speech and coresponding targets speech file.

If you have WSJ0 data, you can use this code http://www.merl.com/demos/deep-clustering/create-speaker-mixtures.zip to create the mixed speech. 

Or you can also use you own data.

## Extract FFT spectrum feats for every utterance. 

For every utterance, you need to extract the mixed speech, speak1 and speaker2 feature matrix and use the function in 'io_funcs/tfrecords_io.py'  make_sequence_example_two_labels(inputs,inputs_cmvn, labels1, labels2)  to generate tensorflow examples. 
     inputs: the mixed speech feats matrix with shape (num_frames, dim)
     inputs_cmvn: the mixed speech feats matrix after mean and variance normalization. I don't think this is necessary. You can 
                  use the same data with inputs.
     labels, labels2: spker1 and spker2's feats as targets.
     
     
## Generate tfrecord files list for training, cv and test sets.

make a dir, named lists. Put all the training tfrecord files' path to 'lists/tr.lst' and the same for the 'lists/cv.lst', 'lists/tt.lst'

## Run run.sh

Once you prapared all  data list files for tr, cv and tt (test), you can run 'run.sh' from the step3--train RNN. Make sure you give the right list dir. 

