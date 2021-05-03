The main parts of this code were reproduced from "Exploiting temporal information for 3D human pose estimation - ECCV2018". 

### Training from the scratch


`python temporal_3d.py --use_sh --camera_frame --dropout 0.5`

Use the flag `--use_sh` if you want to use the stacked_hourglass detections. Otherwise omit the flag (for ground truth 2D). 


### Pre-trained model

You can download a pre-trained model for testing, visualization and fine-tuning from: 
https://drive.google.com/file/d/1j2jpwDpfj5NNx8n1DVqCIAESNTDZ2BDf/view?usp=sharing

Download and untar the file. Copy the contents in `Pose_3D/temporal_3d_release/trained_model/All/dropout_0.5/epochs_100/adam/lr_1e-05/linear_size1024/batch_size_32/use_stacked_hourglass/seqlen_5/`

### Evaluate the model

To evaluate the pre-trained model call: 

`python temporal_3d.py --use_sh --camera_frame --dropout 0.5 --load 1798202 --evaluate`

In this case, 1798202 passed to the load flag is the global iteration number. Change it if you want to test any of your own trained models. 

### Fine-tune an existing model

Do not use the evaluate flag if you want to fine-tune an existing model. 

`python temporal_3d.py --use_sh --camera_frame --dropout 0.5 --load 1798202`


### Create a movie from a set of images and 2D predictions

We provided a sample set of frames and 2D detections (from stacked-hourglass detector) in the directory `Pose_3D/temporal_3d_release/fed/`. 

If you want to use other detection and images, set the flags --data_2d_path abd --imag_dir appropriately

To create a movie run the command: 

`python create_movie.py --use_sh --camera_frame` 





