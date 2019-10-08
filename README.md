# Python version
$ workon pyt3.7


# Python dependencies are covered with: 

$ pip install pillow lxml jupyter matplotlib


# Models-Master Directory(TensorFlow Models)

$ git clone https://github.com/tensorflow/models.git 
OR click the green "clone or download" button on the https://github.com/tensorflow/models page, 
download the .zip, and extract it.


# Protoc Library and Installation

https://github.com/protocolbuffers/protobuf/releases

$ protoc object_detection/protos/*.proto --python_out=.


# Set Env Tensorflow Models Path
$ cd /home/syoo/.virtualenvs/pyt3.7/models/research
$ protoc object_detection/protos/*.proto --python_out=.
$ export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim


# Train Model
$ cd /home/syoo/.virtualenvs/pyt3.7/models/research/object_detection
$ python3.7 train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/ssd_mobilenet_v1_pets.config


# Test Model
$ cd /home/syoo/.virtualenvs/pyt3.7/models/research/object_detection
$ python3.7 export_inference_graph.py \ 
	--input_type image_tensor --pipeline_config_path training/ssd_mobilenet_v1_pets.config \
	--trained_checkpoint_prefix training/model.ckpt-6875 \ 
	--output_directory mac_n_cheese_graph
