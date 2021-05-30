To run this application, clone the repo:

```bash
 git clone https://github.com/mlops-task/tf-serv.git
 cd tf-serv
 pip install -r requirements.txt
```

Install Tensorflow Serving
- [Link](https://www.tensorflow.org/tfx/serving/setup)


Start TF serving server
```
 docker run -p 8501:8501 --name tfserving_classifier \
 --mount type=bind,source=tf-server/img_classifier/,target=/models/img_classifier \
 -e MODEL_NAME=img_classifier -t tensorflow/serving
```

To make predictions, send HTTP request to server from another terminal.

```
  python predict.py
```

To retrain the model:
```
  python model.py
```
The proposed architecture draft can be found in file **possible_architecture.png**
