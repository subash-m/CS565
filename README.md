# Key-Value Memory Networks in Facebook bAbI Dataset

This repo contains the implementation of [Key Value Memory Networks for Directly Reading Documents](https://arxiv.org/abs/1606.03126) in Tensorflow. The model is tested on [bAbI](http://arxiv.org/abs/1502.05698).


## Requirements

1. Python 2.7
2. numpy
3. tensorflow==0.12.1
4. pandas
5. Flask


## Dataset

1. Download the dataset from Jason Wetson's(One of the author for dataset creation) page http://www.thespermwhale.com/jaseweston/babi/tasks_1-20_v1-2.tar.gz
2. Unzip the dataset inside c in a data directory such that all extracted directories(en, en-10k, hn) appears on data/tasks_1-20_v1-2 path.

     (Or)

1. Simply extract the data.rar to the project's home directory.

## Training
Taining and testing is done on both en and en-10k dataset.

To train the model, we have two files one to train individually all task by(single.py) and training all tasks jointly using (joint.py).

# Single training
1. Use $python single.py  (It will by default train for task 1 with 1k dataset), we can pass different arguments to work on different task and dataset.
2. $python single.py --task_id <any task ID between 1-20> --data_dir <data/tasks_1-20_v1-2/en-10k for 10k dataset> --reader <bow, simple_gru> to run on different tasks.
3. train_allTask_single.sh can be used to run all task individually at one go.
The models will be generated under models/models-1k/task-<ID> folder for each task for 1k dataset and for 10k dataset it will get stored in models/models-10k/task-<ID> by
making change in line 179 of single.py by giving path as ./models/models-10k/task-{}/model.ckpt".format(FLAGS.task_id).
