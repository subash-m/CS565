# Key-Value Memory Networks in Facebook bAbI Dataset

This repo contains the implementation of [Key Value Memory Networks for Directly Reading Documents](https://arxiv.org/abs/1606.03126) in Tensorflow. The model is tested on [bAbI](http://arxiv.org/abs/1502.05698).


## Requirements

1. Python 2.7
2. numpy
3. tensorflow==0.12.1
4. pandas
5. Flask


## Dataset

1. Download the dataset from Jason Wetson's(One of the authors for dataset creation) page http://www.thespermwhale.com/jaseweston/babi/tasks_1-20_v1-2.tar.gz
2. Unzip the dataset inside c in a data directory such that all extracted directories(en, en-10k, hn) appear on data/tasks_1-20_v1-2 path.

     (Or)

1. Simply extract the data.rar to the project's home directory.

## Training
Training and testing are done on both en(1k) and en-10k dataset.

To train the model, we have two files one to train individually all task by(single.py) and training all tasks jointly using (joint.py).

### Single training

```
# Train the model on a single task (Default - task 1 with 1k dataset)
python single.py
```
Pass the task_id to train the model on a specific task
```
python single.py --task_id <task_id between 1-20>
```
There are several flags with single.py
```
python single.py --task_id <any task ID between 1-20> --data_dir <data/tasks_1-20_v1-2/en-10k for 10k dataset> --reader <bow, simple_gru>
```
To run all the tasks individually at one go.
```
bash train_allTask_single.sh
```
The models will be generated under 
 - models/models-1k/task-<ID> folder for each task for 1k dataset.
 - models/models-10k/task-<ID> folder for each task for 10k dataset
Model save location can be modified by making change in line 179 of single.py by giving path as ./models/models-10k/task-{}/model.ckpt".format(FLAGS.task_id).


